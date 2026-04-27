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

A closed-loop pipeline that takes hypotheses about market microstructure — expressed as declarative primitives — through brainstorming, parsing, and harness-gated backtesting, and returns factor expressions that survive out-of-sample evaluation. Three frontier LLMs collaborate on the proposal step, each running side-by-side as an orthogonal proposer; a backtest harness calibrated to hedge-fund-grade quant-research review decides what survives. AlphaBot has been deployed and validated on two markets: US equities at Cubist (Point72), and an independent self-funded crypto deployment with an 18-month live track that I run outside Cubist.

## Why a closed loop matters

The discourse on "LLM-driven research" tends to optimize for the demo. In a real research environment, what matters is whether the pipeline produces alphas that survive an out-of-sample regime the model has never seen.

That requires a harness, not a chatbot:

- train / validate splits on different time periods,
- odd / even sample splits to catch overfit-to-regime before an alpha is considered,
- joint thresholds on train *and* validate Sharpe before an alpha exits the funnel,
- a final out-of-sample holdout the brainstorm LLMs never saw.

The language models propose. The harness disposes.

## Multi-LLM proposal: an empirical ranking

Across 47 centers-of-expertise (CoE) per alpha, three LLMs generate factor expressions in parallel. After 43 alpha rounds, two empirical signals are stable:

- **Yield ranking (expressions per brainstorm call):** **Opus 12.7 > GPT-5 11.0 > Gemini 9.7**.
- **Orthogonality:** only ~3.7% expression overlap between Opus and GPT-5 — the two strongest models propose substantially complementary candidates rather than redundant ones.
- **Cost-effectiveness:** prioritize Opus over GPT-5 over Gemini for cost-effective generation, on a yield-per-dollar basis.

This is why AlphaBot runs three LLMs side-by-side. A single LLM, even the highest-yielding one, would surface a much narrower candidate surface than the union — and the harness, not the LLM, is the bar that decides which expressions survive, so wider is better at the proposal step.

## The pipeline

1. **Center-of-expertise generation.** Claude Opus generates thematic primitives — centers of expertise — each a compact declarative description of a market-microstructure regularity (e.g. *information flow into the close*).
2. **Brainstorm.** Three LLMs in parallel (Claude Opus, GPT-5, Gemini 2.5 Pro) propose factor expressions per CoE. 47 CoE × 3 LLMs = 141 brainstorm calls per alpha; 141/141 successful in production.
3. **Consolidate, parse, and repair.** Dedupe and convert proposals into runnable factor expressions; recover paren imbalances; filter structurally broken patterns.
4. **Backtest with train / validate splits.** Odd/even sample consistency, joint Sharpe thresholds.
5. **Parameter tuning** on survivors. Deterministic, zero LLM cost (tree-based parameter identification).
6. **Out-of-sample holdout** — the only number that matters.

## Scale to date

Across Alpha1 → Alpha43:

- **1,501 expressions backtested** end-to-end through the harness.
- **166 high-Sharpe (>1.0) survivors** after train/validate filtering.
- **80+ significant meta-alphas** identified across momentum, mean reversion, liquidity, information flow, and other risk factors on US equities.
- Ensemble prediction models combining surviving alphas attain **promising Sharpe on both large- and small-cap US equities** (specifics IP-protected).
- **>$80K of cumulative LLM-API spend** across the production and research deployments. The empirical yield, orthogonality, and cost-effectiveness numbers above are anchored on this scale of usage — not a small benchmark sample.

## The cross-market check

The same pipeline architecture also runs on a self-funded crypto research project I keep outside Cubist (joint work with Beier Liu). [Live performance is public](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) — please set the time range to Jan 1, 2025 to view the full **18-month live track** on a self-funded testing account.

Two markets, same scaffolding — which is the point: when the same agent architecture produces surviving factors in markets with very different microstructure (US equities vs mid-frequency crypto), the scaffolding is doing real work, not overfitting to a single regime.

---

*Sanitized public version forthcoming.*
