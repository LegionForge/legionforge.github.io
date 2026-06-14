---
layout: product
title: llm-valet
tagline: Cross-platform LLM lifecycle manager
subtagline: auto-pause/resume Ollama based on system pressure and gaming detection
description: >-
  llm-valet pauses and resumes Ollama based on memory pressure, GPU pressure,
  and recognized game processes. Cross-platform — macOS, Linux, Windows.
permalink: /llm-valet/
category: tool
product_id: llm-valet
repo: llm-valet
---

## What it is

Running a local LLM is expensive in RAM. A 7B-parameter model in 4-bit quantization is ~4.5 GB; an 8B at q4 is ~5.5 GB. On a 16 GB machine, keeping Ollama warm means you have ~10 GB for everything else — and the moment the system swaps, the LLM gets evicted unpredictably and re-loads on the next request (~30 s wait).

llm-valet sits in the middle. It watches:

- **Memory pressure** — if the system is paging or close to it, pause Ollama models cleanly.
- **GPU pressure** — if another GPU-hungry process spins up (a game, a render), pause the model.
- **Gaming detection** — recognized game processes are a strong signal that the user wants their hardware back.

When the pressure subsides, llm-valet warms the model back up automatically.

## When to use it

- You run Ollama locally and use the same machine for other workloads.
- You don't want LLM memory pressure to thrash the rest of your system.
- You want the model to come back automatically when there's room — not on the next slow request.

## When not to use it

- Dedicated inference box (no other workloads). Just let Ollama hold memory.
- Cloud-only LLM use. There's nothing to pause.

## Status

Active. Public. Cross-platform (macOS, Linux, Windows) but tested most heavily on Apple Silicon.

See the [GitHub repo](https://github.com/LegionForge/llm-valet) for installation and the latest release.
