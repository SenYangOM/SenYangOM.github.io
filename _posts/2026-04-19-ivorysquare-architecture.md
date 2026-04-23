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

> **Status: draft.** A longer writeup is in preparation. The outline below records the framing.

*IvorySquare — an open Ivory Tower for everyone.*

## The premise

Most "AI for finance" tools today are wrappers around chat, with a human as the user of the language model. IvorySquare is built on the inverted premise: the language model is the user, and the system exposes verifiable, citation-grounded methodology as the tool surface it consumes.

The ambition is not a single domain. Finance, accounting, economics, and operations research have produced decades of peer-reviewed methods — each with a formula, a data requirement, an empirical validation, and a citation. Making those methods available to an LLM agent as typed, test-backed, provenance-tracked skills turns the academic literature into a form of infrastructure that agents can call against.

## The architecture

Three components, each with its own contract, plus a purpose-built evaluation harness that gates every solution.

**Data.** Ingestion of corporate disclosures (SEC filings, XBRL / iXBRL), market data, and related sources through APIs and MCP connectors. Standardized into a typed store (L0 raw → L5 delivery) with versioning and deterministic replay.

**Skills.** Citation-grounded implementations derived directly from peer-reviewed papers. Each skill carries:

- the formula and its paper reference;
- a unit-test harness against known cases;
- a provenance trace from numeric output down to the source filing line item;
- a declarative interface callable from either an MCP server or an OpenAI tool specification — one library, two surfaces, no translation glue.

**Solutions.** Compositions of data and skills into workflows and sub-agents for concrete applications. Four LLM sub-agent personas — `accounting_expert`, `quant_finance_methodologist`, `evaluation_agent`, `citation_auditor` — self-validate outputs and flag hallucinated citations before delivery.

**Evaluation harness.** A first-class design concern, not an afterthought. Every solution is gated by an evaluation harness tuned to the review bar of the domain it serves — rubric-driven scoring for accounting interpretation, overfitting-aware statistical validation for quantitative research. The harness, not the language model, decides what ships.

## A worked example

The current vertical slice chains fundamental extraction, the Beneish M-Score, and the Altman Z-Score into a composite red-flag report. Every numeric output in the report is traceable to (a) a specific source filing line item and (b) the academic paper that defines the formula.

## AlphaBot as a solutions instance

*AlphaBot*, the multi-LLM pipeline for systematic alpha discovery I built at Cubist (Point72), is one concrete instance of the *solutions* component — specialized to US-equities alpha research. The same scaffolding — data ingestion, a skill library, composed sub-agents, and an evaluation harness — underpins both the accounting-interpretation vertical and the alpha-research vertical, which is the point of the three-component framing: the solutions component is where domains diverge; the data and skill components are shared infrastructure.

## The research direction

If skills are paper-derived and citation-audited, a *library* of skills is more than a collection — it is a graph whose topology mirrors the citation and conceptual structure of the underlying literature. That graph is, in principle, a structured post-training substrate for tool-using LLMs: each skill supplies both a tool-use trace and a verifiable ground-truth signal, and the citation topology supplies a natural curriculum from primitive methods to composite ones.

This is the research direction I find most promising and the reason the broader framework exists.

---

*Repo: [github.com/SenYangOM/iv_solutions](https://github.com/SenYangOM/iv_solutions) (to be renamed). Comments / questions: sy2576 [at] stern.nyu.edu.*
