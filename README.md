# clow-studio — ARCHIVED (2026-11-06)

**This repository is archived.** Its content has been merged into
[`dnzengou/clow-studio-reloaded/web/marketing/`](https://github.com/dnzengou/clow-studio-reloaded/tree/main/web/marketing)
so there is one canonical source for every surface in the ecosystem.

## Where the live product lives now

| Surface | Repo |
|---|---|
| **`https://clow.studio/`** (the Go binary on Fly.io) | **[`dnzengou/clow-studio-reloaded`](https://github.com/dnzengou/clow-studio-reloaded)** |
| `https://clow-tau.vercel.app/` (marketing site, blog, deck, AEO kit) | [`dnzengou/clow`](https://github.com/dnzengou/clow) |
| Deck mirror on GitHub Pages | `web/` subtree of `clow-studio-reloaded` |

See [`ARCHITECTURE.md`](https://github.com/dnzengou/clow-studio-reloaded/blob/main/ARCHITECTURE.md)
in `clow-studio-reloaded` for the full topology.

## Why this is archived

Before 2026-11-06 this repo carried a thin static marketing shell that
had drifted from the live product. Having two places called "clow-studio"
risked splitting the brand's SEO authority and confusing AI agents that
resolve the entity. Unifying everything behind one Fly.io target with
one source of truth fixes that.

## If you want to contribute

- To fix a **bot handler, engine, or server behaviour** →
  [`dnzengou/clow-studio-reloaded`](https://github.com/dnzengou/clow-studio-reloaded).
- To fix a **marketing page, blog post, deck, or AEO asset** →
  [`dnzengou/clow`](https://github.com/dnzengou/clow).

Contact: des@desiredsolutions.me
