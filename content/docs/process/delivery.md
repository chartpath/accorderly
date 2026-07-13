---
title: Delivery
type: docs
prev: docs/process/design
---

## TL;DR

Delivery is the loop that ships small, often, and behind flags. The goal is learning from real usage, not finishing a plan.

## What it is

Delivery is build, ship, observe, repeat. The smallest loop is one branch, one review, one deploy, one observation. The fastest loops win. The team commits to a weekly shipping cadence in public, and the calendar holds them to it.

The reason delivery stays inside the other two loops is to keep the cost of being wrong low. Behind a flag, a wrong decision costs a comment thread. Without a flag, the same decision costs a rollback at 2am.

## What happens

- One short-lived branch per slice, reviewed inside one business day
- Flags for anything user-visible, auto-cleaned after a release settles
- A shipped slice is observed inside a week — analytics, a user conversation, or a short note in the next weekly write-up
- Real usage either confirms the next slice belongs in the same direction, or replaces it before the next branch opens

## What you get

- A deployable artifact at the end of every working week
- A short retro note: what shipped, what it cost, what we learned
- A backlog that stays small on purpose — anything stale for two weeks gets cut, not carried

## Cadence

- One shipping event per week, with a hard cap on Friday afternoon
- Two short planning conversations: one on Monday morning, one mid-week
- A 30-minute retro at the end of every week

## What I need from you

- A working deploy pipeline on day one, even if the deploy target is a single server
- A reviewer who can turn a pull request around in a day — slow reviews are the most common cause of stuck delivery
- Agreement that "shipped behind a flag" counts as shipped — the goal is feedback, not a public launch event

## Where this loops back

Every shipped slice becomes the next input for [Discovery](/docs/process/discovery/). Real usage is the cheapest source of new hypothesis the team will ever have, and the only way to keep that source open is to keep shipping.
