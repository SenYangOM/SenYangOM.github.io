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

I am a final-year Ph.D. candidate in Operations Management at NYU Stern, advised by Jiawei Zhang and Divya Singhvi. My work sits at the intersection of online learning, stochastic optimization, and LLM-agent systems. On the theoretical side, I develop adaptive online gradient descent methods for non-stationary environments, together with primal–dual algorithms for large-scale resource allocation; my thesis research is motivated by and applied to problems in inventory control, e-commerce order fulfillment, portfolio selection, and related online convex optimization.

In parallel, I build LLM-agent systems that bring peer-reviewed methodology into practical use. My current project, [iv_solutions](https://github.com/SenYangOM/iv_solutions), treats academic methodology from finance, accounting, economics, and operations research as a first-class tool surface for LLM agents. The system is organized in three layers: a **data layer** that connects to corporate disclosures, standardized filings, and market data through APIs and MCP; a **skill layer** of citation-grounded, test-verified implementations derived directly from peer-reviewed papers; and a **solution layer** that composes data and skills into workflows and sub-agents for concrete applications.

*AlphaBot*, built during a research engagement at Cubist (Point72), is one such solution — a multi-LLM pipeline specialized to systematic alpha discovery on US equities. Language models propose candidate factors; the pipeline parses and backtests them under train/validate splits, and a harness calibrated to hedge-fund-grade quant-research review — not the language model — decides which factors survive. The same architecture also runs on an independent crypto research account outside Cubist as a cross-market check.

A research direction I find particularly promising is the **use of academic citation networks as a structured post-training substrate for tool-using LLMs**. The topology of how ideas build from primitive methods to composite ones is a natural curriculum; a paper-indexed library of verifiable, test-backed skills turns that curriculum into supervised tool-use data.

Before NYU, I received a B.Sc. in Mathematics from the Chinese University of Hong Kong with First Class Honours. I was also a Quantitative Research Summer Intern at Optiver US, working on 0-dte SPXW volatility-change-rate estimation.

I am based in New York City. Email: sy2576 [at] stern [dot] nyu [dot] edu.

<br clear="left"/>

# Research Interests

**Online learning and stochastic optimization**
- adaptive gradient methods
- non-stationary environments
- primal–dual algorithms for resource allocation
- bandit theory

**LLM-agent systems**
- multi-agent pipelines with closed-loop evaluation harnesses
- paper-derived skill libraries
- agent-native tool surfaces (MCP / OpenAI tools)
- tool-use as a post-training substrate

**Quantitative finance applications**
- systematic alpha research
- ensemble modeling for return prediction
- options and volatility estimation
