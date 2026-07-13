---
title: Design
type: docs
weight: 2
prev: docs/process/discovery
next: docs/process/devops
---

## TL;DR

Before any code, a rough sketch of the solution is shaped into a pitch with a fixed appetite, a list of rabbit holes, and a list of no-gos. The pitch is the contract the team builds against.

## What this is

Design is the loop that fits the solution to the people using it and the team building it. The output is small, sharp, and ready to build — not polished mockups.

The framing comes from two sources. The [UK Design Council's Double Diamond](https://www.designcouncil.org.uk/our-resources/the-double-diamond/) models the second diamond as a diverge-converge: develop different answers, then deliver what works. [Shape Up](https://basecamp.com/shapeup) by Ryan Singer tightens that loop: shape the work into a pitch with fixed time and variable scope, bet on it, then build.

I take the convergent half of the Double Diamond ("Develop" + "Deliver") and use Shape Up's shaping discipline to make it cheap to run on a solo engagement.

## What happens

- **Set the appetite first.** Time, not estimate. "Six weeks" or "two weeks" — not "should take four weeks if everything goes well." Fixed time forces trade-offs.
- **Find the elements, not the screens.** Fat marker sketches and breadboards — UI concepts that define affordances and their connections without visual styling. Words are too abstract, wireframes are too concrete, sketches land in the middle.
- **Surface the rabbit holes.** Parts of the project that are too unknown or too complex to bet on. Either spike them, declare them out of bounds, or cut back.
- **Write the pitch.** A one-pager with five ingredients: Problem, Appetite, Solution (with sketches), Rabbit Holes, No-Gos. The No-Gos list is what makes the pitch a real contract.
- **Get one piece done before the rest.** In Shape Up terms: integrate one slice end-to-end before chasing the next one. The point is to find the unblockable unknowns early, not to build the whole UI.

## What you get

- A pitch document the team can argue about in plain language, before any code is written.
- A small batch of fat marker sketches and breadboards — low-fidelity artifacts that make disagreement cheap.
- A list of rabbit holes with a plan for each: spike, bound, or cut.
- A clear definition of done that includes "deployed" — not "coded and demoed".

## Cadence

- **First two weeks: most of the design happens before any code, to give delivery a clear runway.** Shape Up's six-week cycle compresses to two or three weeks on a solo engagement, with the same internal rhythm: shape, bet, build.
- **Steady state: 1–3 hour slices two or three times a week.** Most weeks, the design loop returns for a single feature between builds.
- **Anything bigger than a half-day of design work breaks into smaller questions first.** If the pitch can't fit on a page, the appetite is wrong.

## What I need from you

- One person on your team to react to sketches the same day — fast, blunt feedback is the point.
- Permission to use whatever tool the team already lives in, even if it is messy.
- A short answer to "what would make this version obviously worth shipping?" before each new design slice.

## What comes next

A sharp design hands off to [DevOps](/docs/process/devops/). Design does not stop — it returns for the next slice as soon as the current one has shipped behind a flag.