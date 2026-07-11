---
layout: product
title: idn-analyzer
tagline: Offline prompt profiler for LLM routing decisions
subtagline: know what a prompt needs before choosing where to serve it
description: >-
  idn-analyzer is a lightweight, offline-capable prompt profiler for LLM
  applications. It estimates complexity, domain, PII risk, routing tier, and
  execution requirements before an LLM call is made.
permalink: /idn-analyzer/
category: tool
product_id: idn-analyzer
repo: Intelligence-Delivery-Network-Request-Analyzer
---

## What it is

idn-analyzer is a lightweight prompt profiler for LLM applications. It analyzes natural-language prompts and returns structured metadata about complexity, domain, PII risk, recommended routing tier, and execution requirements before any model call is made.

It is the analytical core of the [Intelligence Delivery Network](/intelligence-delivery-network/), but it is designed to stand alone inside any LLM app, gateway, or router.

## What it returns

```json
{
  "token_estimate": 312,
  "complexity_score": 0.74,
  "reasoning_hops": 2,
  "domain_tags": ["coding"],
  "pii_risk": "none",
  "data_egress_permitted": true,
  "recommended_tier": "L2",
  "confidence": 0.91
}
```

## Design goals

<div class="card-grid">
  <div class="card">
    <h3>Offline-capable</h3>
    <p>Layer 1 analysis is rules-based and does not require a network call or model invocation.</p>
  </div>
  <div class="card">
    <h3>PII-aware</h3>
    <p>Prompts can be flagged for sensitive data and compliance constraints before cloud egress.</p>
  </div>
  <div class="card">
    <h3>Gateway-agnostic</h3>
    <p>The output schema is meant to feed any custom router, LiteLLM-style proxy, or app-level policy engine.</p>
  </div>
  <div class="card">
    <h3>Cross-platform</h3>
    <p>The roadmap includes Python, JavaScript, C/C++, WebAssembly, mobile, and embedded targets.</p>
  </div>
</div>

## Status

Development is currently on hold. The repository captures the pre-alpha design, schema, CLI shape, and platform roadmap.

See the [GitHub repo](https://github.com/LegionForge/Intelligence-Delivery-Network-Request-Analyzer) for the current source.
