---
layout: default
title: ~
description: >-
  Sovereign AI primitives — built local-first, security-native, owned by you.
  Open-source software that gives you AI without giving up your sovereignty.
permalink: /
---

<section class="hero">
  <div class="hero-inner">
    <div class="badge">v0.7.1-alpha · 2247 smoke tests</div>
    <h1>Sovereign AI <span>primitives</span></h1>
    <p class="tagline">Built local-first, security-native, owned by you.</p>
    <p class="subtagline">software that gives you AI without giving up your sovereignty</p>
    <div class="cta-group">
      <a class="btn btn-primary" href="/framework/">Explore the framework →</a>
      <a class="btn btn-secondary" href="https://docs.legionforge.org/">Read the docs</a>
    </div>
  </div>
</section>

<section id="why">
  <div class="container container-narrow">
    <p class="section-eyebrow">Why this exists</p>
    <h2 class="section-title">Built in the opposite order</h2>
    <p>
      In January 2026, OpenClaw hit 60,000 GitHub stars in 72 hours and 300,000+ users in
      weeks. Kaspersky found 512 vulnerabilities (8 critical). Cisco found active data
      exfiltration in third-party skills.
    </p>
    <p>
      LegionForge is built in the opposite order: <strong>security first, product on top</strong>.
      Every component lives on your hardware, under your keys. Validation runs in deterministic
      code, not in the model. The LLM is the last resort, not the first.
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
