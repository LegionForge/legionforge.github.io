---
layout: product
title: headroom
tagline: System stability monitor with AI-powered diagnostics
subtagline: memory pressure, paging, diagnostic narration in plain language
description: >-
  headroom watches the host for signs of running out of resources and explains
  in plain language what process is the likely culprit. AI diagnosis is opt-in
  and runs locally.
permalink: /headroom/
category: tool
product_id: headroom
repo: headroom
---

## What it is

headroom watches the host for signs that it's running out of resources — and tells you *why* in plain language before the system gets unstable. It samples:

- Resident set size of large processes
- Page-in / page-out rates
- Swap usage trends
- I/O wait

When pressure crosses a threshold, headroom can:

- **Alert** — log to a file, push to a webhook, or surface in a status bar
- **Diagnose** — run an LLM analysis over recent samples to identify which process is the likely culprit and what's typical for that process

The AI diagnosis is **opt-in**, runs locally by default (via the LegionForge framework's `llm_factory` if available, or directly via Ollama), and only invokes when a threshold is crossed — not on every sample.

## When to use it

- You run heavy workloads on a memory-constrained machine and want early warning before things slow down.
- You want a "what's going on right now?" view that doesn't require knowing what to grep for.
- You're operating LegionForge or another local-LLM stack and want diagnostics specific to that workload.

## Integration with LegionForge

headroom complements the framework's `health_metrics` table:

- **`health_metrics`** captures per-task framework resource usage (Ollama RAM, gateway RAM, queue depth).
- **headroom** captures system-wide pressure indicators — the broader context.

Operating both gives you both views: "what is my agent doing" and "what is my machine doing about it".

## Status

Active. Public. See the [GitHub repo](https://github.com/LegionForge/headroom) for the latest.
