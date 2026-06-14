---
layout: product
title: hermes-tool-test-suite
tagline: pytest harness for AI agent tool-calling reliability
subtagline: certify that a model + prompt-config combination actually executes tools end-to-end
description: >-
  pytest harness that validates AI agent tool-calling reliability across providers.
  Used to certify that a model + prompt-config combination actually executes
  tool calls end-to-end, not just generates text that looks like one.
permalink: /hermes-tool-test-suite/
category: tool
product_id: hermes-tool-test-suite
repo: hermes-tool-test-suite
---

## What it is

A pytest harness that validates AI agent tool-calling reliability across providers. It's used to certify that a given model + prompt-config combination actually **executes** tool calls end-to-end, not just generates text that looks like a tool call.

The default validation set covers 10 scenarios across:

| Category | Scenarios |
|---|---|
| Terminal | shell exec, cwd handling |
| File ops | read, write, edit, list |
| Code execution | inline Python, subprocess Python |
| Web tools | fetch, search |

Each scenario has a deterministic expected output. The model's tool-call sequence is run and the resulting state (filesystem, stdout, etc.) is compared.

## Why this exists

A model that generates a `tool_calls` block in its API response hasn't actually proven it can drive tools. Real failures observed in practice:

- Model generates `tool_calls` but the framework's tool dispatcher trips on a tool name that's been mangled (e.g., underscore stripping)
- Model returns text describing a tool call instead of using the structured `tool_calls` field
- Model loops on the same call without integrating the result

A test harness that runs the entire loop catches all three.

## Use cases

- **Pre-deployment certification** — before shipping a new model to production, run the suite. If 9/10 pass, you know what the failure mode is and whether it's blocking.
- **Model comparison** — A/B testing tool-call reliability between providers (Ollama llama3.1 vs qwen2.5 vs cloud Claude vs OpenAI).
- **Regression detection** — after upgrading a framework version, re-run the suite to confirm no regression.

## Status

Active. Public. See the [GitHub repo](https://github.com/LegionForge/hermes-tool-test-suite) for installation and the test catalog.
