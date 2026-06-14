---
layout: product
title: mcp-probe
tagline: Connectivity and configuration advisor for your MCP services
subtagline: configures, connects, diagnoses, recommends — no scanning of unauthorized targets
description: >-
  mcp-probe configures, connects to, diagnoses, and recommends settings for
  Model Context Protocol servers you own or operate. Explicitly not a scanner.
permalink: /mcp-probe/
category: tool
product_id: mcp-probe
repo: mcp-probe
---

## What it is

mcp-probe configures, connects to, diagnoses, and recommends settings for [Model Context Protocol](https://modelcontextprotocol.io) servers that **you own or operate**.

It is explicitly **not** a scanner. It does not enumerate, probe, or characterize MCP services on infrastructure you don't control.

## Use cases

- Setting up a new MCP server and verifying it's reachable, responsive, and properly configured.
- Debugging an MCP integration that an agent framework is using.
- Getting a recommendation for which MCP capabilities to enable for a given workload.

## Why this scope (and not scanning)

Tools that scan third-party MCP services would be useful for security researchers but they're also useful for attackers. The LegionForge org's policy is to ship tools that improve *your* infrastructure, not tools that profile *others'*. mcp-probe is deliberately limited to targets you can prove ownership of.

## Quick use

```bash
pip install mcp-probe
mcp-probe configure --server http://localhost:3000
mcp-probe diagnose
mcp-probe recommend --workload "code-review-agent"
```

## Integration with LegionForge

The LegionForge framework can act as both an MCP client and server. mcp-probe is useful when:

- Setting up the framework's MCP server endpoints and verifying clients can reach them
- Adding a new MCP server as a context source for the framework's agents
- Diagnosing connectivity when a registered MCP source stops responding

## Status

Active. Public. See the [GitHub repo](https://github.com/LegionForge/mcp-probe) for the full command reference.
