---
layout: product
title: ConvoBox
tagline: Local, backend-agnostic voice frontend for CLI coding agents
subtagline: full-duplex voice control for Codex, Claude Code, OpenCode, and other agent CLIs, with barge-in, tool approval, and a local web UI
description: >-
  ConvoBox is a local-first voice frontend for CLI coding agents. It provides
  continuous listening, local speech-to-text and text-to-speech, deterministic
  hard-stop handling, voice-gated tool approval, and backend adapters for
  coding-agent tools — all three backends live-verified end to end on Windows.
permalink: /convobox/
category: app
product_id: convobox
repo: convobox
---

## What it is

ConvoBox sits between you and whichever coding-agent CLI you are driving — Claude Code, Codex, OpenCode, and eventually others — and lets you work by voice instead of, or alongside, the keyboard. It's a developer tool, not a general-purpose voice assistant: without an already-running coding-agent CLI, it has nothing to talk to.

It is local-first by default: speech-to-text and text-to-speech run on hardware you control, with a thin adapter layer translating spoken intent into each backend's native control surface — preferring structured/headless interfaces over scraping terminal output wherever a backend offers one.

## What it does

<div class="card-grid">
  <div class="card">
    <h3>Full-duplex conversation</h3>
    <p>Continuous listening with voice-activity detection and spoken responses, not push-to-talk. Barge-in is a two-axis preset system — what happens to the current turn is independent of what happens to your new words.</p>
  </div>
  <div class="card">
    <h3>Backend-agnostic adapters</h3>
    <p>A small adapter surface — send text, interject, hard-stop, report busy state — maps onto whichever coding agent you're driving, verified live against real OpenCode, Claude Code, and Codex instances.</p>
  </div>
  <div class="card">
    <h3>Voice-gated tool approval</h3>
    <p>A spoken phrase gates pending destructive tool calls on Codex and Claude Code — approve, deny, or ask for a plain-language explanation before deciding.</p>
  </div>
  <div class="card">
    <h3>Deterministic hard stops</h3>
    <p>Safeword handling stays outside the model path so an abort command cannot be second-guessed or reinterpreted by an LLM.</p>
  </div>
  <div class="card">
    <h3>Local-first audio</h3>
    <p>VAD, STT (faster-whisper), and TTS (Kokoro, Apache-2.0) run on hardware you control. Acoustic echo cancellation keeps the assistant's own voice from tripping its own barge-in detection.</p>
  </div>
  <div class="card">
    <h3>An optional local web UI</h3>
    <p>A browser view of a live session — transcript, tool calls, pending approvals — streamed over Server-Sent Events, with optional local SQLite history. No authentication; loopback-only by design.</p>
  </div>
</div>

## Architecture

```text
mic -> VAD -> local STT -> safeword check -> orchestrator -> backend adapter
                                                           -> local TTS
```

The orchestrator decides whether each utterance is a new command, a soft interjection into an active task, or a hard stop. Backend adapters prefer structured/headless interfaces where available and fall back to terminal control only when necessary.

## Status

All three backend adapters — OpenCode (HTTP+SSE), Claude Code (stream-json subprocess), and Codex (app-server JSON-RPC) — have been driven through the full live voice loop, including real tool use, on Windows 11. Linux/macOS are implemented but not yet voice-validated end to end.

Beyond the core pipeline, a substantial interaction/safety layer has since landed: barge-in presets, a live conversation TUI, response tiering, voice-gated tool approval, acoustic echo cancellation, and the local web UI described above. This is a working, extensively tested prototype under active live-testing iteration — not yet a packaged, stable end-user release.

## Known limits

- Linux and macOS run the same adapters/pipeline as Windows but haven't been voice-validated end to end there yet.
- Browser-side approve/deny for the web UI isn't built — voice and the TUI remain the only channels for that decision.
- No remote-access or authentication story for the web UI, by design — it's meant for the same machine only.

See the [GitHub repo](https://github.com/LegionForge/convobox) for current implementation notes and testing status.
