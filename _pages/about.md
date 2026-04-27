---
permalink: /
title: "Sen Yang 杨森"
excerpt: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

![profile](https://github.com/SenYangOM/SenYangOM.github.io/blob/main/images/profile.jpg?raw=true){: width="280px" style="float:left; padding-right:35px" }

I earned my Ph.D. in Operations Management at NYU Stern, advised by Jiawei Zhang and Divya Singhvi. My work sits at the intersection of online learning, stochastic optimization, and LLM-agent systems for quantitative research. On the theoretical side, I develop adaptive online gradient descent methods for non-stationary environments, together with primal–dual algorithms for large-scale resource allocation; my thesis research is motivated by and applied to problems in inventory control, e-commerce order fulfillment, portfolio selection, and related online convex optimization.

In parallel, I run **AlphaBot**, a multi-LLM agent system for systematic alpha discovery deployed across two markets. The system runs Opus, GPT-5, and Gemini 2.5 Pro side-by-side as orthogonal proposers — only ~3.7% of the expressions Opus suggests overlap with what GPT-5 suggests, so the three LLMs combine into a substantially wider candidate surface than any single one. A backtesting harness calibrated to hedge-fund-grade quant-research review (rolling-period statistical validation, odd/even sample consistency, joint train/validate thresholds, and out-of-sample holdout) decides which expressions survive — the language models propose, the harness disposes. To date the pipeline has executed 141/141 successful Step-2 brainstorm calls per alpha (47 centers-of-expertise × 3 LLMs), backtested **1,501 expressions**, and produced **166 high-Sharpe (>1.0) survivors** across Alpha1 → Alpha43, on **>$80K of cumulative LLM-API spend** across the production and research deployments. An empirical signal that fell out of this work: for quant-research generation, expression yield ranks Opus (12.7 expr/call) > GPT-5 (11.0) > Gemini (9.7), and Opus is the most cost-effective on a yield-per-dollar basis. AlphaBot has been validated on two markets: **US equities at Cubist (Point72)** during my Sep 2025 – Feb 2026 research engagement, where it identified 80+ significant meta-alphas across momentum, mean reversion, liquidity, and information flow with promising Sharpe on both large- and small-cap names (qualitative summary; specifics IP-protected); and an **independent self-funded crypto deployment** that I run outside Cubist with [public live performance over 18 months](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) — please set the time range to Jan 1, 2025 to view the full track.

*[IvorySquare](https://github.com/SenYangOM/IvorySquareSolutions)* (Apr 2026 – present, with Han Yan) treats peer-reviewed methodology — across finance, accounting, economics, and operations research — as a first-class tool surface for LLM agents. The skill graph is anchored at the bottom by a foundational curriculum layer of textbook-subsection-granular concept skills sourced from eight standard texts (CFA Level 1 FSA / Equity / Corporate Issuers, a CPA FAR review outline, Bertsimas-Tsitsiklis on linear optimization, Boyd-Vandenberghe on convex optimization, Ross on stochastic processes, Ross on probability), with ninety-five candidate subsection nodes in a prerequisite DAG and a two-dimensional bare-LLM filter that materializes each surviving node under one of three reasons — `closed_form_determinism` (closed-form arithmetic ships with a deterministic `code/` reference implementation), `conceptual_high_value` (markdown-only concept page), or `llm_fails`. Above the curriculum layer, a paper-derived skill layer is produced by a six-stage LLM-orchestrated pipeline — extraction, long-form digest, implementation, unit-test authoring, replication harness, three-persona verification — wrapped in cost-tracking instrumentation that records per-call token counts to a per-run JSONL log and gates each stage with structured persona verdicts (`go` / `revise` / `block`). Both layers expose a declarative interface callable from either an MCP server or an OpenAI tool specification.

A research direction I find particularly promising is the **use of academic citation networks as a structured post-training substrate for tool-using LLMs**. The topology of how ideas build from primitive methods to composite ones is a natural curriculum; a paper-indexed library of verifiable, test-backed skills turns that curriculum into supervised tool-use data.

Before NYU, I received a B.Sc. in Mathematics from the Chinese University of Hong Kong with First Class Honours. I was also a Quantitative Research Summer Intern at Optiver US, working on 0-dte SPXW volatility-change-rate estimation.

I am based in New York City. Email: sy2576 [at] stern [dot] nyu [dot] edu.

<br clear="left"/>

# Research Interests

**LLM-Agent Systems and Tool-Using AI**
- Multi-LLM agent pipelines and closed-loop agent evaluation
- Tool-using LLMs and post-training for domain-specialized capability
- Evaluation, hallucination mitigation, and trustworthy AI

**Quantitative Finance and Alpha Research**
- Systematic alpha research and explainable factor discovery
- Multi-market validation of agent architectures (equities, crypto)

**Online Learning, Stochastic Optimization, and Sequential Decision-Making**
- Adaptive online stochastic gradient descent and regret minimization in non-stationary environments
- Primal–dual algorithms for online resource allocation (inventory control, e-commerce fulfillment, revenue management)
