---
title: "IvorySquare: peer-reviewed methodology as a tool surface for LLM agents"
date: 2026-04-19
permalink: /posts/2026/04/ivorysquare-architecture/
tags:
  - llm-agents
  - architecture
  - mcp
  - tool-use
---

*IvorySquare — an open Ivory Tower for everyone.*

## The premise

Most "AI for finance" tools are wrappers around chat, with a human as the user of the language model. IvorySquare inverts that premise: the language model is the user, and the system exposes verifiable, citation-grounded methodology as the tool surface it consumes. Finance, accounting, economics, and operations research have produced decades of peer-reviewed methods — each with a formula, a data requirement, an empirical validation, and a citation. IvorySquare turns that body of work into typed, test-backed, provenance-tracked skills the agent calls against.

The architecture is a stack of layers, each with its own contract: a layered data and standardization stack, a foundational curriculum layer at textbook-subsection granularity, a paper-derived skill layer, four LLM persona configurations that gate every artifact, and an evaluation harness that decides what ships.

## Layered data stack (L0 – L5)

Ingestion of corporate disclosures (SEC filings, XBRL / iXBRL), market data, and related sources flows through APIs and MCP connectors into a typed store with deterministic replay and content-hash versioning at every layer:

- **L0 raw** — original payloads, captured byte-for-byte with their fetch URL, retrieval timestamp, and content hash.
- **L1 parsed** — structured representations (XBRL facts, parsed PDF text, normalized JSON) with original-source line-item provenance preserved.
- **L2 standardized** — canonical accounting concepts and market-data fields under the standardization layer's vocabulary, with unit and period normalization.
- **L3 derived** — fundamental-extraction and ratio computations performed via the foundational skill layer.
- **L4 modeled** — paper-derived methodology applied (Beneish M-Score, Altman Z-Score, readability/complexity factors, and so on).
- **L5 delivery** — composed reports, agent-callable JSON, and downstream-consumer surfaces.

Every consumer of an L_n artifact carries a citation chain back to the L0 source, so a numeric output in an L5 deliverable is traceable to a specific filing line item with hash, retrieval timestamp, and source URL.

## Standardization layer

Between L1 and L2 sits the standardization layer: a typed mapping from filer-specific tags (XBRL element names, vendor-specific market-data fields, paper-specific worked-example labels) to IvorySquare's canonical vocabulary. Standardization is reversible — every canonical fact records the source tag, the mapping rule, and the rule's version, so a later schema change replays cleanly without losing the prior ground truth. Mappings are reviewed by the `accounting_expert` persona before promotion.

## Foundational curriculum layer

The skill graph is anchored at the bottom by a foundational layer of textbook-subsection-granular concept skills. Two branches populate the layer:

- **Finance/accounting:** CFA Level 1 — FSA, Equity, Corporate Issuers — and a CPA FAR review outline.
- **Operations research:** Bertsimas-Tsitsiklis *Introduction to Linear Optimization*, Boyd-Vandenberghe *Convex Optimization*, Ross *Stochastic Processes*, Ross *A First Course in Probability*.

Eight textbook TOCs ingest into a YAML-backed prerequisite DAG with ninety-five candidate subsection nodes; node identifiers preserve `<branch>/<book_id>/chXX__YY__sub` shape so prerequisite chains remain readable in both the curriculum audit log and the materialized skill tree. The graph is queryable through the `mvp curriculum` CLI surface (`ingest`, `filter`, `materialize`, `graph`) and renders to Graphviz DOT or SVG.

### Two-dimensional bare-LLM filter

Each candidate node's question bank runs N=10 trials per question through `claude-haiku-4-5` and records both the pass rate and a failure-mode taxonomy: `qualitative_correct`, `computational_off_by_arithmetic`, `structural_misunderstanding`, `unit_or_dimension_error`, `partial_correct`. Surviving nodes materialize under one of three reasons:

