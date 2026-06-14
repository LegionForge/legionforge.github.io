---
layout: product
title: LegionForge Framework
tagline: Local-first AI agent framework with security in the foundation
subtagline: built on LangGraph, runs on your hardware, enforces guardrails in deterministic code
description: >-
  LegionForge is an open-source framework for running hardened AI agent systems
  on your own hardware. Built on LangGraph, runs local LLMs via Ollama or cloud
  APIs, with a full security stack baked into every layer.
permalink: /framework/
category: framework
product_id: framework
repo: LegionForge
docs_path: framework
---

## What it is

LegionForge is the **flagship project** of the LegionForge ecosystem — a framework for building AI agent systems that run on your hardware and behave predictably under adversarial inputs.

It's built on [LangGraph](https://github.com/langchain-ai/langgraph) for the agent graph runtime, [Ollama](https://ollama.com) for local LLM hosting, and a custom security pipeline that wraps every tool call, every LLM invocation, and every input/output boundary in deterministic checks.

## What's in the box

<div class="card-grid">
  <div class="card">
    <div class="card-icon">⚙</div>
    <h3>Local-first LangGraph runtime</h3>
    <p>Agents execute on your hardware. Cloud APIs are optional, not required. Switch providers via env var.</p>
  </div>
  <div class="card">
    <div class="card-icon">▲</div>
    <h3>Deterministic security pipeline</h3>
    <p>Prompt-injection detection, tool revocation, capability-boundary, Ed25519 signing, adaptive threat rules — all in code, none in the model.</p>
  </div>
  <div class="card">
    <div class="card-icon">⟳</div>
    <h3>Three loop-protection layers</h3>
    <p>Step counter, action-history hash, token budget. A single failure can't loop forever.</p>
  </div>
  <div class="card">
    <div class="card-icon">⌥</div>
    <h3>Multi-provider LLM factory</h3>
    <p>Ollama, OpenAI, Anthropic, InceptionLabs behind one interface. Rate-limited, cost-estimated, cloud-fallback ready.</p>
  </div>
  <div class="card">
    <div class="card-icon">▣</div>
    <h3>PostgreSQL state layer</h3>
    <p>Async pool with role separation, LangGraph checkpoint resumption, pgvector RAG, SHA-256 hash-chained audit log.</p>
  </div>
  <div class="card">
    <div class="card-icon">⟶</div>
    <h3>Gateway API</h3>
    <p>FastAPI with task queue, SSE streaming, A2A and MCP endpoints, Bearer auth, web UI with HITL approval gate.</p>
  </div>
  <div class="card">
    <div class="card-icon">⌬</div>
    <h3>Connectors</h3>
    <p>Discord, Telegram, Slack, WhatsApp, generic webhook. Drop-in chat-to-agent bridges.</p>
  </div>
  <div class="card">
    <div class="card-icon">⌘</div>
    <h3>Guardian sidecar</h3>
    <p>7-check deterministic pipeline on every tool call, running in its own container. Sub-5ms latency.</p>
  </div>
</div>

## What makes it different

| Compared to | LegionForge | Their model |
|---|---|---|
| **Cloud agent platforms** (OpenAI Operator, Anthropic Computer Use, Google Mariner) | Runs on your hardware. Your data never leaves. | Runs on their hardware. Your prompts and tool outputs pass through opaque infrastructure. |
| **OSS agent frameworks** (LangChain, AutoGen, CrewAI) | Security enforced deterministically on every tool call. No opt-out. | Flexible substrate. Guardrails are libraries you may or may not add. |
| **Productivity agents** (Devin, OpenDevin, OpenClaw) | Auditable security stack. PostgreSQL audit chain. Role separation. | Vary widely. Recent OpenClaw analysis surfaced 512 vulnerabilities, 8 critical. |

## Status

<div class="stats">
  <div class="stat">
    <span class="stat-value">v0.7.1</span>
    <span class="stat-label">Current version (alpha)</span>
  </div>
  <div class="stat">
    <span class="stat-value">2247</span>
    <span class="stat-label">Smoke tests passing</span>
  </div>
  <div class="stat">
    <span class="stat-value">38</span>
    <span class="stat-label">Integration tests</span>
  </div>
  <div class="stat">
    <span class="stat-value">381</span>
    <span class="stat-label">Operator tools</span>
  </div>
</div>

## Get started

```bash
# Install
git clone https://github.com/LegionForge/LegionForge.git
cd LegionForge
pyenv install 3.11.15 && pyenv local 3.11.15
python3 -m venv venv && source venv/bin/activate
pip install -r requirements.txt

# Configure
export AGENT_HARDWARE_PROFILE=mac_m4_mini_16gb

# Bring up infrastructure and run smoke tests
make check
make db-init
make start
make test-smoke
```

Full setup walkthrough in the [Getting Started guide](https://docs.legionforge.org/framework/getting-started/).

## Read more

- [Architecture](https://docs.legionforge.org/framework/architecture/) — module map, request flow, design principles
- [Security Model](https://docs.legionforge.org/framework/security-model/) — trust boundaries, the security stack, what we catch and don't
- [Guardian](/guardian/) — the deterministic security sidecar
- [Threat Events](https://docs.legionforge.org/framework/threat-events/) — every security-relevant event we log and why
