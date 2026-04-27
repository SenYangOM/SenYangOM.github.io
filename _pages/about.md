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

In parallel, I run **AlphaBot**, a multi-LLM agent system for systematic alpha discovery. The architecture treats frontier LLMs as orthogonal proposers and a backtesting harness — calibrated to hedge-fund-grade quant-research review — as the bar that decides what survives. The language models propose; the harness disposes. AlphaBot has been validated on two markets: **US equities at Cubist (Point72)** during my Sep 2025 – Feb 2026 research engagement, where it identified 80+ significant meta-alphas across momentum, mean reversion, liquidity, and information flow; and an **independent self-funded crypto deployment** outside Cubist with [public live performance over 18 months](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d). One research finding from running the same task across three frontier model families: research-output quality ranks **Opus > GPT > Gemini**.

*[IvorySquare](https://github.com/SenYangOM/IvorySquareSolutions)* (Apr 2026 – present, with Han Yan) treats peer-reviewed methodology — across finance, accounting, economics, and operations research — as a first-class tool surface for LLM agents. Skills are paper-derived, citation-grounded, and gated by purpose-built evaluation harnesses; the human-expert layer remains disjoint from engineering through declarative persona contracts. The skill graph is structured in two coupled tiers — a foundational concept layer at textbook-subsection granularity under prerequisite ordering, and a paper-derived methodology layer with formal implementations and line-item citation provenance — both exposed as declarative MCP and OpenAI tool surfaces.

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
