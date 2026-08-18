---
title: AI ethics policy
type: docs
weight: 2
---

This is my standard advice for AI on client projects: the suggestions I make by default and the goals I work towards. Where a project needs something outside these defaults, I work with the client to do it safely.

## TL;DR

Generative AI is on the table when the liability is designed for: automated checks, human expert review where needed, and the client owning the output.

- No generative AI for creative work or chatbots by default. Both are on the table when the risk is controlled.
- AI output is never treated as fact. It gets checked.
- Code and data generation only where every output can be checked deterministically.
- Open source or open-weight models preferred.

## The policy

- Generative AI is not my default for copy, images, or artwork. If a project needs it, the work gets a human pass before it ships.
- I don't lead with thin model wrappers as products. Embedded command palettes and composer features are fine. Where a chatbot is the right answer, the liability side is designed in from the start.
- Voice AI is input only by default: transcription, not synthetic voices. A synthetic voice needs verified copyright permission from the original speaker.
- Language models can't verify their own answers. Anything presented as fact gets checked against an original source, by automated rules, or by a human expert.
- Code and data generation fits where every output can be checked deterministically. In [Moffatt v. Air Canada (2024 BCCRT 149)](https://www.canlii.org/en/commentary/doc/2025CanLIIDocs1963), the airline was liable for a bereavement fare its chatbot invented. When that risk applies, I advise on automated and human expert checking, and the client assumes full responsibility for the output.
- Open source or open-weight models are preferred, because most training data was gathered without permission and models anyone can run give some protection back to the community. A client who chooses a closed model owns that choice and its risks.
- No products marketed towards replacing jobs or avoiding doom.

Creative and strategic work stays with real people.
