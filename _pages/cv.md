---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

> 📄 **Download PDF:** [SenYang_NYU_CV.pdf](/files/SenYang_NYU_CV.pdf)
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
  * Developed rolling-period statistical validation and robust selection pipeline (odd/even split overfitting controls) to minimize overfit-to-regime.
  * Trained ensemble models combining surviving alphas across regression families, loss functions, and targets — promising Sharpe on both large- and small-cap US equities.

* **Optiver US** — *Quantitative Research Summer Intern, Chicago* *(Jun 2024 – Aug 2024)*
  * Volatility-change-rate (VCR) estimation for 0-dte SPXW.
  * Built dynamic rolling-window algorithm + smoothing, lifting **R² from 0.23 to 0.44**.

* **NYU Stern** — *Instructor, J-term 2022*
  * Taught Operations Management. Course evaluation 4.0 / 5.0.

# Personal projects

* **[`iv_solutions`](https://github.com/SenYangOM/iv_solutions)** — a framework that treats peer-reviewed methodology from finance, accounting, economics, and operations research as a first-class tool surface for LLM agents. Three interacting components — *data* (ingestion from corporate disclosures and market sources through APIs and MCP), *skills* (a library of citation-grounded, test-verified implementations derived directly from academic papers, each carrying its formula, paper reference, test harness, and provenance trace), and *solutions* (workflows and sub-agents that compose data and skills into concrete applications) — each solution gated by a purpose-built evaluation harness. The skill library is exposed through parallel MCP and OpenAI tool specifications; four LLM sub-agent personas (`accounting_expert`, `quant_finance_methodologist`, `evaluation_agent`, `citation_auditor`) self-validate outputs and flag hallucinated citations before delivery. A research direction that motivates the framework is the use of academic citation networks as a structured post-training substrate for tool-using LLMs.

* **Self-funded crypto research account** — an independent deployment of the AlphaBot architecture on mid-frequency crypto trading outside Cubist, as a cross-market validation of the scaffolding. 18-month live track on a self-funded $10K testing account; [public performance dashboard](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) — set the time range to Jan 1, 2025 to view the full track.

# Working papers

* *Adaptive Gradient Descent Algorithms for Online Optimization Problems in Operations* — Sen Yang, Jinzhi Bu, Siyi Wang. Working paper, 2024–.
* *Online Gradient Descent Algorithm for Multi-Item E-commerce Order Fulfillment* — Sen Yang, Divya Singhvi, Jiawei Zhang. Working paper, 2024–.

# Awards

* **Funding Master Gold Medal for Graduating Students** — Wu Yee Sun College, CUHK.

# Skills

* **Languages:** Python (research + production), MATLAB, LaTeX. Working: Bash, SQL.
* **ML / agents:** PyTorch, scikit-learn, multi-LLM orchestration (Claude, OpenAI, Gemini), MCP, agent design.
* **Quant tools:** statistical alpha research, ensemble modeling, factor analysis, options theory.
