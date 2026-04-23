---
title: "AlphaBot: a closed-loop multi-LLM pipeline for systematic alpha discovery"
date: 2026-04-19
permalink: /posts/2026/04/alphabot-multi-llm-alpha-discovery/
tags:
  - llm-agents
  - quantitative-finance
  - alpha-research
  - backtest
---

> **Status: draft, sanitized version pending Cubist review.** Below is the outline of the public writeup.

## What it is

A pipeline that takes hypotheses about market microstructure — expressed as declarative primitives — through brainstorming, parsing, and harness-gated backtesting, and returns factor expressions that survive out-of-sample evaluation. Four language models collaborate on the proposal step; a harness calibrated to hedge-fund-grade quant-research review decides what survives.

AlphaBot is one concrete instance of the broader [IvorySquare](/posts/2026/04/ivorysquare-architecture/) framework, specialized to US-equities alpha research.

## Why a closed loop matters

The discourse on "LLM-driven research" tends to optimize for the demo. In a real research environment, what matters is whether the pipeline produces alphas that survive an out-of-sample regime the model has never seen.

That requires a harness, not a chatbot:

- train / validate splits on different time periods,
- odd / even sample splits to catch overfit-to-regime before an alpha is considered,
- joint thresholds on train *and* validate Sharpe before an alpha exits the funnel,
- a final out-of-sample holdout the brainstorm LLMs never saw.

The language models propose. The harness disposes.

## The pipeline

1. **Primitive generation.** Claude Opus generates thematic primitives — centers of expertise — each a compact declarative description of a market-microstructure regularity (e.g. *information flow into the close*).
2. **Brainstorm.** Four language models in parallel (Claude Opus, Sonnet, OpenAI, Gemini) propose factor expressions per primitive.
3. **Consolidate, parse, and repair.** Dedupe and convert proposals into runnable factor expressions.
4. **Backtest with train / validate splits.**
5. **Parameter tuning** on survivors.
6. **Out-of-sample holdout** — the only number that matters.

## The cross-market check

The same pipeline architecture also runs on a self-funded crypto research project I keep outside Cubist. Two different markets, same scaffolding — which is the point: when the same agent architecture produces surviving factors in markets with very different microstructure, the scaffolding is doing real work.

---

*Sanitized public version forthcoming.*
