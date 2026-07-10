# Setup

This repo serves two roles — both now point at **[alpertarhan.dev](https://alpertarhan.dev)**:

| File | Role |
| --- | --- |
| `README.md` | GitHub **profile README** (shown on `github.com/alpertarhan`). All links → `alpertarhan.dev`. |
| `index.html` | **GitHub Pages redirector** → `alpertarhan.dev`. No app, no build step. |
| `.github/workflows/badges.yml` | Daily job that refreshes the README stat-badge `src` URLs from the GitHub GraphQL API. |

> The interactive terminal portfolio **moved to [alpertarhan.dev](https://alpertarhan.dev)** (rebuilt in Astro: same terminal aesthetic, plus a blog + TR/EN i18n). This repo is now a thin redirect + profile README layer so old links keep working.

## Enable the Pages redirect (one time)

1. **Settings → Pages**
2. **Source:** `Deploy from a branch`
3. **Branch:** `main` · **Folder:** `/ (root)` · **Save**
4. Wait ~1 min → visiting `alpertarhan.github.io/alpertarhan/` now instantly redirects to `alpertarhan.dev`.

## The actual site

The source for `alpertarhan.dev` lives in a **separate repo** (`alpertarhandev`, Astro). Build-time it fetches live GitHub data (with an optional `GITHUB_TOKEN` to lift the anonymous 60 req/hr cap to 5000/hr) and bakes it into the terminal + project cards — no client-side fetch, no rate-limit cliff.

## Stat badges

The `badges.yml` action updates these `src` URLs daily (real GitHub counts, never dead):
`followers`, `following`, `flagship ★`, `own projects`. No env secrets needed — it uses the default `GITHUB_TOKEN` provided to every Action run.
