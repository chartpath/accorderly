---
title: Triple Diamond SDLC
type: docs
weight: 1
sidebar:
  open: true
---

## TL;DR

Three continuous activities — Discovery, Design, DevOps — run in parallel. The model is a synthesis of other people's published work; I added the third diamond (DevOps), for the shift-left reason below.

## What it is, and what it isn't

The Triple Diamond is a delivery model, not a methodology. Each diamond is a small, repeating loop: **diverge → converge → ship**. The three loops run at different speeds but never stop, which is why they overlap instead of handing off.

{{< acc-figure
  src="marketing/method/triple-diamond.webp"
  alt="The triple diamond: three diverge then converge beats covering Discovery, Design, and DevOps."
  width="1400"
  height="445"
  caption="The triple diamond: three diverge-converge beats. Each diamond widens the option space, then narrows to a decision. The three run in parallel, not as phases."
>}}

Hand-offs lose context. Discoveries that happen after a decision is locked hurt. Shipping pieces nobody asked for wastes the team's time. Keeping all three alive at once shortens the gap between "we learned something" and "the user can see the change".

It is called "triple diamond" because it is a synthesis of three models that each only describe one diamond:

- **Discovery** — [Teresa Torres' *Continuous Discovery Habits*](https://www.producttalk.org/opportunity-solution-trees/) and the [Opportunity Solution Tree](https://www.producttalk.org/opportunity-solution-trees/) (OST)
- **Design** — the [UK Design Council's Double Diamond](https://www.designcouncil.org.uk/our-resources/the-double-diamond/) (Discover / Define / Develop / Deliver) and [Shape Up](https://basecamp.com/shapeup) by Ryan Singer
- **DevOps** — [The DevOps Handbook](https://itrevolution.com/the-devops-handbook/) (Kim, Humble, Debois, Willis, Forsgren) and The Three Ways

Each of those sources is for larger teams. The triple-diamond reframing keeps the same habits but compresses them onto one person — me — which is what a solo engagement can afford.

## Why triple, and not double

The Double Diamond ends at delivery — the second diamond converges on what gets built. The moment something ships, the question "does it actually work for the people we said it would work for?" starts. That is its own loop, and it is where DevOps earns its keep. Adding a third diamond for build / ship / observe is the smallest change that keeps the answer honest without inventing a new model.

The reason for keeping it a parallel loop rather than a serial phase is the [shift-left idea](https://en.wikipedia.org/wiki/Shift-left_testing) (Larry Smith, 2001): do the things at the end of the timeline earlier, in parallel with what comes before. Shift-left testing means tests run with every commit, not at release. Shift-left delivery — the third diamond — means the build, ship, and observe loop runs alongside Discovery and Design from day one, not after the design is "done".

The TL;DR of shift-left, applied here: build the production feedback loop before you have any production, not after.

{{< cards >}}
  {{< card link="discovery" title="Discovery" icon="search" subtitle="Continuous customer interviews, an Opportunity Solution Tree, and one working hypothesis a week." >}}
  {{< card link="design" title="Design" icon="pencil-alt" subtitle="Shape a rough, solved, bounded pitch that fits the appetite before any code is written." >}}
  {{< card link="devops" title="DevOps" icon="cog" subtitle="Build, ship, observe — a tight loop on CI/CD, telemetry, and small changes behind flags." >}}
{{< /cards >}}

## What a week looks like

- A discovery conversation on Tuesday surfaces a new opportunity in the OST.
- That opportunity becomes a shaped pitch by Thursday.
- A small build ships behind a flag by next Tuesday.
- Real usage either confirms the opportunity or replaces it before the flag flips.

No big reveal. No phase-gate. Each loop ends every week. Some weeks the loops produce nothing worth shipping; those weeks are still useful because they confirm what's not the answer.

## How engagements start

A first conversation is short. We talk through what you need, what's blocking you, and what's already been tried. From there: a clear scope, a polite no, or a referral to someone better suited.

{{< hextra/hero-button text="Book a call →" link="https://cal.eu/accorderly" >}}