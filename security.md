---
layout: default
title: Security
description: >-
  LegionForge's security posture, philosophy, and differentiators. What we
  defend against, what we don't, and how to disclose vulnerabilities.
permalink: /security/
---

<section class="hero">
  <div class="hero-inner">
    <div class="badge">SECURITY POSTURE</div>
    <h1>Security is the <span>foundation</span></h1>
    <p class="tagline">Not a feature. Not a layer. The constraint every other decision is shaped around.</p>
  </div>
</section>

<section>
  <div class="container container-narrow">
    <p class="section-eyebrow">Philosophy</p>
    <h2 class="section-title">The thesis</h2>
    <p>
      The LLM is not trustworthy. Everything that crosses a trust boundary is validated by
      deterministic code before the LLM ever sees it, and everything the LLM produces is
      validated again before it has any effect on the outside world.
    </p>
    <p>
      The reflex when designing a security layer in 2026 is to put an LLM in it — "have the
      model judge whether this call is safe." That's wrong. LLM-based checks can be
      prompt-injected by the very payloads they're inspecting, they're slow, and they're
      expensive. LegionForge sticks to regex, hash compare, signature verify, and capability
      lookups. They're crude. They're also predictable and auditable.
    </p>
  </div>
</section>

<section>
  <div class="container">
    <p class="section-eyebrow">Five non-negotiables</p>
    <h2 class="section-title">Principles that shape every component</h2>
    <div class="principles">
      <div class="principle">
        <h3>Fail-safe tiering</h3>
        <p>Halt → sandbox/retry → degrade. Never silently succeed. Errors propagate with intent.</p>
      </div>
      <div class="principle">
        <h3>Human gates on mutations</h3>
        <p>Destructive actions cross a human-in-the-loop boundary by default.</p>
      </div>
      <div class="principle">
        <h3>Replace AI with determinism</h3>
        <p>The LLM is the last resort, not the first. Rules, tables, and pattern matchers run ahead.</p>
      </div>
      <div class="principle">
        <h3>Validate at trust boundaries</h3>
        <p>Sanitize once, at the edge. Internal code trusts internal data. Validate at the edges, not at every node.</p>
      </div>
      <div class="principle">
        <h3>Privilege tied to tasks</h3>
        <p>Capability is scoped to the active task and expires when the task ends. No persistent agent privilege.</p>
      </div>
    </div>
  </div>
</section>

