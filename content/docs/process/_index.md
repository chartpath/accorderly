---
title: Triple Diamond SDLC
type: docs
---

## TL;DR

Three continuous activities — Discovery, Design, DevOps — run in parallel. The result is software that fits the user, the team, and the budget, shipped in small pieces from day one.

## What it is

The Triple Diamond is a delivery model, not a project plan. Each diamond is a small, repeating loop: **diverge → converge → ship**. The three loops run at different speeds but never stop, which is why they overlap instead of handing off.

The point of running them together is simple. Hand-offs lose context. Discoveries that happen after a decision is locked hurt. Ship pieces that nobody has asked for waste the team's time. Keeping all three alive at once shortens the gap between "we learned something" and "the user can see the change".

It is called "triple diamond" because it is a synthesis of three models that each only describe one diamond:

- **Discovery** — drawn from [Teresa Torres' *Continuous Discovery Habits*](https://www.producttalk.org/opportunity-solution-trees/) and the [Opportunity Solution Tree](https://www.producttalk.org/opportunity-solution-trees/) (OST)
- **Design** — drawn from the [UK Design Council's Double Diamond](https://www.designcouncil.org.uk/our-resources/the-double-diamond/) (Discover / Define / Develop / Deliver) and [Shape Up](https://basecamp.com/shapeup) by Ryan Singer
- **DevOps** — drawn from [The DevOps Handbook](https://itrevolution.com/the-devops-handbook/) (Kim, Humble, Debois, Willis, Forsgren) and The Three Ways

Each of those sources is for larger teams. The triple-diamond reframing keeps the same habits but compresses them onto one person — me, Chris Hart — which is what a solo engagement can afford. I run all three loops myself rather than splitting them across roles.

## Why "triple" rather than "double"

The Double Diamond ends at delivery — the second diamond converges on what gets built. In practice, the moment something is shipped, the question "does it actually work for the people we said it would work for?" starts. That is its own loop, and it is where DevOps earns its keep. Adding a third diamond for build / ship / observe is the smallest change that keeps the answer honest without inventing a new model.

The reason for keeping it a parallel loop rather than a serial phase is the [shift-left](https://en.wikipedia.org/wiki/Shift-left_testing) idea (Larry Smith, 2001): do the things that traditionally live at the end of the timeline earlier, in parallel with the things that come before. Shift-left testing means tests run with every commit, not at release. Shift-left delivery — the third diamond — means the build, ship, and observe loop runs alongside Discovery and Design from day one, not after the design is "done".

{{< cards >}}
  {{< card link="discovery" title="Discovery" icon="search" subtitle="Continuous customer interviews, an Opportunity Solution Tree, and one working hypothesis a week." >}}
  {{< card link="design" title="Design" icon="pencil-alt" subtitle="Shape a rough, solved, bounded pitch that fits the appetite before any code is written." >}}
  {{< card link="devops" title="DevOps" icon="cog" subtitle="Build, ship, observe — a tight loop on CI/CD, telemetry, and small changes behind flags." >}}
{{< /cards >}}

## What continuous looks like in practice

- A discovery conversation on Tuesday surfaces a new opportunity in the OST
- That opportunity becomes a shaped pitch by Thursday
- A small build ships behind a flag by next Tuesday
- Real usage either confirms the opportunity or replaces it before the flag flips

No big reveal. No phase-gate. Each loop ends every week.

## How engagements start

A first conversation is short. We talk through what you need, what's blocking you, and what's already been tried. From there, one of three things happens next: a clear scope, a polite no, or a referral to someone better suited.