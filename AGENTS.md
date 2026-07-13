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

## Contact info (must stay consistent in three places)

- Email: `hello@accorderly.com`
- Booking: `https://cal.eu/accorderly`
- LinkedIn: `https://www.linkedin.com/company/accorderly/`

When updating any one of these, edit all three of: `content/_index.md`, `content/about.md`, `content/contact.md`. `grep -rE 'hello@|cal\.eu|linkedin\.com/company/accorderly' content/` is the cheap verification.

## Repo conventions

- Markdown content under `content/`, with front-matter and shortcodes
- Hextra docs-style pages live under `content/docs/` and use `type: docs`
- Section indexes are `_index.md`; pages are bare `<name>.md`
- No CI lint, no tests — keep builds local before pushing
- Company name on legal/copyright lines: **Accorderly Technologies Inc.**

## When stuck

1. Look at the hextra theme layout at `~/.cache/hugo_cache/modules/filecache/modules/pkg/mod/github.com/imfing/hextra@v0.12.3/layouts/`. That's the source of truth for shortcodes, partials, and what each one expects. Docstrings inside the templates are worth reading.
2. Site params Hextra exposes are listed in `themes/.../data/` (icons.yaml) and `themes/.../layouts/_shortcodes/` (shortcode files).
3. The `content/docs/accessibility.md` rule applies to any new prose.
