---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

{% include base_path %}

## [iv_solutions](https://github.com/SenYangOM/iv_solutions)
*2025–present*

A system for treating peer-reviewed methodology — across finance, accounting, economics, and operations research — as a first-class tool surface for LLM agents. The architecture is three-layered:

- **Data layer.** Ingestion of corporate disclosures (SEC filings, XBRL / iXBRL), market data, and related sources through APIs and MCP connectors, standardized into a layered store (L0 raw → L5 delivery) with typed schemas and deterministic replay.
- **Skill layer.** A library of citation-grounded, test-verified implementations derived directly from peer-reviewed papers. Each skill carries its formula, its paper reference, its test harness, and a provenance trace from numeric output down to the source filing line item.
- **Solution layer.** Compositions of data and skills into workflows and sub-agents for concrete applications — for example, a composite red-flag report that chains fundamental extraction, Beneish M-Score, and Altman Z-Score into a citation-auditable narrative.

Two parallel tool surfaces — an MCP server and an OpenAI tool specification — expose the skill library to any compatible agent runtime without translation glue. Four LLM sub-agent personas (`accounting_expert`, `quant_finance_methodologist`, `evaluation_agent`, `citation_auditor`) self-validate outputs and flag hallucinated citations before delivery.

A research direction that motivates the broader project is the use of **academic citation networks** — the topology of how ideas build from primitive to composite methods — as a structured post-training substrate for tool-using LLMs.

---

## AlphaBot
*Quantitative Research Intern, Cubist (Point72), Sep 2025 – Feb 2026*

A concrete instance of the *iv_solutions* solution layer, specialized to systematic alpha discovery on US equities. Four language models — Claude Opus, Sonnet, OpenAI, and Gemini — propose candidate factor expressions, conditioned on a declarative primitive library. Proposals are parsed, syntactically repaired, and backtested under train/validate splits with overfitting-aware selection (rolling-period statistical validation, odd/even-sample consistency checks, joint train/validate Sharpe thresholds). Survivors are parameter-tuned and evaluated on an out-of-sample holdout; a harness calibrated to hedge-fund-grade quant-research review — not the language model — decides what survives. Downstream, surviving factors feed ensemble prediction models across regression families, loss functions, and targets.

The same architecture also runs on an independent self-funded crypto research account outside Cubist, as a cross-market validation of the scaffolding.

*A sanitized technical writeup is forthcoming — pending Cubist review.*

---

## Working papers

### Adaptive Gradient Descent Algorithms for Online Optimization in Operations
*Sen Yang, Jinzhi Bu, Siyi Wang. Working paper, 2024–.*

Adaptive online stochastic gradient descent for non-stationary environments, achieving state-of-the-art sublinear regret **even when the magnitude of environmental variation is unknown a priori**. Applications to multi-product inventory control, portfolio selection, and broader online convex optimization problems. *arXiv preprint forthcoming.*

### Online Gradient Descent for Multi-Item E-commerce Order Fulfillment
*Sen Yang, Divya Singhvi, Jiawei Zhang. Working paper, 2024–.*

A primal–dual online gradient descent algorithm for the large-scale e-commerce fulfillment problem. The algorithm maintains dual prices for inventory using the gap between LP-relaxed primal solutions and actual fulfillment decisions as the gradient signal, sidestepping the need for a separate dual oracle. *arXiv preprint forthcoming.*
