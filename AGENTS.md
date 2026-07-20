# AGENTS.md — Accorderly repo notes

A small Hugo site built on the [Hextra](https://github.com/imfing/hextra) theme.
No app code, no tests, no linter — the build is the only verification.

## Stack and versions

- Hugo `0.156.0` **extended** (matches `.github/workflows/pages.yaml`)
- Go `1.26` (Hugo modules dependency)
- Node, npm, etc. are not used

If a build fails with a shortcode or icon error, it is almost always a Hextra API mismatch, not a Hugo one. Check `themes/.../data/icons.yaml` (cached under `~/.cache/hugo_cache/modules/filecache/modules/pkg/mod/github.com/imfing/hextra@v0.12.3/data/icons.yaml` after first build) before guessing icon shortcodes.

## Commands

```shell
# First-time / after changing go.mod
hugo mod tidy

# Dev server — bind 0.0.0.0 lets you hit it from another device on the LAN
hugo server --bind 0.0.0.0 -p 1313 --disableFastRender

# Production build (mirrors CI)
hugo --gc --minify --baseURL https://accorderly.com/
```

After `hugo mod tidy`, restart any running `hugo server` so the module cache is picked up.

## Verification before push

There are no tests. The only signal is a clean build:

```shell
hugo mod tidy && hugo --gc --minify --baseURL https://accorderly.com/
```

If you changed prose, also do a manual read against the *Plain-language writing rules* section below. The site is not externally tested for conformance; this is the contract that all prose on the site is checked against manually. New prose that violates it (jargon, marketing fluff, double negatives, buzzwords) is a bug.

## Plain-language writing rules (internal contract)

The whole site should read like a clear note from one person to another: short sentences, everyday words, one idea per paragraph, no marketing fluff. This section used to live at `content/docs/accessibility.md` as a public page; it was moved here because the guidance is for the agent / author, not for site visitors.

### Authorship

- The human contributor must always edit and rewrite any draft prose themselves before committing. Anything an agent writes is a first draft, not finished copy.
- AI cannot be trusted to write well on its own. Treat generated prose as material to react to, not as text to ship.
- Unless the user's prompt is very specific, it is fine — and often better — to leave a section as a placeholder instead of guessing. Write a short note that names the topic, the context, and what the section needs to say, and let the human fill it in their own voice.
- A concrete placeholder beats mediocre auto-generated copy. When in doubt, mark the gap and stop.

### Plain language

- Short sentences. Aim for under 20 words. Break long ones in half.
- Everyday words. If a simpler word works, use it.
- One idea per paragraph. If a paragraph covers two ideas, split it.
- Active voice. "I write code" instead of "code is written".
- Present tense where it fits. "The loop converges" instead of "the loop will have converged".
- Define a term the first time it is used, especially if it is a process name like "delivery".
- No idioms, no culture-specific references. They do not survive translation.
- No marketing fluff. No "best-in-class". No "world-class". No "robust".

### Structure

- Headings describe the section they head. "How engagements work" is fine. "Going forward" is not.
- Every long page starts with a TL;DR: 2–4 bullets that summarise the page in a way that lets you stop reading.
- Use bullet lists when order does not matter.
- Use numbered lists when order does.
- Code, commands, file paths, and identifiers are in code formatting. Nothing else is.

### Tone

- Direct, not chatty.
- Helpful, not promotional.
- Honest about what is and is not in scope.
- One voice. The whole site is written by one person — it should sound like it.

### Writing patterns to avoid (tropes)

Adapted from [tropes.fyi/tropes-md](https://tropes.fyi/tropes-md). Any single one of these used once is fine; the problem is when several appear together or one is repeated. Most of these are anti-patterns the model reaches for by default. Catch them before publishing.

**Word choice**

- No "quietly", "deeply", "fundamentally", "remarkably", "arguably" as decorative intensifiers
- No "delve" — use "look at" or "look into"
- No "tapestry", "landscape", "paradigm", "synergy", "ecosystem", "framework" used as decoration. ("Framework" is fine in its literal sense — the DevOps framework, the Design Council framework — but not as a synonym for "field" or "area".)
- No "leverage" as a verb. No "utilize" — use "use".
- No "robust", "streamline", "harness", "seamless"
- No "serves as", "stands as", "marks", "represents" as a substitute for "is" or "are"

**Sentence structure**

- No "It's not X — it's Y" refrains, "It's not bold. It's backwards." style. One in a piece can be effective; ten is a tell. The reader can tell that X is Y without the inversion.
- No "Not X. Not Y. Just Z." countdowns
- No self-posed rhetorical questions like "The result? Devastating." Just say the thing.
- No anaphora — repeating the same sentence opener three or four times in a row
- No stacked tricolons. One rule-of-three is fine. Three in a paragraph is a pattern-recognition failure.
- No "It's worth noting", "Importantly", "Interestingly", "Notably" as filler transitions
- No "-ing" phrases tacked onto the end of sentences to imply shallow analysis ("highlighting its importance", "contributing to the development of")
- No "from X to Y" ranges where X and Y aren't actually on a spectrum
- No em-dashes for manufactured drama. One or two per page is fine. Eight is not. If a comma or colon does the job, use that.
- No "Despite its challenges" formula that acknowledges problems only to dismiss them

**Paragraph structure**

- No short punchy fragments for manufactured emphasis. "He published this. Openly. As a book." — no. Write like a human thinks, not like a captioned infographic.
- No "listicle in a trench coat" — paragraphs that disguise themselves as continuous prose but are really sequential points starting with "The first… The second… The third…"

**Tone**

- No "Here's the kicker / thing / deal / where it gets interesting" — the buildup is bigger than the payoff
- No "Think of it as…" or "It's like a…" analogies that oversimplify the reader's own concept
- No "Imagine a world where…" futurism filler
- No false vulnerability ("And yes, I'm openly in love with…"). Either say the thing or don't.
- No "The truth is simple / History is unambiguous / The metrics are clear" assertions of clarity in lieu of being clear
- No grandiose stakes inflation. "This will fundamentally reshape how we think about everything." — no.
- No "Let's break this down", "Let's unpack this", "Let's dive in"
- No vague attributions. If you can't name the expert, the report, or the paper, don't cite it. "Experts argue", "Industry reports suggest", "Several publications have cited" — all banned.
- No invented concept labels. "The supervision paradox", "The acceleration trap" — these are rhetorical placeholders, not concepts.
- No dead metaphor. Pick one and use it once or twice, don't beat it into the ground across the entire piece.

**Composition**

- No fractal summaries. Don't say "In this section we'll explore…" at the top and "As we've seen in this section…" at the bottom. The TL;DR is the only summary that's allowed.
- No historical-analogy stacking. The "Apple didn't build Uber, Facebook didn't build Spotify, Stripe didn't build Shopify" pattern is banned. One analogy at a time.
- No one-point dilution. Don't restate the same thesis eight ways across four thousand words. If a paragraph can be cut without losing information, cut it.
- No content duplication. The same paragraph appearing twice in a single piece is a sign of unedited output.
- No "In conclusion" signposts. The reader can tell.

**Formatting**

- No bold-first bullets. Every bullet starting with `**Keyword**: …` is a tell.
- No Unicode decoration in prose. Use straight quotes, hyphens, and `->` or `→` only where it actually carries meaning. Real writers type straight quotes.
- No emoji in marketing copy. Process pages with a single small emoji for the diamond icon (via Hextra's `icon` parameter on `{{< card >}}`) is fine; that is iconography, not decoration.

### Review checklist

Before publishing any page, read it once and answer these:

1. Could a smart non-expert understand every sentence?
2. Does each heading tell the reader what the section is about?
3. Is every paragraph about one idea?
4. Is every list either clearly ordered or clearly unordered?
5. Are there any idioms, slang, or jargon that the reader would have to look up?
6. Are there any superlatives, buzzwords, or marketing-only words ("best", "world-class", "robust", "seamless")?
7. Does the TL;DR actually save the reader from reading the page when they only need the gist?
8. If a sentence says nothing, is it cut?
9. Are any of the [tropes](https://tropes.fyi/tropes-md) patterns present? If more than one is, the piece is slop — fix it.
10. Does the prose sound like Chris Hart, or like an LLM imitating Chris Hart?

If any answer is "no" or "sort of", fix it before publishing.

### Out of scope

Technical accessibility (WCAG, screen-reader semantics, keyboard nav, contrast) is a separate piece of work and is not the contract this section enforces. When that work starts, it will live in its own internal doc.

## Hextra gotchas

These are easy to get wrong on first contact:

- **Icons.** Names come from `themes/.../data/icons.yaml`. Heroicons-style names that are *missing* include `rocket`, `infinity`, `pencil`. Valid alternatives used here: `paper-airplane` (Delivery), `arrows-expand` (loop), `search` (Discovery), `pencil-alt` (Design), `book-open` (Accessibility).
- **Hero shortcode is `{{< hextra/hero-section >}}` (and `-headline`, `-subtitle`, `-button`)**, not `{{< hero >}}`. There is no top-level `{{< hero >}}`; using one will fail with `template for shortcode "hero" not found`.
- **Cards are `{{< cards >}}{{< card link="..." title="..." icon="..." subtitle="..." >}}`** — `link` is relative to the section root, not the site root. `docs/process/discovery` works inside `content/docs/_index.md` but not inside `content/_index.md` (use `docs/process/discovery` there).
- **Footer copyright.** The default footer reads `© 2026 Hextra Project.` — a translation key. Override it in `i18n/en.yaml` with `copyright: "..."`. Do not edit the theme.
- **Favicon cleanup.** Hextra's bundled theme `static/` ships `favicon-16x16.png`, `favicon-32x32.png`, `site.webmanifest`, and `android-chrome-*.png`. Because the project `static/` does not shadow them, they reappear in `public/` on every build even though no HTML references them. This is harmless but expected — do not chase it. Our `layouts/_partials/favicons.html` keeps the rendered HTML clean.
- **Unused theme files in `public/`.** The output directory may contain `favicon-16x16.png`, `favicon-32x32.png`, `site.webmanifest`, `android-chrome-*.png`, `categories/`, `tags/`. These come from Hextra's bundled static files; nothing in `content/` references them. Safe to ignore.

## Where things live

| Area | File / path | Notes |
|---|---|---|
| Site config | `hugo.yaml` | title, `baseURL`, navbar menu, `editURL`, footer flags |
| Copyright override | `i18n/en.yaml` | keyed `copyright` |
| Favicon HTML | `layouts/_partials/favicons.html` | overrides hextra's to drop unused PNG/manifest refs |
| Custom domain | `static/CNAME` | contains `accorderly.com`; do not remove unless you intend to drop the domain |
| Favicon / icons | `static/favicon.ico`, `static/favicon.svg`, `static/apple-touch-icon.png`, `static/images/accorderly-icon.svg` | sourced from the sibling `vibefix.dev` project |
| Workflow | `.github/workflows/pages.yaml` | builds on push to `main`, deploys to GitHub Pages |
| Old demo / Netlify | none | demo content was already deleted; `netlify.toml` and `pages.yaml` (orig) replaced |

## Process docs are sourced — do not invent

The pages under `content/docs/process/` are a synthesis of published frameworks with attribution. Edits should keep the attribution honest and the names of the original authors / books / sites intact. Current sources:

- **Discovery** — Teresa Torres, *Continuous Discovery Habits* (2021) and the Opportunity Solution Tree at `producttalk.org`
- **Design** — UK Design Council's Double Diamond (`designcouncil.org.uk`) and *Shape Up* by Ryan Singer (Basecamp)
- **DevOps** — *The DevOps Handbook* (Kim, Humble, Debois, Willis, Forsgren) and The Three Ways

The Triple Diamond name is a synthesis, not a single canonical model. If a future page uses the word "diamond", it should make clear which framework it is borrowing from. The file is `devops.md`, not `delivery.md` — the third diamond covers build, ship, observe, not just shipping.

## Deploy

Production deploy is **GitHub Pages**, not bunny.net. The workflow reads the base URL from `actions/configure-pages`, so the local `--baseURL` and the deployed URL do not have to match. Do not hardcode `baseURL` in `pages.yaml`.

A bunny.net Storage Zone + Pull Zone deploy was the original plan but is deferred. If it comes back, restore it as a workflow sibling — the artifact (`public/`) is identical.

## Contact info (must stay consistent)

- Email: `hello@accorderly.com`
- Booking: `https://cal.eu/accorderly`
- LinkedIn: `https://www.linkedin.com/company/accorderly/`

Contact info lives in one place: the `layouts/_shortcodes/reach-me.html` shortcode, which is used by `content/_index.md` (the "Reach me" section) and `content/docs/_index.md`. The old `content/about.md` and `content/contact.md` pages were folded into the homepage; if those pages are reintroduced, the contact details must match the shortcode. `grep -rE 'hello@|cal\.eu|linkedin\.com/company/accorderly' layouts/ content/` is the cheap verification.

## Repo conventions

- Markdown content under `content/`, with front-matter and shortcodes
- Hextra docs-style pages live under `content/docs/` and use `type: docs`
- Section indexes are `_index.md`; pages are bare `<name>.md`
- No CI lint, no tests — keep builds local before pushing
- Company name on legal/copyright lines: **Accorderly Technologies Inc.**

## When stuck

**Hard rule: when in doubt about a Hextra feature, shortcode, layout, or parameter, read the official Hextra docs at <https://imfing.github.io/hextra/docs/> first, before guessing or digging only in the cache.** The docs are the source of truth for how the theme is meant to be used; the cached templates confirm what a specific version actually does.

1. Check the Hextra docs at <https://imfing.github.io/hextra/docs/> — shortcodes, layout params, configuration, and gotchas.
2. Look at the hextra theme layout at `~/.cache/hugo_cache/modules/filecache/modules/pkg/mod/github.com/imfing/hextra@v0.12.3/layouts/`. That's the source of truth for shortcodes, partials, and what each one expects. Docstrings inside the templates are worth reading.
3. Site params Hextra exposes are listed in `themes/.../data/` (icons.yaml) and `themes/.../layouts/_shortcodes/` (shortcode files).
4. The `content/docs/accessibility.md` rule applies to any new prose.
