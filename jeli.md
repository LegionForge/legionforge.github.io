---
layout: product
title: Jeli
tagline: Security and governance layer for sovereign personal memory
subtagline: hash-chained provenance, constitutional rules, judicial conflict resolution, portable memory
description: >-
  Jeli is a security and governance layer for personal memory systems. It keeps
  memory local-first, tamper-evident, trust-scored, portable, and governed by
  user-signed rules.
permalink: /jeli/
category: app
product_id: jeli
repo: jeli
---

## What it is

Jeli is a security and governance layer for personal AI memory systems. It keeps facts, decisions, preferences, history, and agent-written context under your control, with a verifiable chain of custody for every memory.

It is not a promise that memory can be made perfectly secure. Jeli makes poisoning and tampering harder, more visible, and easier to audit through configurable layers: cryptographic provenance, trust scoring, user-signed rules, conflict resolution, and exportable data.

## What changed

The project has moved beyond a simple personal memory store. Jeli now implements a three-branch governance model for memory:

<div class="card-grid">
  <div class="card">
    <h3>Executive: agents</h3>
    <p>Agents propose memories through a scoped MCP server. They cannot write directly to the database or claim user-level trust.</p>
  </div>
  <div class="card">
    <h3>Legislative: storage</h3>
    <p>PostgreSQL and pgvector hold an append-only, HMAC hash-chained memory log with audit rows and state events.</p>
  </div>
  <div class="card">
    <h3>Judicial: resolution</h3>
    <p>Daemons arbitrate contradictions, record precedent, and escalate unresolved conflicts for human review.</p>
  </div>
  <div class="card">
    <h3>Constitutional: user rules</h3>
    <p>User-signed rules can block writes, cap trust, filter reads, and enforce non-negotiable memory policy.</p>
  </div>
</div>

## Current capabilities

- **Hash-chained memory writes** with per-record signing-key identity and `jeli verify` integrity checks.
- **Scoped MCP access** for `capture_memory`, `search_memory`, `audit_trail`, `search_by_entity`, and entity graph reads.
- **Trust-scored provenance** distinguishing user-direct, user-confirmed, agent-inferred, behavior-inferred, external, and flagged content.
- **Layered injection defense** using regex checks, Unicode normalization, content-class stigma, and an optional LLM second pass.
- **Constitutional read/write gates** over user-signed rules that agents cannot override.
- **Judicial conflict resolution** with precedent case law and human escalation for unresolved contradictions.
- **Ingestion Bouncer** for staged capture, deduplication, classification, and safe promotion into the hash chain.
- **Entity graph extraction** for people, projects, organizations, technologies, and relations.
- **Memory portability** through JSON-Lines export/import with tamper detection and local re-embedding.
- **Local-first embeddings** via Ollama by default, with OpenAI as an explicit opt-in provider.

## Why it matters

Memory is becoming one of the most important parts of AI infrastructure. If your assistant remembers your preferences, work, relationships, decisions, and identity, you need more than convenience. You need custody, provenance, revision history, conflict handling, and a real exit path.

Jeli is built so memory remains something you can inspect, move, verify, revise, invalidate, redact, and govern.

## Status

v0.2.0-alpha. The three-branch governance model is implemented and tested, including the constitutional layer, judicial precedent, entity graph, portability, ingestion bouncer, and read/write defense layers. Jeli has been deployed on local hardware since v0.1.0-alpha.

See the [GitHub repo](https://github.com/LegionForge/jeli) for the latest status, threat model, and trust doctrine.
