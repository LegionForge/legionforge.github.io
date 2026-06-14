---
layout: product
title: Jeli
tagline: Sovereign, cryptographically-attested personal memory
subtagline: signed at write, audited end-to-end, lives on your hardware
description: >-
  Jeli is a sovereign personal memory framework — a store of facts, decisions,
  preferences and history that AI assistants read from and contribute to.
  Every entry is signed. Memory provenance is verifiable.
permalink: /jeli/
category: app
product_id: jeli
repo: jeli
---

## What it is

Jeli is a personal memory framework — a sovereign store of facts, decisions, preferences, and history that an AI assistant can read from and contribute to.

- **Sovereign** — lives on your hardware, under your keys. Not in a SaaS database somewhere.
- **Cryptographically attested** — every entry is signed at write time. Tampering and forgery are detectable.

The model: your AI assistant queries Jeli before answering, augmenting the model's context with facts only you have. New facts learned during a conversation get *proposed* back to Jeli for review and signing — humans-in-the-loop on memory persistence.

## Design principles

The same principles that shape LegionForge shape Jeli:

- **Local-first.** Memory lives on your machine. Replication is opt-in and explicit.
- **Cryptographic provenance.** Every entry has a signature. Memory can be audited and replayed.
- **Human gates on writes.** New memories are *proposed* by the assistant and *committed* by you. Same pattern as HITL on destructive tool calls.
- **Replace AI with determinism wherever possible.** Memory retrieval is structured (tags, types, dates) before falling back to embedding search.

## Use cases

- Personal AI assistants that need stable, user-controlled context
- Long-running agents that should accumulate knowledge across sessions
- Compliance scenarios where memory provenance has to be auditable

## Integration with LegionForge

Jeli exposes an MCP server. The LegionForge framework registers Jeli as a context source and gains read / propose access through the standard MCP path. The HITL approval gate in LegionForge handles the "approve this proposed memory" step.

## Status

Active. Public. See the [GitHub repo](https://github.com/LegionForge/jeli) for the latest.
