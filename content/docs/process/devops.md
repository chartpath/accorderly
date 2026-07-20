---
title: DevOps
type: docs
weight: 3
prev: docs/process/design
---

## TL;DR

A tight loop on build, ship, and observe. Every change goes through CI/CD. Every shipped slice produces telemetry. Every week ends with the numbers, not a status meeting.

## What this is

DevOps is the third diamond — the one that starts when something reaches production and answers a question the Discovery and Design loops can't: *does it actually work for the people we said it would work for, in the conditions we said it would work in?*

The framing comes from [The DevOps Handbook](https://itrevolution.com/the-devops-handbook/) by Gene Kim, Jez Humble, Patrick Debois, John Willis, and Nicole Forsgren. The book organises DevOps around **The Three Ways**:

- **The First Way — Flow.** Move work from commit to production in a predictable, automated pipeline. The goal is short lead time, not heroic effort.
- **The Second Way — Feedback.** Amplify feedback from production back into the team. Telemetry, monitoring, and incident review close the loop so the next commit is informed.
- **The Third Way — Continuous Learning.** A culture that experiments, takes risks, and converts local learning into global improvement. The reason the loop never stops is the team's job is to get better at running the loop.

This third diamond is where DORA's four metrics live: **deployment frequency, lead time for changes, change failure rate, and failed deployment recovery time.** A solo engagement has less ceremony than a large team, but the same metrics and the same feedback loop.

## Why a third diamond (shift-left)

The Double Diamond ends at delivery — the second diamond converges on what gets built. Treating delivery as a one-shot event at the end loses the answer to the only question that matters: *does it actually work for the people we said it would work for?* The way to keep that answer honest is to start the build / ship / observe loop on day one, not at the end of the project. That is the "shift left" approach: do the things later in the lifecycle earlier, in parallel with the things that come before them.

The phrase comes from Larry Smith's 2001 *Dr. Dobb's Journal* article on [shift-left testing](https://en.wikipedia.org/wiki/Shift-left_testing), where "left" means earlier on the project timeline. The same principle applied to security is the basis of DevSecOps; applied to delivery it is the basis of the DevOps diamond on this site. CI/CD, telemetry, and small changes behind flags are not a final phase — they run alongside Discovery and Design, all the time.

## What happens

- **CI/CD from day one.** Every commit goes through automated build, test, and deploy. A pull request that fails the pipeline does not get reviewed.
- **Small changes behind flags.** Anything user-visible ships behind a feature flag. The flag is the diff between "the team knows about it" and "the user sees it".
- **Telemetry on what we shipped.** Every shipped slice gets a way to observe whether the working hypothesis held up. Logs, metrics, traces, or a small user study — whatever fits the question.
- **A weekly retro on the numbers.** Not "what did we ship" but "what did we learn, and what does the next commit need to know." The retro is the bridge between DevOps and the next Discovery conversation.
- **An incident review when something breaks.** Blameless, written up, and read by the team. The point is the next incident gets faster to detect and cheaper to fix.

## What you get

- A deployable artifact at the end of every working week — "done means deployed," not "demoed on a branch".
- A short retro note: what shipped, what it cost, what we learned.
- A backlog that stays small on purpose — anything stale for two weeks gets cut, not carried.
- A measurable loop: deployment frequency, lead time, change failure rate, recovery time. The numbers are the scoreboard.

## Cadence

- **One shipping event per week**, with a hard cap on Friday afternoon.
- **Two short planning conversations**: one on Monday morning, one mid-week.
- **A 30-minute retro at the end of every week** — over the numbers, not over feelings.
- **Incident response is the exception, not the cadence.** When something breaks, the loop compresses until it is fixed; otherwise the steady-state rhythm holds.

## What I need from you

- A working deploy pipeline on day one, even if the deploy target is a single server.
- A reviewer who can turn a pull request around in a day — slow reviews are the most common cause of stuck delivery.
- Telemetry access — application logs, error reports, the things that tell us whether a working hypothesis actually worked.
- Agreement that "shipped behind a flag" counts as shipped — the goal is feedback, not a public launch event.

## Where this loops back

Every shipped slice becomes the next input for [Discovery](/docs/process/discovery/). Real usage is the cheapest source of new opportunities the team will ever have, and the only way to keep that source open is to keep shipping. Discovery, Design, and DevOps form a closed loop: customer interviews surface opportunities, shaping turns opportunities into pitches, DevOps turns pitches into evidence, evidence turns into the next interview question.

If this is the kind of help you need, the next step is a 30-minute call.

{{< hextra/hero-button text="Book a call →" link="https://cal.eu/accorderly" >}}