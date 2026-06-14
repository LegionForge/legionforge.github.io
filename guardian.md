---
layout: product
title: Guardian
tagline: Deterministic security sidecar for AI agent frameworks
subtagline: drop-in protection against prompt injection, tool poisoning, capability abuse
description: >-
  Guardian is a deterministic security sidecar for LLM agent frameworks. Sub-5ms
  per check. Works with any framework via HTTP — LangChain, LangGraph, AutoGen,
  CrewAI, custom. Open source, MIT-licensed.
permalink: /guardian/
category: security
product_id: guardian
repo: guardian
docs_path: guardian
---

## What it is

Guardian is a **deterministic security sidecar** for AI agent frameworks. It runs as a separate FastAPI service in a Docker container. Every tool invocation in your agent stack POSTs to Guardian's `/check` endpoint before executing. Guardian runs 7 checks in sub-5ms and returns allow or deny.

The checks are deterministic — no LLM in the hot path — so latency is predictable, cost is zero, and adversarial robustness is high.

## The 7 checks

<div class="card-grid">
  <div class="card">
    <h3>1. Tool revocation list</h3>
    <p>Known-bad tool IDs. Instant deny.</p>
  </div>
  <div class="card">
    <h3>2. Hash validation</h3>
    <p>Live tool code hashed and compared to registered hash. Catches supply-chain tool tampering.</p>
  </div>
  <div class="card">
    <h3>3. Capability boundary</h3>
    <p>Tool's required capability must be in the task's authorized scope. Stops capability creep.</p>
  </div>
  <div class="card">
    <h3>4. Destructive pattern detection</h3>
    <p><code>rm -rf /</code>, <code>DROP TABLE</code>, fork bombs, pipe-to-shell, cloud metadata endpoints. Extensible.</p>
  </div>
  <div class="card">
    <h3>5. Sequence contracts</h3>
    <p>Some tool sequences have implicit ordering. <code>delete_file</code> must follow <code>read_file</code>. Enforced.</p>
  </div>
  <div class="card">
    <h3>6. Ed25519 signature verification</h3>
    <p>Every registered tool has a cryptographic signature. Verification catches unauthorized tool registration.</p>
  </div>
  <div class="card">
    <h3>7. Adaptive threat rules</h3>
    <p>Operator-defined rules hot-reloaded every 10 seconds. Novel patterns go live without redeploying.</p>
  </div>
</div>

## Why a separate sidecar

Three reasons Guardian is a separate process rather than a Python library imported into the framework:

- **Crash isolation.** A bug in Guardian shouldn't take down the agent.
- **Framework independence.** Designed to drop into any agent framework via HTTP — LangChain, LangGraph, AutoGen, CrewAI, custom. Guardian doesn't care which.
- **Hot-reloadable rules.** New rules in `threat_rules` table go live within 10 seconds without restarting any agent process.

## Drop-in usage

```python
import httpx

GUARDIAN_URL = "http://localhost:9766"

async def guarded_tool_call(tool_name, args, task_context):
    response = await httpx.AsyncClient().post(
        f"{GUARDIAN_URL}/check",
        json={
            "tool_name": tool_name,
            "task_id": task_context.task_id,
            "user_id": task_context.user_id,
            "capability_scope": task_context.scope,
            "args": args,
            "code_hash": get_tool_hash(tool_name),
        },
    )
    decision = response.json()
    if not decision["allow"]:
        raise PermissionError(decision["reason"])
    return await actually_call_tool(tool_name, args)
```

That's the entire integration. Plug Guardian into any framework the same way.

## Status

<div class="stats">
  <div class="stat">
    <span class="stat-value">v0.1.0</span>
    <span class="stat-label">on PyPI</span>
  </div>
  <div class="stat">
    <span class="stat-value">MIT</span>
    <span class="stat-label">License (vs. AGPL framework)</span>
  </div>
  <div class="stat">
    <span class="stat-value">3-5ms</span>
    <span class="stat-label">Per-check latency</span>
  </div>
  <div class="stat">
    <span class="stat-value">9766</span>
    <span class="stat-label">Default port</span>
  </div>
</div>

## Install

```bash
pip install legionforge-guardian
```

Or pull the Docker image:

```bash
docker pull legionforge-guardian:latest
```

Full deployment walkthrough in the [Guardian docs](https://docs.legionforge.org/guardian/deployment/).

## Read more

- [Architecture](https://docs.legionforge.org/guardian/architecture/) — sidecar layout, request lifecycle, rule storage
- [Checks](https://docs.legionforge.org/guardian/checks/) — detail on each of the 7 checks
- [Deployment](https://docs.legionforge.org/guardian/deployment/) — docker-compose, env vars, health probes, metrics