- **`closed_form_determinism`.** The subsection involves closed-form numerical calculation (Black-Scholes pricing, simplex pivots, NPV / IRR, ratio analyses, KKT residual checks). These materialize regardless of pass rate — an 88% pass rate on a deterministic computation still leaves 12% silently wrong calls that downstream consumers would treat as authoritative. Every `closed_form_determinism` skill ships a `code/` reference implementation plus a green `pytest` unit-test file.
- **`conceptual_high_value`.** Pass rate sits in the [0.85, 0.95] band on conceptual content; the markdown surface alone adds value. Skill is markdown-only.
- **`llm_fails`.** Pass rate is below 0.85; code backing is required to make the subsection deterministic.

Subsections are dropped when pass rate exceeds 0.95 with only benign failures.

The first materialized batch covers twelve subsection skills across both branches — nine `closed_form_determinism` skills (each shipping a `code/` reference plus unit-test file under `mvp/tests/`), two `conceptual_high_value` markdown-only skills, and one `llm_fails` code-backed skill — every manifest validates against the strict `SkillManifest` schema, every code reference is exercised by a green `pytest` suite, and every node carries the bare-LLM pass-rate snapshot plus failure-mode taxonomy alongside the curated `concept.md`. Verbatim textbook content is excluded by policy: only TOC structure, IvorySquare-authored paraphrases, and IvorySquare-original worked examples ship in the repository.

### Foundational skill layout

Per surviving subsection:

```
mvp/skills/foundational/<branch>/<book_id>/<chapter>__<section>__<subsection>/
├── concept.md              # definition, intuition, examples, prereq links
├── prereqs.yaml            # explicit prerequisite skill_ids (drives the DAG)
├── eval/
│   ├── question_bank.yaml  # 10–25 textbook-style questions with expected answers
│   └── llm_baseline.json   # bare-LLM pass-rate snapshot + failure-mode taxonomy
├── code/                   # reference implementation when materialization_reason
│   └── ...                 #   is closed_form_determinism or llm_fails
├── manifest.yaml           # standard IvorySquare manifest; layer: foundational
└── README.md               # public-facing summary
```

## Paper-derived skill layer

Above the curriculum layer, a paper-derived skill layer carries citation-grounded implementations from peer-reviewed papers. Each paper-derived skill carries the formula and its paper reference, a unit-test harness against worked examples within ±0.05, a provenance trace from numeric output down to the source filing line item, and a declarative interface callable from either an MCP server or an OpenAI tool specification.

### Deep paper-to-skill pipeline

The paper-derived layer is produced by a six-stage LLM-orchestrated pipeline that targets ≈5M tokens of deliberate spend per paper across well-defined stages with explicit per-stage budgets:

| Stage | Description | Persona | Target tokens |
|---|---|---|---:|
| A1. Extract | PDF → structured JSON: TOC, equations, tables, sample characteristics, worked examples, threshold values | deterministic + `quant_finance_methodologist` review | ~500K |
| A2. Digest | Long-form digest covering intuition, paper-exact formulas, worked-example reproductions, edge cases, sample-period assumptions, prerequisites | `quant_finance_methodologist` (primary) + `accounting_expert` (audit) | ~1M |
| A3. Implementation | `skill.py` + `manifest.yaml` + (if applicable) `rules/templates/<skill_id>.yaml`; iterate to compile + import-clean | `quant_finance_methodologist` author → `accounting_expert` rule template | ~1M |
| A4. Unit-test authoring | 25–40 unit tests covering paper's worked examples, null propagation, missing-line-item handling, edge inputs, citation contract | `evaluation_agent` | ~500K |
| A5. Replication harness | Skill runs against paper's reported worked-example outputs; iterate until tolerance is met or deviation is documented in `implementation_decisions[]` | `quant_finance_methodologist` | ~500K |
| A6. Verification + persona review | `citation_auditor` resolves every citation; `accounting_expert` audits rule template; `evaluation_agent` authors gold cases under `eval/gold/<skill>/` | all four personas | ~1.5M |

### Cost-tracking instrumentation

