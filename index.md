---
layout: default
title: ~
description: >-
  Sovereign AI for Everyone — built local-first, security-native, owned by you.
  Your memory, your agents, your rules.
permalink: /
---

<section class="hero">
  <div class="hero-inner">
    <img class="hero-logo" src="/assets/img/legionforge-logo.svg" alt="LegionForge" width="96" height="96">
    <h1>Sovereign AI for <span>Everyone!</span></h1>
    <p class="tagline">Built local-first, security-native, owned by you.</p>
    <p class="subtagline">Your memory, your agents, your rules.</p>
    <div class="cta-group">
      <a class="btn btn-primary" href="/framework/">Explore the framework →</a>
      <a class="btn btn-secondary" href="https://docs.legionforge.org/">Read the docs</a>
    </div>
  </div>
</section>

<section id="why">
  <div class="container container-narrow">
    <p class="section-eyebrow">Why this exists</p>
    <h2 class="section-title">Sovereign memory for local-first AI</h2>
    <p>
      AI assistants are becoming memory systems: places where we ask questions, store
      context, make decisions, and build up a working model of who we are. That memory
      should not be trapped inside a vendor account or disappear when a subscription ends.
    </p>
    <p>
      LegionForge is built around a simpler premise: <strong>your memory belongs to you</strong>.
      You should control what gets inserted, updated, deduplicated, enhanced, forgotten, or
      resolved when facts conflict. You should be able to inspect and move your data, tune
      your agents, and decide which tools can touch which parts of your identity.
    </p>
    <p>
      LegionForge provides a user-first, security-conscious, open-source path for local AI:
      owned by you, running under your rules, with deterministic validation where it matters
      and LLMs used where they actually help.
    </p>
  </div>
</section>

<section id="principles">
  <div class="container">
    <p class="section-eyebrow">Five non-negotiables</p>
    <h2 class="section-title">Design principles</h2>
    <div class="principles">
      <div class="principle">
        <h3>Sovereignty first</h3>
        <p>Your memory, agents, rules, and data stay under your control. Inspect, tune, update, move, or forget any part of the system.</p>
      </div>
      <div class="principle">
        <h3>Local-first custody</h3>
        <p>Core state lives on infrastructure you control. Cloud services are optional dependencies, not the source of truth.</p>
      </div>
      <div class="principle">
        <h3>Human authority</h3>
        <p>Irreversible changes, sensitive writes, and memory conflicts cross a human-controlled boundary by default.</p>
      </div>
      <div class="principle">
        <h3>Deterministic guardrails</h3>
        <p>Rules, signatures, trust scores, and capability checks run before the model gets a vote.</p>
      </div>
      <div class="principle">
        <h3>Right to exit</h3>
        <p>Your memories and audit trails should be portable. Leaving a vendor should not mean losing yourself.</p>
      </div>
    </div>
  </div>
</section>

<section id="products">
  <div class="container">
    <p class="section-eyebrow">The ecosystem</p>
    <h2 class="section-title">Build with what fits</h2>
    <p style="color: var(--dim); margin: -1rem 0 2rem; font-size: 0.95rem;">
      LegionForge is a family of independent, composable projects for sovereign AI:
      memory governance, local agents, voice interfaces, orchestration, diagnostics,
      and security tooling. Use one piece, or wire the stack end-to-end.
    </p>

    <div class="product-grid">
      {% for product in site.products %}
        <a class="product-card" href="/{{ product.id }}/">
          <span class="product-cat">{{ product.category }}</span>
          <h3>{{ product.name }}</h3>
          <p>{{ product.tagline }}</p>
        </a>
      {% endfor %}
    </div>
  </div>
</section>

<section id="security">
  <div class="container container-narrow">
    <p class="section-eyebrow">Security posture</p>
    <h2 class="section-title">Security in service of ownership</h2>
    <p>
      Security is not only about blocking bad tool calls. It is about making sure your
      memory, identity, and agent history remain inspectable, portable, and governed by you.
    </p>
    <p>
      LegionForge favors deterministic checks, scoped capabilities, signed provenance,
      and human-controlled mutation points. The model can help reason, but it should not
      be the authority deciding what your system is allowed to remember or do.
    </p>
    <p>
      <a href="/security/" class="btn btn-secondary">How LegionForge handles security →</a>
    </p>
  </div>
</section>

<section id="cta-bottom">
  <div class="container container-narrow" style="text-align: center;">
    <h2 class="section-title" style="justify-content: center;">Ready to dig in?</h2>
    <div class="cta-group">
      <a class="btn btn-primary" href="https://docs.legionforge.org/">Read the docs</a>
      <a class="btn btn-secondary" href="https://github.com/LegionForge">GitHub organization</a>
    </div>
  </div>
</section>
