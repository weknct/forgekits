# CLAUDE.md — forgekits (public marketplace)

PUBLIC repo `weknct/forgekits`: the ForgeKits marketplace manifest + 4 free **Lite**
plugins. Top-of-funnel **lead magnets** that route prospects to the done-for-you ForgeKits
service on forgekits.dev.

> **⚠ PIVOT (2026-06-25):** ForgeKits is now a **hosted, done-for-you service**, not a sold
> product. These free Lite plugins prove the method and drive **service intakes** — they no
> longer funnel to a "buy Premium" purchase. Keep them public; never publish premium source.

## Identity (NON-NEGOTIABLE)
- Public byline **Michael Xander**; company **WEKNCT, INC.**; email **admin@weknct.com**.
- Real owner name appears nowhere. Git author every commit:
  `Michael Xander <admin@weknct.com>`.
- This repo is **public** — never commit anything internal/sensitive (pricing ops,
  customer data, secrets, premium source).

## Layout
- `.claude-plugin/marketplace.json` — the manifest (4 Lite plugins; bump `version` on change).
- `plugins/{cae,process-decomposition,sdlc-forge,mcp-builder}-lite/` — Lite plugin source.
- `directory-submission/` — paste-ready kit to list ForgeKits in public plugin
  directories (see its README; submission is account-gated → hub `08.ACTION` #16).

## Rules
- Lite source is published here from `forgekits-build/plugins/` — treat that as upstream
  if they diverge.
- Run `claude plugin validate ./plugins/<name>` before publishing changes.
- Keep README + marketplace.json in sync (4 packs; don't reintroduce the stale "3").

## Resume pointer
Platform is built; remaining work is account-gated — see `forgekits-hq/08.ACTION-Waiting-On-You.md`.
For this repo specifically: optionally submit the 4 Lite packs to public plugin directories
via `directory-submission/` (still valid as lead-gen, now funneling to the service).
