---
title: "Online gradient descent for multi-item e-commerce fulfillment, in plain words"
date: 2026-04-19
permalink: /posts/2026/04/ogd-for-fulfillment/
tags:
  - online-learning
  - operations-research
  - stochastic-optimization
---

> **Status: outline.** A non-technical reader-facing summary of joint work with Divya Singhvi and Jiawei Zhang.

## The problem

When an e-commerce order arrives, the platform must decide *which fulfillment center* ships *which item*. This is a large-scale online decision problem with two coupled difficulties:

1. **Inventory is a binding constraint** — once it's gone, it's gone.
2. **You don't see the future** — orders arrive sequentially, and the right decision depends on which orders you'll see next.

The classical primal-dual approach handles this by maintaining **dual prices** for each (item × fulfillment center) — a shadow price that says "use this inventory only if the immediate gain exceeds this threshold." The hard part is keeping those dual prices accurate as the world drifts.

## The trick

We propose an **online gradient descent** on the dual prices. The novel piece: instead of needing a separate dual oracle to compute the gradient, we use **the gap between the LP-relaxed primal solution and the integer fulfillment decision actually taken** as a free, accurate gradient signal.

This sidesteps a chunk of machinery and gets us competitive regret bounds on a problem class that previously required heavier methods.

## Why it matters beyond fulfillment

The same primal–dual + OGD scaffolding shows up in:

* online ad allocation under budget constraints,
* dynamic pricing with inventory,
* portfolio rebalancing with leverage caps.

The "gap as gradient" trick is a small idea that generalizes.

---

*Working paper with Divya Singhvi and Jiawei Zhang, 2024–. arXiv preprint forthcoming.*
