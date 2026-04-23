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

I earned my Ph.D. in Operations Management at NYU Stern, advised by Jiawei Zhang and Divya Singhvi. My work sits at the intersection of online learning, stochastic optimization, and LLM-agent systems. On the theoretical side, I develop adaptive online gradient descent methods for non-stationary environments, together with primal–dual algorithms for large-scale resource allocation; my thesis research is motivated by and applied to problems in inventory control, e-commerce order fulfillment, portfolio selection, and related online convex optimization.

In parallel, I build LLM-agent systems that bring peer-reviewed methodology into practical use. My current project, [IvorySquare](https://github.com/SenYangOM/IvorySquareSolutions) — an open Ivory Tower for everyone — treats academic methodology from finance, accounting, economics, and operations research as a first-class tool surface for LLM agents. The system is organized around three components: **data** — connections to corporate disclosures, standardized filings, and market data through APIs and MCP; **skills** — citation-grounded, test-verified implementations derived directly from peer-reviewed papers; and **solutions** — compositions of data and skills into workflows and sub-agents for concrete applications, each gated by a purpose-built evaluation harness.

*AlphaBot*, built during a research engagement at Cubist (Point72), is one such solution — a multi-LLM pipeline specialized to systematic alpha discovery on US equities. Language models propose candidate factors; the pipeline parses and backtests them under train/validate splits, and a harness calibrated to hedge-fund-grade quant-research review — not the language model — decides which factors survive. The same architecture also runs on an independent self-funded crypto research account outside Cubist as a cross-market check — [live performance is public](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) (please set the time range to Jan 1, 2025 to view the full track).

A research direction I find particularly promising is the **use of academic citation networks as a structured post-training substrate for tool-using LLMs**. The topology of how ideas build from primitive methods to composite ones is a natural curriculum; a paper-indexed library of verifiable, test-backed skills turns that curriculum into supervised tool-use data.

Before NYU, I received a B.Sc. in Mathematics from the Chinese University of Hong Kong with First Class Honours. I was also a Quantitative Research Summer Intern at Optiver US, working on 0-dte SPXW volatility-change-rate estimation.

I am based in New York City. Email: sy2576 [at] stern [dot] nyu [dot] edu.

<br clear="left"/>

# Research Interests

**Online Learning, Stochastic Optimization, and Sequential Decision-Making**
- Adaptive online stochastic gradient descent and regret minimization in non-stationary environments
- Primal–dual algorithms for online resource allocation (inventory control, e-commerce fulfillment, revenue management)

**LLM-Agent Systems and Tool-Using AI**
- Multi-agent systems and closed-loop agent evaluation
- Tool-using LLMs and post-training for domain-specialized capability
- Evaluation, hallucination mitigation, and trustworthy AI

**Quantitative Finance and Alpha Research**
- Systematic alpha research and explainable factor discovery
