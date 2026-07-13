# Accorderly

**Accorderly Technologies Inc.** — solo tech consulting. Continuous discovery, design, and delivery, run in parallel rather than as three hand-offs.

This repo is the source for [accorderly.com](https://accorderly.com). It is a small Hugo site built on the [Hextra](https://github.com/imfing/hextra) theme and deployed to GitHub Pages.

## What's in here

- `content/_index.md` — landing page
- `content/about.md` — about
- `content/contact.md` — contact details
- `content/docs/` — the working docs:
  - `_index.md` — "How I work" index
  - `accessibility.md` — the plain-language guideline that shapes how everything on this site reads
  - `process/` — `discovery.md`, `design.md`, `delivery.md`, plus an overview
- `static/` — favicons, the wordmark (`images/accorderly-icon.svg`), and the `CNAME` file that pins GitHub Pages to `accorderly.com`
- `hugo.yaml` — site config
- `.github/workflows/pages.yaml` — builds the site on push to `main` and deploys to GitHub Pages

## Local development

Requires [Hugo](https://gohugo.io/getting-started/installing/) (extended) and [Go](https://golang.org/doc/install).

```shell
hugo mod tidy
hugo server --bind 0.0.0.0 -p 1313
```

The `--bind 0.0.0.0` flag is useful if you want to test from another device on the same network.

## Production build

```shell
hugo --gc --minify --baseURL https://accorderly.com/
```

The output goes to `public/` and is what gets uploaded.

## Deployment

Deploys are handled by GitHub Actions on every push to `main`. The workflow is `.github/workflows/pages.yaml`:

1. Checks out the repo with submodules
2. Installs Hugo `0.156.0` extended and Go `1.26`
3. Runs `hugo mod tidy` then `hugo --gc --minify --baseURL "${{ steps.pages.outputs.base_url }}/"`
4. Uploads `public/` as a Pages artifact
5. Deploys the artifact to GitHub Pages

The base URL is set at build time from the `actions/configure-pages` step, so the same workflow runs cleanly against both the default GitHub Pages URL and a custom domain.

### One-time setup

1. In the repo, open **Settings → Pages**.
2. Under **Build and deployment → Source**, pick **GitHub Actions**.
3. (Optional) Under **Custom domain**, enter `accorderly.com` and follow GitHub's instructions to add the DNS records (apex + `www`). The repo already ships `static/CNAME` so once the domain is verified Pages will serve from it without further config.

You can also run the workflow manually from the Actions tab (`workflow_dispatch`).

## When to move to bunny.net (later)

The site is one file, the build is ~70 ms, and traffic at launch will be near zero. GitHub Pages is fine for that.

If any of these change, switch the deploy to bunny.net:

- You start seeing throttling past the Pages bandwidth cap (currently ~100 GB/month before throttling kicks in)
- You need tunable cache TTLs or push-button cache purges
- You want the site on its own edge nodes for geographic reasons

The bunny.net deploy would be the same `hugo --gc --minify` artifact plus an `rclone sync` to a Storage Zone and an explicit Pull Zone purge. The workflow we previously had is straightforward to bring back when it becomes worth it.

## Accessibility — by design

Every page on this site is written against the plain-language guideline in [`content/docs/accessibility.md`](./content/docs/accessibility.md). The short version:

- Short sentences, one idea per paragraph
- Everyday words; define a term the first time it's used
- Headings describe the section they head
- Every long page opens with a TL;DR

If a future page on this site reads like marketing fluff, that page is wrong.
