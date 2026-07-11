---
layout: product
title: ConvoBox
tagline: Local, backend-agnostic voice frontend for CLI coding agents
subtagline: full-duplex voice control for Codex, Claude Code, OpenCode, and other agent CLIs
description: >-
  ConvoBox is a local-first voice frontend for CLI coding agents. It provides
  continuous listening, local speech-to-text and text-to-speech, deterministic
  hard-stop handling, and backend adapters for coding-agent tools.
permalink: /convobox/
category: app
product_id: convobox
repo: convobox
---

## What it is

ConvoBox sits between you and whichever coding-agent CLI you are driving and lets you work by voice instead of, or alongside, the keyboard. The goal is a portable voice layer that can point at Codex, Claude Code, OpenCode, or another backend without being tied to one product.

It is local-first by default: speech-to-text and text-to-speech run on hardware you control, with a thin adapter layer translating spoken intent into each backend's native control surface.

## Design goals

<div class="card-grid">
  <div class="card">
    <h3>Full-duplex conversation</h3>
    <p>Continuous listening with voice-activity detection, barge-in, and spoken responses instead of push-to-talk dictation.</p>
  </div>
  <div class="card">
    <h3>Backend-agnostic adapters</h3>
    <p>A small adapter surface maps text, interject, hard-stop, and busy-state operations onto each coding agent.</p>
  </div>
  <div class="card">
    <h3>Local-first audio</h3>
    <p>VAD, STT, and TTS are designed to run on-device or on private-network hardware under your control.</p>
  </div>
  <div class="card">
    <h3>Deterministic hard stops</h3>
    <p>Safeword handling stays out of the model path so an abort command cannot be second-guessed by an LLM.</p>
  </div>
</div>

## Architecture

```text
mic -> VAD -> local STT -> safeword check -> orchestrator -> backend adapter
                                                           -> local TTS
```

The orchestrator decides whether each utterance is a new command, a soft interjection into an active task, or a hard stop. Backend adapters prefer structured/headless interfaces where available and fall back to terminal control only when necessary.

## Status

Scaffolding stage. The repository has initial implementations for audio capture/playback, VAD segmentation, local STT, safeword detection, TTS, orchestration, and an OpenCode adapter. Claude Code and Codex adapters are not stable yet.

See the [GitHub repo](https://github.com/LegionForge/convobox) for current implementation notes and testing status.
