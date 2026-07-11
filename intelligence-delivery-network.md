---
layout: product
title: Intelligence Delivery Network
tagline: CDN-style routing model for LLM workloads
subtagline: route requests to the right compute tier before spending frontier-model money
description: >-
  Intelligence Delivery Network is a CDN-inspired routing architecture for LLM
  workloads. It profiles prompts and routes them across on-device, edge,
  regional, and frontier compute tiers.
permalink: /intelligence-delivery-network/
category: research
product_id: intelligence-delivery-network
repo: Intelligence-Delivery-Network
---

## What it is

Intelligence Delivery Network, or IDN, is a CDN-style architecture for AI workloads. Instead of sending every request to the same large model, IDN profiles the request first and routes it to the compute tier that fits its complexity, privacy needs, latency target, and tool requirements.

The central idea is simple: trivial, private, or latency-sensitive requests should stay close to the user; expensive global frontier models should be reserved for work that actually needs them.

## The tier model

| Tier | Location | Typical use |
|---|---|---|
| L0 | On-device | Offline use, privacy-forced prompts, PII preprocessing |
| L1 | Edge | Fast extraction, classification, lightweight RAG |
| L2 | Regional | Coding, summarization, document workflows, tool agents |
| L3 | Global | Deep reasoning, research synthesis, multi-agent planning |

## Core components

<div class="card-grid">
  <div class="card">
    <h3>Workload profiler</h3>
    <p>Analyzes token size, complexity, reasoning hops, domain, PII risk, and latency sensitivity.</p>
  </div>
  <div class="card">
    <h3>Router</h3>
    <p>Maps profiler output to a tier, expert model, tool plan, fallback path, and cost estimate.</p>
  </div>
  <div class="card">
    <h3>L0 privacy firewall</h3>
    <p>Keeps data on-device when egress is blocked and can redact sensitive fields before escalation.</p>
  </div>
  <div class="card">
    <h3>Async planner</h3>
    <p>Splits multi-part requests into subtasks that can route to different tiers and merge cleanly.</p>
  </div>
</div>

## Status

Development is currently on hold. The repository captures the architecture, routing model, profiler schema, and prototype direction.

See the [GitHub repo](https://github.com/LegionForge/Intelligence-Delivery-Network) for the current design notes.