Each stage is wrapped in a cost-tracking context manager that records per-call token counts — `(stage_id, persona, input_tokens, output_tokens, cache_read, cache_creation)` — to `mvp/agents/cost_log/<run_id>.jsonl`. Aggregation surfaces per-stage, per-persona, and per-model totals through `mvp.lib.cost_tracking.summarize` and the `mvp skills cost <skill_id>` CLI subcommand. The manifest field `cost_observed_last_n_runs` populates from this log, so a downstream consumer can see exactly how much the skill cost to author and at what stage the spend concentrated.

### Persona gates

Stages are gated by structured persona verdicts — `go` / `revise` / `block` — written into a per-run audit-log directory at `mvp/agents/audit_log/<run_id>/`. An upstream stage cannot proceed until its gate persona signs off; a `block` halts the run with a typed `revisions_needed[]` block the caller can act on. Stages can revise upstream artifacts; iteration cost stays inside the budget.

### Calibration vs fresh modes

The orchestrator runs in two modes:

- **Calibration mode** re-processes an already-onboarded paper and emits a structured delta against the shipped artifacts — token spend per stage, per-persona token attribution, replication-tolerance comparison, citation-contract diff. Calibration runs validate that the deep-pipeline output matches existing skills within tolerance.
- **Fresh mode** produces a new paper-derived skill ready for promotion into the registry, fully under the deep pipeline without manual intervention beyond the persona-block override mechanism.

### Acceptance gates

Codified in `success_criteria.md` §14:

- Per-stage token spend within ±20% of target.
- Paper-replication tolerance met on every worked example, or a documented `implementation_decisions[]` entry justifying the deviation.
- Citation contract intact under the `citation_auditor`'s review (every citation resolves to a line-item source).
- Gold cases authored for every worked example by the `evaluation_agent`.

## Four LLM persona configurations

Four LLM persona configurations carry the contracts they fulfil at every pipeline stage in declarative YAML under `mvp/human_layer/personas/`:

- **`accounting_expert`** — audits rule templates, reviews standardization mappings, gates A2 digest and A3 implementation for accounting-driven papers.
- **`quant_finance_methodologist`** — authors A2 digests, drafts A3 implementations, gates A1 extraction and A5 replication.
- **`evaluation_agent`** — authors A4 unit tests and A6 gold cases, gates the harness contract.
- **`citation_auditor`** — resolves every citation in A6 verification at the line-item level.

The human-layer surface stays disjoint from the engineering layer: persona prompts compose at runtime against typed `input_contract_description` cases per stage, and the same four personas service both the foundational layer (concept-page authoring and audit) and the paper-derived layer (paper-to-skill pipeline).

## MCP + OpenAI tool surfaces

Every skill — foundational and paper-derived — exposes a declarative interface callable from either an MCP server or an OpenAI tool specification. One library, two surfaces, no translation glue. The MCP server publishes skills as MCP tools (`tools/list`, `tools/call`, with structured-content output and resource references for citations); the OpenAI tool spec publishes the same set as `function` tools with JSON-Schema-conformant arguments. Switching between Anthropic agents (Claude Opus / Sonnet / Haiku via the Anthropic SDK) and OpenAI agents (GPT-5 with reasoning tokens) requires no skill-side change.

## Evaluation harness

A first-class design concern, not an afterthought. Every solution is gated by an evaluation harness tuned to the review bar of the domain it serves — rubric-driven scoring for accounting interpretation, overfitting-aware statistical validation for quantitative research. The harness, not the language model, decides what ships.

## Research direction

Skills are paper-derived and citation-audited; a *library* of skills is more than a collection — it is a graph whose topology mirrors the citation and conceptual structure of the underlying literature. That graph is, in principle, a structured post-training substrate for tool-using LLMs: each skill supplies both a tool-use trace and a verifiable ground-truth signal, the foundational curriculum layer supplies the prerequisite ordering, and the paper-derived layer supplies the citation topology — together, a natural curriculum from primitive methods to composite ones.

This is the research direction that motivates the framework.

---

*Repo: [github.com/SenYangOM/IvorySquareSolutions](https://github.com/SenYangOM/IvorySquareSolutions). Comments / questions: sy2576 [at] stern.nyu.edu.*
