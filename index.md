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
        <h3>Fail-safe tiering</h3>
        <p>Halt → sandbox/retry → degrade. Never silently succeed.</p>
      </div>
      <div class="principle">
        <h3>Human gates on mutations</h3>
        <p>Destructive actions cross a human-in-the-loop boundary by default.</p>
      </div>
      <div class="principle">
        <h3>Replace AI with determinism</h3>
        <p>The LLM is the last resort. Rules, tables, and pattern matchers run ahead.</p>
      </div>
      <div class="principle">
        <h3>Validate at trust boundaries</h3>
        <p>Sanitize once, at the edge. Internal code trusts internal data.</p>
      </div>
      <div class="principle">
        <h3>Privilege tied to tasks</h3>
        <p>Capability is scoped to the active task and expires when it ends.</p>
      </div>
    </div>
  </div>
</section>

<section id="products">
  <div class="container">
    <p class="section-eyebrow">The ecosystem</p>
    <h2 class="section-title">Build with what fits</h2>
    <p style="color: var(--dim); margin: -1rem 0 2rem; font-size: 0.95rem;">
      LegionForge is a family of independent, composable projects. Adopt the framework
      end-to-end, or use Guardian standalone to harden the agent stack you already run.
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
    <h2 class="section-title">Different from cloud agent platforms — different from unguarded OSS frameworks</h2>
    <p>
      Most cloud agent platforms (OpenAI Operator, Anthropic Computer Use, Google Mariner)
      run your tasks on someone else's hardware. Your prompts, your data, your tool outputs —
      they pass through systems you can't audit.
    </p>
    <p>
      Most open-source frameworks (LangChain, AutoGen, CrewAI) are flexible substrates that
      <em>let</em> you add guardrails. LegionForge <em>enforces</em> them — in deterministic
      code, on every step, with no opt-out path.
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
