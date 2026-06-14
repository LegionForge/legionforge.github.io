---
layout: product
title: ADHD-OS
tagline: Personal assistant framework for those with ADHD
subtagline: scaffolding for the cognitive gaps, not yet another todo list
description: >-
  ADHD-OS is a personal assistant framework designed around ADHD-specific
  cognitive patterns — time blindness, working memory gaps, task switching cost,
  hyperfocus/distraction cycles.
permalink: /adhd-os/
category: app
product_id: adhd-os
repo: ADHD-OS
---

## What it is

ADHD-OS is a personal assistant framework designed around the **specific cognitive patterns of ADHD**: time blindness, working-memory gaps, task switching cost, hyperfocus / distraction cycles, and the difficulty of capturing-then-acting on intentions that aren't pinned down in the moment.

It's not a productivity app that adds another todo list. It's scaffolding for the cognitive gaps — friction-light capture, surfacing of *the right thing right now*, and graceful handling of plans that change.

## Design opinions

- **Friction-light capture wins.** If recording an intention requires more than a sentence, it doesn't happen. The system accepts unstructured input and structures it later.
- **Time pressure is a feature, not a bug.** Surfaces concrete deadlines and uses them as anchor points.
- **Forgive context loss.** Designed for sessions that get interrupted mid-thought. State persists; resumption is cheap.
- **No shame loops.** The system doesn't moralize about missed tasks. It re-plans.

## When to use it

The project is opinionated and personal-fit matters. The right way to evaluate is to clone the repo, read the design docs, and decide whether the assumptions match your patterns.

## Integration with LegionForge

ADHD-OS runs on the LegionForge framework. The personal-fit nature means it generally runs locally with local LLMs — exactly what the framework is built for. [Jeli](/jeli/) is the persistence layer for memory and decisions.

## Status

Active. Public. See the [GitHub repo](https://github.com/LegionForge/ADHD-OS) for the latest.
