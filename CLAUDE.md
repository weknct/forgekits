# CLAUDE.md — forgekits (public marketplace)

PUBLIC repo `weknct/forgekits`: the ForgeKits marketplace manifest + 4 free **Lite**
plugins. Top-of-funnel discovery; routes buyers to Premium on forgekits.dev.

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
Portfolio is built; remaining work is account-gated — see hub `08.ACTION-Waiting-On-You.md`.
For this repo specifically: #16 (submit the 4 Lite packs to the directories) via
`directory-submission/`.
