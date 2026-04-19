---
title: "iv_solutions: building accounting interpretation as an LLM-native skill library"
date: 2026-04-19
permalink: /posts/2026/04/iv-solutions-architecture/
tags:
  - llm-agents
  - architecture
  - accounting
  - mcp
---

> **Status: draft.** Full writeup coming soon. Below is the outline I'm filling in.

## The thesis

Most "AI for finance" tools today are wrappers around chat. `iv_solutions` is built on the opposite premise: **the LLM is the user**, not the interface.

A skill is only useful to an agent if it returns *machine-readable, citation-grounded, schema-valid output*. Free-text answers are a regression on an audited spreadsheet, not a step forward.

## The architecture

* **L0–L5 layered store** — sources → ingestion → standardization → interpretation rules + engine → skills library → delivery.
* **Two parallel surfaces** — MCP server + OpenAI tool spec — same skill library, no translation glue.
* **Four LLM-subagent personas** replacing what would historically be human experts: `accounting_expert`, `quant_finance_methodologist`, `evaluation_agent`, `citation_auditor`. Each is a YAML-configurable prompt over a shared Claude / OpenAI runtime.
* **Citation-grounded outputs.** Every numeric output traces back to (a) the source filing line item, (b) the academic paper that defines the formula.

## The MVP slice

Seven skills shipped. Two fundamental, two interpretation, two paper-derived (Beneish M-Score + Altman Z), one composite. 380 passing tests.

Canonical demo:
```
mvp run analyze_for_red_flags --cik 0001024401 --year 2000
```
This runs the full pipeline against the historical Enron 10-K — a known-positive case used as a regression check.

## The bigger bet

If a skill is paper-derived and citation-audited, then a *library* of skills becomes a network whose topology mirrors the citation/conceptual structure of the literature. That network — once large enough — could be a high-quality **post-training substrate** for tool-using LLMs in narrow technical domains, with each skill providing both a tool-use trace *and* a verifiable ground-truth signal.

That's the research direction I'm most excited about.

---

*Repo: [github.com/SenYangOM/iv_solutions](https://github.com/SenYangOM/iv_solutions). Comments / questions: sy2576 [at] stern.nyu.edu.*
