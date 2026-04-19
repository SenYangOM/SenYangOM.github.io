---
title: "AlphaBot: a closed-loop multi-LLM agent for systematic alpha discovery"
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

A six-stage pipeline that turns *vague intuitions about market microstructure* into *backtested, code-implemented, robustly-validated alphas* — with four different LLMs collaborating on the brainstorming step and a hedge-fund-grade harness deciding what survives.

## Why a closed-loop matters

The discourse on "LLM-driven research" tends to optimize for the demo. In a real research environment, what matters is whether the pipeline produces alphas that **survive an out-of-sample regime that the model has never seen**.

That requires a harness, not a chatbot:

* train / validate splits on different time periods,
* odd / even sample splits to catch overfit-to-regime (`odd_close_sr × even_close_sr > 0.34` before an alpha is even considered),
* joint thresholds on train *and* validate Sharpe before an alpha exits the funnel,
* a final 2026 holdout the brainstorm LLMs never saw.

The LLMs propose. The harness disposes.

## The six steps

1. **Name cards** — Claude Opus generates ~50 "centers of expertise" (CoEs), each a thematic primitive (e.g. *information flow into the close*).
2. **Brainstorm** — 4 LLMs in parallel (Claude Opus, Sonnet, OpenAI, Gemini) propose declarative alpha expressions per CoE.
3. **Consolidate + parse-and-fix** — dedupe and convert into runnable factor expressions.
4. **Backtest with train/validate splits.**
5. **Parameter tuning** on survivors.
6. **Out-of-sample 2026 holdout** — the only number that matters.

## The cross-market check

The same pipeline architecture also runs on a self-funded crypto research account I keep outside Cubist — mid-frequency, ~55% trailing-year returns on a $10K test capital, 18-month live track. Two different markets, same scaffolding. The diversity is the point.

---

*Sanitized public version forthcoming.*
