---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

{% include base_path %}

## AlphaBot — Multi-LLM Agent System for Systematic Alpha Discovery
*Quantitative Research Intern, Cubist (Point72), Sep 2025 – Feb 2026; independent self-funded deployment ongoing.*

A closed-loop multi-LLM pipeline for systematic alpha discovery, deployed and validated on two markets.

- **Multi-LLM proposal, harness-gated evaluation.** Three frontier model families generate factor expressions in parallel; a backtesting harness — calibrated to hedge-fund-grade quant-research review (rolling-period statistical validation, odd/even sample consistency, joint train/validate thresholds, strict out-of-sample holdout) — is what decides which expressions survive. The language models propose; the harness disposes.
- **Pipeline.** Center-of-expertise generation → multi-LLM brainstorm → consolidate / parse / repair → backtest with train-validate splits → parameter tuning on survivors → out-of-sample holdout.
- **Two-market validation.**
  - **US equities at Cubist.** 80+ significant meta-alphas across momentum, mean reversion, liquidity, information flow and other risk factors; ensemble prediction models attain promising Sharpe on both large- and small-cap US equities. (Specifics IP-protected; qualitative summary only.)
  - **Self-funded crypto.** An independent deployment on mid-frequency crypto outside Cubist, joint with Beier Liu — [public live performance over 18 months](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d).
- **A research finding from the multi-LLM work.** Across the three frontier model families used in the ensemble, research-output quality on this task ranks **Opus > GPT > Gemini**.

A sanitized technical writeup is in [this blog post](/posts/2026/04/alphabot-multi-llm-alpha-discovery/); deeper details pending Cubist review.

---

## [IvorySquare](https://github.com/SenYangOM/IvorySquareSolutions)
*An open Ivory Tower for everyone. Apr 2026 – present. In collaboration with Han Yan.*

A framework that treats peer-reviewed methodology — across finance, accounting, economics, and operations research — as a first-class tool surface for LLM agents. Skills are paper-derived, citation-grounded, and gated by purpose-built evaluation harnesses; the human-expert layer remains disjoint from engineering through declarative persona contracts.

- **Two-tier skill graph.** A foundational concept layer at textbook-subsection granularity, sitting under prerequisite ordering, and a paper-derived methodology layer with formal implementations, worked-example replication, and line-item citation provenance back to the source filing.
- **Tool surfaces.** Every skill — foundational and paper-derived — exposes a declarative interface callable from either an MCP server or an OpenAI tool specification. One library, two surfaces, no translation glue.
- **Persona-driven authorship.** Four LLM persona configurations — accounting expert, quant-finance methodologist, evaluation agent, citation auditor — author and gate every artifact, keeping domain expertise as YAML/markdown rather than Python.
- **Motivating research direction.** Academic citation networks as a structured post-training substrate for tool-using LLMs: each skill supplies both a tool-use trace and a verifiable ground-truth signal, and the citation topology gives a natural curriculum from primitive methods to composite ones.
- **Open source.** [github.com/SenYangOM/IvorySquareSolutions](https://github.com/SenYangOM/IvorySquareSolutions).

A sanitized architectural deep dive is in [this blog post](/posts/2026/04/ivorysquare-architecture/).