<section>
  <div class="container">
    <p class="section-eyebrow">Differentiators</p>
    <h2 class="section-title">How LegionForge differs from the others</h2>

    <table>
      <thead>
        <tr>
          <th></th>
          <th>LegionForge</th>
          <th>Cloud agent platforms<br><small style="color: var(--dim); font-weight: 400;">(OpenAI Operator, Anthropic Computer Use, Google Mariner)</small></th>
          <th>OSS agent frameworks<br><small style="color: var(--dim); font-weight: 400;">(LangChain, AutoGen, CrewAI)</small></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><strong>Where it runs</strong></td>
          <td>Your hardware</td>
          <td>Their hardware</td>
          <td>Your hardware</td>
        </tr>
        <tr>
          <td><strong>Where your data sits</strong></td>
          <td>Your PostgreSQL</td>
          <td>Their database (opaque)</td>
          <td>Wherever you wire it</td>
        </tr>
        <tr>
          <td><strong>Tool-call security</strong></td>
          <td>7-check deterministic pipeline on every call (enforced)</td>
          <td>Their internal checks (you don't see them)</td>
          <td>Whatever you wire (often nothing)</td>
        </tr>
        <tr>
          <td><strong>Prompt-injection detection</strong></td>
          <td>29 patterns, two tiers, at trust boundary</td>
          <td>Vendor-defined</td>
          <td>Not bundled</td>
        </tr>
        <tr>
          <td><strong>Audit trail</strong></td>
          <td>SHA-256 hash-chained <code>audit_log</code></td>
          <td>Their logs (you don't get them)</td>
          <td>Not bundled</td>
        </tr>
        <tr>
          <td><strong>HITL on destructive actions</strong></td>
          <td>Enforced via approval gate</td>
          <td>Sometimes</td>
          <td>You wire it</td>
        </tr>
        <tr>
          <td><strong>Tool signing</strong></td>
          <td>Ed25519 on every registered tool</td>
          <td>Internal</td>
          <td>Not bundled</td>
        </tr>
        <tr>
          <td><strong>License</strong></td>
          <td>AGPL-3.0 (commercial available) · Guardian MIT</td>
          <td>Proprietary</td>
          <td>MIT / Apache 2.0</td>
        </tr>
      </tbody>
    </table>
  </div>
</section>

<section>
  <div class="container">
    <p class="section-eyebrow">What we defend against</p>
    <h2 class="section-title">Threat model</h2>
    <div class="threat-grid">
      <div class="threat-card high">
        <div class="threat-name">Prompt injection (Tier 1)</div>
        <div class="threat-def">High-confidence patterns. Match → reject immediately, log <code>INJECTION_DETECTED</code>.</div>
      </div>
      <div class="threat-card high">
        <div class="threat-name">Tool poisoning</div>
        <div class="threat-def">Live tool code hashed at invocation and compared to registered hash. Catches dependency-replacement attacks.</div>
      </div>
      <div class="threat-card high">
        <div class="threat-name">Capability creep</div>
        <div class="threat-def">Tool's required capability must be in the task's scope. Scope is set at task creation and never widens.</div>
      </div>
      <div class="threat-card medium">
        <div class="threat-name">Destructive tool arguments</div>
        <div class="threat-def">Regex pipeline catches <code>rm -rf /</code>, <code>DROP TABLE</code>, fork bombs, pipe-to-shell, metadata endpoints.</div>
      </div>
      <div class="threat-card medium">
        <div class="threat-name">Runaway behavior</div>
        <div class="threat-def">Three independent loop-protection layers: step counter, action-history hash, token budget.</div>
      </div>
      <div class="threat-card medium">
        <div class="threat-name">Tool result injection</div>
        <div class="threat-def">Tool output containing injection payloads aimed back at the model (e.g., a fetched web page).</div>
      </div>
      <div class="threat-card low">
        <div class="threat-name">PII leakage in logs</div>
        <div class="threat-def">Output sanitization strips PII before logging to LangSmith or returning to user.</div>
      </div>
      <div class="threat-card low">
        <div class="threat-name">Unauthorized destructive ops</div>
        <div class="threat-def">HITL approval gate. Destructive tool calls cross a human-in-the-loop boundary.</div>
      </div>
    </div>
  </div>
</section>

<section>
  <div class="container container-narrow">
    <p class="section-eyebrow">What we don't claim to catch</p>
    <h2 class="section-title">Honest limits</h2>
    <ul>
      <li>A malicious <em>human</em> operator with gateway credentials. Bearer auth gates entry; access control inside the gateway assumes the operator is authorized.</li>
      <li>Side-channel attacks on local LLM weights. Model integrity is checked at load, but not at every inference.</li>
      <li>Physical access to the machine.</li>
      <li>Threats specific to platforms we don't run on (we run local-first; cloud-specific threats aren't our model).</li>
    </ul>
    <p>
      Listing the limits matters as much as listing the wins. A threat model that claims to
      defend against everything is a threat model nobody has actually walked.
    </p>
  </div>
</section>

<section>
  <div class="container container-narrow">
    <p class="section-eyebrow">Reporting vulnerabilities</p>
    <h2 class="section-title">Coordinated disclosure</h2>
    <p>
      <strong>Do not open a public issue for security vulnerabilities.</strong>
      Email <a href="mailto:security@legionforge.org">security@legionforge.org</a>.
    </p>
    <p>
      We respond within 5 business days. After a fix is in place and users have had a
      chance to update, we publish a security advisory in the affected repo with the
      coordinated CVE if one was assigned.
    </p>
    <div class="cta-group" style="justify-content: flex-start;">
      <a class="btn btn-primary" href="mailto:security@legionforge.org">Disclose a vulnerability</a>
      <a class="btn btn-secondary" href="https://docs.legionforge.org/framework/security-model/">Read the security model →</a>
    </div>
  </div>
</section>
