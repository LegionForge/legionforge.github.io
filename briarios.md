---
layout: product
title: Briarios
tagline: Security-native orchestration meta-layer for parallel agent workstreams
subtagline: triage scoring, model-tier routing, budget gating, and independent verification
description: >-
  Briarios is a security-native orchestration meta-layer for parallel agentic
  development workstreams. It adds issue triage, model-tier routing, resource
  budget gates, and verification pipelines on top of agent execution systems.
permalink: /briarios/
category: orchestration
product_id: briarios
repo: Briarios
---

## What it is

Briarios is a security-native orchestration meta-layer for parallel agentic development workstreams.

It does not replace OpenHands, LangGraph, or managed agent platforms. It sits above them and adds the operational controls needed to run several agent lanes at once: security-aware triage, model-tier routing, multi-resource budget gates, and independent verification before human approval.

## What it adds

<div class="card-grid">
  <div class="card">
    <h3>Security-aware triage</h3>
    <p>Issues are scored by security risk, blast radius, complexity, and blocking impact before assignment.</p>
  </div>
  <div class="card">
    <h3>Model-tier routing</h3>
    <p>High-risk and ambiguous work routes to stronger models; small, bounded tasks can use cheaper lanes.</p>
  </div>
  <div class="card">
    <h3>Budget gates</h3>
    <p>Parallel agent lanes are gated by token budget, CPU load, VRAM headroom, and external API limits.</p>
  </div>
  <div class="card">
    <h3>Verification pipeline</h3>
    <p>Diffs pass through test, review, eval, and security checks before crossing a human merge gate.</p>
  </div>
</div>

## Triage model

Every issue is scored across four axes:

| Axis | What it captures |
|---|---|
| Security risk | Cosmetic change vs. exploitable vulnerability |
| Blast radius | Isolated file vs. cross-cutting subsystem |
| Complexity | Clear implementation vs. architecture decision |
| Blocking | Standalone task vs. blocker for other work |

The score controls agent tier, verification depth, and whether a security-focused review lane is required.

## Status

Research complete. Architectural decisions are accepted and the project is ready for scaffolding.

See the [GitHub repo](https://github.com/LegionForge/Briarios) for the current ADRs and research notes.
