---
title: Design
type: docs
prev: docs/process/discovery
next: docs/process/delivery
---

## TL;DR

Design is the loop that fits the solution to the people using it and the team building it. The output is small, sharp, and ready to ship — not polished mockups.

## What it is

Design here is the smallest artifact that closes a decision: a one-screen sketch, a copy edit, a flow diagram with three boxes, a written contract of behavior. Anything bigger is usually a sign that a discovery question has been skipped. The job of design is to make the next delivery decision obvious without being precious about it.

## What happens

- Sketching the smallest viable version of a flow before any code is written
- Writing the interface as text first (component names, copy, error states) so the team can disagree on the words early
- Picking the lightest tool that fits — paper, Figma, an actual code branch — whatever the team will actually read
- Specifying just enough that a backend change and a frontend change can land independently

## What you get

- A working sketch in whatever format fits the question (often a static HTML page or a screenshot in the issue)
- A short written contract of behavior: inputs, outputs, edge cases, what is intentionally out of scope
- A review-friendly artifact that a non-designer can comment on in three minutes

## Cadence

- First two weeks: most of the design happens before any code, to give delivery a clear runway
- Steady state: design work continues alongside delivery, usually in 1–3 hour slices two or three times a week
- Anything bigger than a half-day of design work breaks into smaller questions first

## What I need from you

- One person on your team to react to sketches the same day — fast, blunt feedback is the point
- Permission to use whatever tool the team already lives in, even if it is messy
- A short answer to "what would make this version obviously worth shipping?" before each new design slice

## What comes next

A sharp design hands off to [Delivery](/docs/process/delivery/). Design does not stop — it returns for the next slice as soon as the current one has shipped behind a flag.
