---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

{% include base_path %}

## AlphaBot — Multi-LLM Agent System for Systematic Alpha Discovery
*Quantitative Research Intern, Cubist (Point72), Sep 2025 – Feb 2026; independent self-funded deployment ongoing.*

A closed-loop multi-LLM pipeline for systematic alpha discovery, deployed and validated on two markets.

- **Three LLMs as orthogonal proposers.** Claude Opus, GPT-5, and Gemini 2.5 Pro generate factor expressions in parallel. Empirically, expression yield ranks **Opus (12.7 expr/call) > GPT-5 (11.0) > Gemini (9.7)**; only ~3.7% of expressions overlap between Opus and GPT-5, so the three LLMs together cover a substantially wider candidate surface than any single one. For cost-effective generation, Opus is prioritized over GPT-5 over Gemini.
- **Scale.** 141/141 successful Step-2 brainstorm calls per alpha (47 centers-of-expertise × 3 LLMs), **1,501 expressions backtested** across Alpha1 → Alpha43, **166 high-Sharpe (>1.0) survivors**, on **>$80K of cumulative LLM-API spend** across the production and research deployments.
- **Harness, not chatbot.** A backtesting harness calibrated to hedge-fund-grade quant-research review — rolling-period statistical validation, odd/even sample consistency, joint train/validate thresholds, strict out-of-sample discipline — is what decides which expressions survive. The language models propose; the harness disposes.
- **Pipeline.** Center-of-expertise generation → multi-LLM brainstorm → consolidate / parse / repair → backtest with train-validate splits → parameter tuning on survivors → out-of-sample holdout. Steps 4–6 are deterministic (zero LLM cost).
- **Two-market validation.**
  - **US equities at Cubist.** 80+ significant meta-alphas across momentum, mean reversion, liquidity, information flow and other risk factors; ensemble prediction models attain promising Sharpe on both large- and small-cap US equities. (Specifics IP-protected; qualitative summary only.)
  - **Self-funded crypto.** An independent deployment on mid-frequency crypto outside Cubist, joint with Beier Liu — [live performance is public](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) over an 18-month track on a self-funded testing account; please set the time range to Jan 1, 2025 to view the full track.

A sanitized technical writeup is in [this blog post](/posts/2026/04/alphabot-multi-llm-alpha-discovery/); deeper details pending Cubist review.

---

## [IvorySquare](https://github.com/SenYangOM/IvorySquareSolutions)
*An open Ivory Tower for everyone. Apr 2026 – present. In collaboration with Han Yan.*

A framework that treats peer-reviewed methodology — across finance, accounting, economics, and operations research — as a first-class tool surface for LLM agents. The architecture composes a layered data and standardization stack (L0 raw → L5 delivery), a foundational curriculum layer at textbook-subsection granularity, a paper-derived skill layer produced by a deep paper-to-skill pipeline, and four LLM persona configurations that gate every artifact.

- **Foundational curriculum layer.** A YAML-backed prerequisite DAG covers ninety-five candidate subsection nodes ingested from eight standard textbooks across two branches — finance/accounting (CFA Level 1 FSA / Equity / Corporate Issuers and a CPA FAR review outline) and operations research (Bertsimas-Tsitsiklis on linear optimization, Boyd-Vandenberghe on convex optimization, Ross on stochastic processes, Ross on probability). Each candidate node passes a two-dimensional bare-LLM filter that records both pass rate and a failure-mode taxonomy (`qualitative_correct`, `computational_off_by_arithmetic`, `structural_misunderstanding`, `unit_or_dimension_error`, `partial_correct`); surviving nodes materialize under one of three reasons — `closed_form_determinism`, `conceptual_high_value`, or `llm_fails`. Twelve materialized subsection skills span both branches: nine `closed_form_determinism` skills (Black-Scholes pricing, simplex pivots, NPV / Gordon growth, KKT residual checks, profitability ratios, depreciation methods, and three more) each shipping a `code/` reference implementation plus a green `pytest` suite; two `conceptual_high_value` markdown-only skills; and one `llm_fails` code-backed skill. The graph is queryable through the `mvp curriculum` CLI (`ingest`, `filter`, `materialize`, `graph`) and renders to Graphviz DOT or SVG. Verbatim textbook content is excluded by policy: only TOC structure, IvorySquare-authored paraphrases, and IvorySquare-original worked examples ship in the repository.
- **Paper-derived skill layer.** A six-stage LLM-orchestrated paper-to-skill pipeline — extraction, long-form digest, implementation, unit-test authoring, replication harness, and three-persona verification — targets ≈5M tokens of deliberate spend per paper across well-defined stages with explicit per-stage budgets. Each stage is wrapped in a cost-tracking context manager that records per-call token counts (input, output, cache read, cache creation) to a per-run JSONL log; aggregation surfaces per-stage, per-persona, and per-model totals through `mvp.lib.cost_tracking.summarize` and the `mvp skills cost <skill_id>` CLI subcommand. Stages are gated by structured persona verdicts — `go` / `revise` / `block` — written into a per-run audit-log directory; an upstream stage cannot proceed until its gate persona signs off, and a `block` halts the run with a typed `revisions_needed[]` block the caller can act on. The orchestrator runs in two modes: a calibration mode that re-processes an already-onboarded paper and emits a structured delta against the shipped artifacts, and a fresh mode that produces a new paper-derived skill ready for promotion into the registry.
- **Persona contracts.** Four LLM persona configurations — `accounting_expert`, `quant_finance_methodologist`, `evaluation_agent`, `citation_auditor` — carry the contracts they fulfil at every pipeline stage in declarative YAML under `mvp/human_layer/personas/`. The human-layer surface stays disjoint from the engineering layer: persona prompts compose at runtime against typed `input_contract_description` cases per stage, citation provenance is resolved at the line-item level, and gold cases are authored for every worked example by the evaluation agent.
- **Acceptance gates.** Codified in `success_criteria.md` §14: per-stage spend within ±20% of target, paper-replication tolerance on every worked example or a documented `implementation_decisions[]` entry, an intact citation contract under the citation-auditor's review, and gold cases authored for every worked example.
- **Tool surfaces.** Every skill — foundational and paper-derived — exposes a declarative interface callable from either an MCP server or an OpenAI tool specification. One library, two surfaces, no translation glue.
- **Open source.** Code, manifests, question banks, persona contracts, and pipeline orchestration all live under [github.com/SenYangOM/IvorySquareSolutions](https://github.com/SenYangOM/IvorySquareSolutions).

A sanitized architectural deep dive is in [this blog post](/posts/2026/04/ivorysquare-architecture/).
