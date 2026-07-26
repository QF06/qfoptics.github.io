# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

This repo is the source for a personal GitHub Pages site (`qfoptics.github.io`, owner `QF06`) belonging to Qingfeng Li, an optics/photonics engineer. It is a static [Jekyll](https://jekyllrb.com/) site using the remote theme [`mmistakes/minimal-mistakes`](https://github.com/mmistakes/minimal-mistakes) (`minimal_mistakes_skin: default`). There is no application code — just Jekyll content/config and a couple of static assets.

There is no Gemfile, no build scripts, and no CI workflow in this repo. GitHub Pages builds and deploys the site automatically on every push to `main` using its own supported Jekyll/theme toolchain — there is nothing to run locally as part of normal edits.

## Repository layout

- `_config.yml` — site-wide Jekyll config: title/description, `remote_theme`, enabled `plugins` (`jekyll-include-cache`, `jekyll-seo-tag`, `jekyll-sitemap`), `author` block (name, avatar, bio, location, email, social links), and `defaults` (applies `layout: single` and `author_profile: true` to every page).
- `index.md` — the site's only content page. Front matter sets `permalink: /`, so this file *is* the home page ("About" page with bio, highlighted project, contact info).
- `_includes/head-custom.html` — theme override/injection point for the page `<head>` (minimal-mistakes supports this file for custom head content); currently empty.
- `assets/` — static files referenced from content/config: `Avatar.png` (profile photo) and `Lebenslauf_202403_QL_en.pdf` (CV, linked from `index.md`).

## Working in this repo

- Content edits are just Markdown/YAML edits to `index.md` and `_config.yml` — no build step is required to make a change; GitHub Pages rebuilds on push.
- To preview locally before pushing, you'd need to add a `Gemfile` (typically bundling the `github-pages` gem to match GitHub's build environment) and run `bundle exec jekyll serve` — neither exists yet, so don't assume a local preview is available unless you set one up.
- Adding a new page: create a `.md`/`.html` file with YAML front matter; it will inherit `layout: single` and `author_profile: true` from the `defaults` in `_config.yml` unless overridden in that page's own front matter.
- `_config.yml`'s `author.avatar` currently points to `/assets/avatar.jpg`, but the actual file in `assets/` is `Avatar.png`. If you touch the avatar, fix this path/case/extension mismatch rather than adding another inconsistent reference.
- `baseurl: /qfoptics.github.io` combined with `url: https://qf06.github.io` matters for any links/assets you add — use root-relative paths (e.g. `/assets/...`) consistently with the existing content rather than hardcoding the baseurl.
