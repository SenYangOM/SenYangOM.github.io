---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

> 📄 **Download PDF:** [SenYang_NYU_CV_Apr27.pdf](/files/SenYang_NYU_CV_Apr27.pdf)
>
> *(Last refreshed April 2026.)*

# Education

* **Ph.D. in Operations Management** — New York University, Stern School of Business *(Sept 2018 – Aug 2025)*
  * Advisors: Jiawei Zhang, Divya Singhvi
  * Research: machine learning, stochastic optimization, convex optimization, online learning
* **B.Sc. in Mathematics** — The Chinese University of Hong Kong *(Sept 2014 – Jun 2018)*
  * **First Class Honours**; GPA 3.77 / 4.00
  * Admission Scholarship — Mainland: tuition fee waived for 4 years

# Experience

* **Cubist (Point72)** — *Quantitative Research Intern, NYC* *(Sep 2025 – Feb 2026)*
  * Built **AlphaBot**, a multi-LLM agent system for systematic alpha discovery on US equities. Identified **80+ significant meta-alphas** across momentum, mean reversion, liquidity, information flow and other risk factors; expanded into broader downstream alpha families with automatic code implementation.
  * Ran Claude Opus, GPT-5, and Gemini 2.5 Pro side-by-side as orthogonal proposers (~3.7% expression overlap between Opus and GPT-5); empirical yield ranking on this task is **Opus 12.7 > GPT-5 11.0 > Gemini 9.7** expressions per call, with Opus the most cost-effective.
  * Pipeline scale: 141/141 successful Step-2 brainstorm calls per alpha (47 CoE × 3 LLMs), **1,501 expressions backtested** across Alpha1 → Alpha43, **166 high-Sharpe (>1.0) survivors**, on **>$80K of cumulative LLM-API spend** across the production and research deployments.
  * Developed rolling-period statistical validation and robust selection pipeline (odd/even split overfitting controls) to minimize overfit-to-regime.
  * Trained ensemble models combining surviving alphas across regression families, loss functions, and targets — promising Sharpe on both large- and small-cap US equities.

* **Optiver US** — *Quantitative Research Summer Intern, Chicago* *(Jun 2024 – Aug 2024)*
  * Volatility-change-rate (VCR) estimation for 0-dte SPXW.
  * Built dynamic rolling-window algorithm + smoothing, lifting **R² from 0.23 to 0.44**.

* **NYU Stern** — *Instructor, J-term 2022*
  * Taught Operations Management. Course evaluation 4.0 / 5.0.

# Personal projects

* **AlphaBot — Personal Deployment.** Independent deployment of the AlphaBot architecture on mid-frequency crypto trading outside Cubist (joint with Beier Liu) as a cross-market validation of the scaffolding. **18-month live track** on a self-funded $10K testing account; [public performance dashboard](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) — set the time range to Jan 1, 2025 to view the full track. Same architecture as the Cubist deployment; different market, same scaffolding produces surviving factors — evidence that the agent system is doing real work rather than overfitting to a single market regime.

* **[IvorySquare](https://github.com/SenYangOM/IvorySquareSolutions)** (*Apr 2026 – present, with Han Yan*) — a framework that treats peer-reviewed methodology as a first-class tool surface for LLM agents. A foundational curriculum layer covers eight textbooks across finance/accounting (CFA L1, CPA FAR) and operations research (Bertsimas-Tsitsiklis, Boyd-Vandenberghe, Ross stochastic, Ross probability) — ninety-five candidate subsection nodes in a prerequisite DAG, twelve materialized subsection skills under a two-dimensional bare-LLM filter (`closed_form_determinism` / `conceptual_high_value` / `llm_fails`), each `closed_form_determinism` skill shipping a deterministic `code/` reference implementation plus a green `pytest` suite. A six-stage LLM-orchestrated paper-to-skill pipeline (extraction, digest, implementation, unit-test authoring, replication harness, three-persona verification) targets ≈5M tokens of deliberate spend per paper with cost tracking and persona gates. Both layers expose MCP and OpenAI tool surfaces.

# Working papers

* *Adaptive Gradient Descent Algorithms for Online Optimization Problems in Operations* — Sen Yang, Jinzhi Bu, Siyi Wang. Working paper, 2024–.
* *Online Gradient Descent Algorithm for Multi-Item E-commerce Order Fulfillment* — Sen Yang, Divya Singhvi, Jiawei Zhang. Working paper, 2024–.

# Awards

* **Funding Master Gold Medal for Graduating Students** — Wu Yee Sun College, CUHK.

# Skills

* **Languages:** Python, MATLAB.
* **LLM-agent stack:** Anthropic SDK (Claude Opus, Sonnet) with extended thinking and prompt caching; OpenAI SDK (GPT-5 with reasoning tokens); Gemini API; Model Context Protocol (MCP) servers.
* **Quant-research stack:** factor research and backtest harness design; rolling-period statistical validation; odd/even-sample consistency checks; ensemble prediction models across regression families, loss functions, and targets.
* **Engineering:** parallel pipelines (`ProcessPoolExecutor`, `ThreadPoolExecutor`); API-rate-limit-aware orchestration across multiple model providers; hard separation between LLM-proposed candidates and harness-decided survivors.
