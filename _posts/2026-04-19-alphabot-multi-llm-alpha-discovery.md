---
title: "AlphaBot: a multi-LLM agent system for systematic alpha discovery"
date: 2026-04-19
permalink: /posts/2026/04/alphabot-multi-llm-alpha-discovery/
tags:
  - llm-agents
  - quantitative-finance
  - alpha-research
  - backtest
---

> **Status: draft, sanitized public version pending Cubist review.**

## What AlphaBot is

AlphaBot is a multi-LLM agent system that does alpha research the way a quantitative team does: it composes validated patterns into candidate trading signals, backtests them under hedge-fund-grade discipline, and ships only the survivors. Three frontier LLM families propose; the harness disposes.

It runs in two markets: **US equities at Cubist (Point72)**, and an **independent self-funded crypto deployment** outside Cubist with an 18-month public live track.

## Architecture, in layers

AlphaBot's architecture is layered, not stepped — each layer is a typed surface the next one composes on:

- **Data.** Market data — prices, volumes, fundamentals, microstructure features, signals from filings — ingested into a normalized research store with deterministic replay.
- **Centers of Expertise (CoE).** A library of validated patterns and operators drawn from where signal-extraction has been studied seriously: statistics, physics, signal processing, electrical engineering, information theory, and adjacent domains. Each CoE is a compact declarative description of a regularity — a *thematic primitive* the language model can compose against. AlphaBot currently runs across **150+ CoEs**.
- **Skills.** Composable research operations — backtesting under train/validate splits with overfitting controls, feature selection with statistical filters, ensemble prediction models across regression families, loss functions, and targets. Skills consume data and CoE-derived candidates, and produce structured research output.

A research solution sits on top of the three layers: *trading-signal generation.* Three LLMs propose candidate factor expressions conditioned on (data, CoE, skill); the candidates flow through the harness; survivors get traded.

## Why a closed loop matters

The discourse on "LLM-driven research" tends to optimize for the demo. In a real research environment, what matters is whether the system produces signals that survive an out-of-sample regime the model has never seen. That requires a harness, not a chatbot:

- train / validate splits on different time periods,
- odd / even sample splits to catch overfit-to-regime,
- joint thresholds on train *and* validate Sharpe,
- a final out-of-sample holdout the brainstorm LLMs never saw.

The language models propose. The harness disposes.

## Multi-LLM proposal: an empirical ranking

Three frontier model families propose in parallel: Claude Opus, GPT-5, Gemini 2.5 Pro. Across many alpha rounds against the same harness, three signals are stable:

- **Research-output quality.** On this task, **Opus > GPT > Gemini**.
- **Orthogonality.** The two strongest models propose substantially complementary candidates rather than redundant ones — the union of their proposals is materially wider than either alone.
- **Cost-effectiveness.** On a yield-per-dollar basis, Opus is the most cost-effective of the three for research-grade generation.

This is why AlphaBot runs three model families side-by-side: the harness, not the LLM, is the bar that decides what survives, so wider candidate surface is better at the proposal step.

## Scale to date

AlphaBot has brainstormed **over 100,000 candidate signals with reasoning** across 150+ CoEs and three frontier LLM families, and has produced **400+ production-level signals** in the equities deployment, spanning momentum, mean reversion, liquidity, information flow, and other risk-factor categories. Ensemble prediction models combining surviving signals attain promising Sharpe on both large- and small-cap US equities. (Specifics IP-protected; qualitative summary only.)

## The cross-market check

The same architecture runs on a self-funded crypto research project outside Cubist (joint with Beier Liu). [Live performance is public](https://dash.300k.xyz/group/300kinvestorshowcaseaccounts?period=30d) over an 18-month track on a self-funded testing account.

Two markets, same scaffolding — that's the point: when the same agent architecture produces surviving signals in markets with very different microstructure (US equities vs mid-frequency crypto), the architecture is doing real work, not overfitting to a single regime.

---

*Sanitized public version forthcoming.*
