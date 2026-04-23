---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

{% include base_path %}

## [IvorySquare](https://github.com/SenYangOM/iv_solutions)
*An open Ivory Tower for everyone. 2025–present.*

A system for treating peer-reviewed methodology — across finance, accounting, economics, and operations research — as a first-class tool surface for LLM agents. The architecture has three components:

- **Data.** Ingestion of corporate disclosures (SEC filings, XBRL / iXBRL), market data, and related sources through APIs and MCP connectors, standardized into a typed store (L0 raw → L5 delivery) with deterministic replay.
- **Skills.** A library of citation-grounded, test-verified implementations derived directly from peer-reviewed papers. Each skill carries its formula, its paper reference, its test harness, and a provenance trace from numeric output down to the source filing line item.
- **Solutions.** Compositions of data and skills into workflows and sub-agents for concrete applications — for example, a composite red-flag report that chains fundamental extraction, Beneish M-Score, and Altman Z-Score into a citation-auditable narrative, gated by a purpose-built evaluation harness.

Two parallel tool surfaces — an MCP server and an OpenAI tool specification — expose the skill library to any compatible agent runtime without translation glue. Four LLM sub-agent personas (`accounting_expert`, `quant_finance_methodologist`, `evaluation_agent`, `citation_auditor`) self-validate outputs and flag hallucinated citations before delivery.

A research direction that motivates the broader project is the use of **academic citation networks** — the topology of how ideas build from primitive to composite methods — as a structured post-training substrate for tool-using LLMs.

---

## AlphaBot
*Quantitative Research Intern, Cubist (Point72), Sep 2025 – Feb 2026*

A concrete instance of the *IvorySquare* framework, specialized to systematic alpha discovery on US equities. The system comprises three components and a purpose-built evaluation harness:

- **Data.** Ingestion of US-equities market data — prices, volumes, fundamentals, and microstructure signals — into a normalized research store.
- **Skills.** A library of factor primitives that implement well-established quantitative concepts drawn from statistics, computer science, physics, and operations research, each packaged as a declarative, test-backed skill.
- **Agents.** Sub-agents compose these skills into a research workflow: a brainstorming agent proposes candidate factor expressions from the primitive library; a backtesting agent runs validation under train/validate splits with overfitting-aware selection; a feature-selection agent filters survivors; a prediction-model agent builds ensemble forecasts across regression families, loss functions, and targets.
- **Harness.** An evaluation harness designed to match hedge-fund-grade quant-research review — rolling-period statistical validation, odd/even-sample consistency, joint train/validate thresholds, and strict out-of-sample discipline — is what decides which proposals survive. The harness, not the language model, is the research bar.

The same architecture also runs on an independent self-funded crypto research account outside Cubist, as a cross-market validation of the scaffolding. [Live performance is public](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) — please set the time range to Jan 1, 2025 to view the full track.

*A sanitized technical writeup is forthcoming — pending Cubist review.*
