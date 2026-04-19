---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

{% include base_path %}

## [iv_solutions — agent-native accounting interpretation](https://github.com/SenYangOM/iv_solutions)
*Founder & lead engineer, 2025–present*

A machine-readable accounting-interpretation service designed to be consumed by LLM agents as a first-class user. The system ingests SEC filings (XBRL / iXBRL), standardizes them into a layered store (L0 sources → L5 delivery), and exposes a **library of paper-derived skills** — each skill grounded in a peer-reviewed methodology, with provenance and citation auditing built in.

**What's interesting about it:**

* **Agent-native architecture.** Two parallel surfaces — MCP server + OpenAI tool spec — so the same skill library is callable by Claude Code, ChatGPT, and any MCP client without translation glue.
* **Paper-derived skills.** The MVP ships seven skills including a vertical slice of the **Beneish M-Score** and **Altman Z-Score** end-to-end, with each numeric output traceable back to the source filing line item *and* the academic paper that defines the formula.
* **LLM-subagent personas replace human experts.** Four YAML-configurable personas — `accounting_expert`, `quant_finance_methodologist`, `evaluation_agent`, `citation_auditor` — let the system self-validate, catch hallucinated citations, and gate outputs on a per-skill rubric.
* **Closed-loop on Enron 2000.** Canonical demo (`mvp run analyze_for_red_flags --cik 0001024401 --year 2000`) produces a citation-grounded red-flag report on the historical Enron 10-K — a known-positive case used as a regression check on the interpretation engine.
* **380 passing tests** across the L0–L5 stack.

The project explores a research thesis I find under-explored: that a **network of paper-derived skills** — where the topology mirrors the citation/conceptual structure of the literature — could serve as a high-quality **post-training substrate** for tool-using LLMs in narrow technical domains.

---

## AlphaBot — multi-LLM agent for systematic alpha discovery
*Quantitative Research Intern, Cubist (Point72), Sep 2025 – Feb 2026*

A multi-LLM agent pipeline for discovering and validating explainable trading strategies on US equities. Built end-to-end with closed-loop validation against real backtests at hedge-fund production scale.

**What's interesting about it:**

* **Six-stage pipeline with closed-loop validation.** *Brainstorm* (4 LLMs in parallel: Claude Opus, Sonnet, OpenAI, Gemini) → *consolidate* → *parse-and-fix* → *backtest with train/validate splits* → *parameter tuning* → *out-of-sample 2026 holdout*. The harness — not the LLM — decides which alphas survive.
* **80+ validated meta-alphas** across categories: momentum, mean reversion, liquidity, information flow, and other risk factors. Each meta-alpha expanded into broad downstream families with automatic code implementation.
* **Robust selection beyond single-period Sharpe.** Rolling-period statistical validation, odd/even split overfitting controls (e.g., `odd_close_sr × even_close_sr > 0.34`), and joint thresholds on train/validate samples to minimize overfitting to a single regime.
* **Ensemble combination layer.** Trained downstream prediction models that combine surviving alphas across regression families, loss functions, and targets — promising Sharpe ratios attained on both large- and small-cap US equities.
* **Cross-market validation.** The same pipeline architecture is also running on my own self-funded crypto trading account (mid-frequency, ~55% returns over the trailing 12 months on a $10K test account; 18-month track record available on request).

*A sanitized technical writeup is forthcoming — pending Cubist review.*

---

## Working papers

### Adaptive Gradient Descent Algorithms for Online Optimization in Operations
*Sen Yang, Jinzhi Bu, Siyi Wang. Working paper, 2024–.*

Adaptive online stochastic gradient descent for non-stationary environments, achieving state-of-the-art sublinear regret **even when environmental variation is unknown**. Applications to multi-product inventory control, portfolio selection, and broader online convex optimization problems. *arXiv preprint forthcoming.*

### Online Gradient Descent for Multi-Item E-commerce Order Fulfillment
*Sen Yang, Divya Singhvi, Jiawei Zhang. Working paper, 2024–.*

A primal–dual online gradient descent algorithm for the large-scale e-commerce fulfillment problem. The algorithm maintains dual prices for inventory using the **gap between primal solutions and actual fulfillment decisions** as the gradient signal — sidestepping the need for a separate dual oracle. *arXiv preprint forthcoming.*
