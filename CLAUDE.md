# CLAUDE.md

This file is written for Claude. It describes this repository and how Claude should behave here.

## What This Repo Is

**DBJ_ICEBERG** is the public blog for DBJ Method — EA AI ROI advice for SMEs navigating AI adoption.

- Live site: https://iceberg.dbj.org/
- Built with Hugo Extended + PaperMod theme
- Deployed via GitHub Actions on push to `main`

## Your Role Here

Content editor and Hugo technician. Tasks here are:
- Adding or editing blog posts
- Fixing Hugo/PaperMod configuration
- Managing the deploy workflow
- Migrating posts from DBJ_METHOD_DEV

Not an advisory role — that is DEV's domain.

## Hugo Conventions

- **Theme:** PaperMod, installed as a git submodule at `themes/PaperMod`
- **Config:** `hugo.toml` in root
- **Content:** `content/posts/` — one folder per post
- **Page bundles:** every post is `content/posts/post-name/index.md` with images local to that folder
- **Search page:** `content/search.md` — do not remove, PaperMod requires it
- **Build:** `hugo --minify` — always use Extended variant (required for PaperMod SCSS)
- **Local verification:** before calling any layout/CSS/template change done, run `hugo server --minify` and check it at `http://localhost:1313/` (or whatever port it binds). Never claim a visual change works without having checked it against the dev server first.

## Post Frontmatter

Every post must have:

```yaml
---
title: "Post Title"
date: YYYY-MM-DD
description: "One sentence — used in post listings and SEO."
tags: ["tag1", "tag2"]
author: "Dusan B. Jovanovic"
---
```

Optional cover image (local to post folder):

```yaml
cover:
  image: "filename.jpg"
```

## Comments (Giscus)

Comments are enabled via [Giscus](https://giscus.app), backed by GitHub Discussions on this repo.

- **Partial:** `layouts/_partials/comments.html` — overrides PaperMod's blank stub with the Giscus script
- **Config:** `hugo.toml` has `comments = true` under `[params]` and a `[params.giscus]` block with repo/category IDs
- **Discussion category:** `General` (`DIC_kwDOSkKOj84C-RO1`)
- PaperMod's built-in `comments.html` is an empty stub — the override in `layouts/_partials/` is required

## .claude/settings.json Policy

`.claude/settings.json` (and `.claude/settings.local.json`) must **not** be tracked in git. This repo is worked on from both Windows and Linux, and this file accumulates machine-specific Bash permission allowlist entries (e.g. absolute Windows paths like `g:/DBJARH/DBJ_ICEBERG/...`) that are meaningless or wrong on the other OS. Each dev/OS keeps their own local copy; it is gitignored. Do not re-add it to tracking or commit changes to it.

## Ownership

- &copy; dbj@dbj.org
- MIT License

## Behavioral Rules

1. **No padding.** No summaries, no affirmations.
2. **Do not invent URLs.**
3. **Repo map is `repos_index.md` in METAREPO.** The authoritative map of all repos is at `G:\METAREPO\repos_index.md`. Do not look for `repos.md` in this repo — it no longer exists here.
