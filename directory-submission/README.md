# Directory Submission — get ForgeKits discovered

The `weknct/forgekits` marketplace is already installable
(`/plugin marketplace add weknct/forgekits`). This folder is the **submission package**
to get its 4 free Lite packs *listed* in the public Claude Code plugin directories, so
people discover them and funnel to Premium + the Sprint.

All listing copy is pre-written in `listing-copy.md` — paste-ready. This README is the
where-and-how, ordered by value.

> ⚠️ **Verify each destination URL + exact form fields at submit time.** The Claude
> plugin ecosystem is moving fast; directories and submission paths change. The *copy*
> in `listing-copy.md` stays valid regardless.

## What you're submitting

- **The marketplace:** `weknct/forgekits` (public GitHub repo with
  `.claude-plugin/marketplace.json`). Most directories list the *marketplace*; plugins
  are discovered inside it.
- **4 Lite plugins:** Client Attraction Engine (Lite), Process Decomposition (Lite),
  SDLC Forge (Lite), MCP Builder (Lite). All free; each upsells its Premium on
  forgekits.dev.

## Where to submit (in priority order)

| # | Destination | Why | How | Verify |
|---|---|---|---|---|
| 1 | **Official Anthropic submission** | Highest trust + reach | Submission form at `claude.ai/settings/plugins/submit` **or** `platform.claude.com/plugins/submit` (one of these is current) — submit the marketplace repo URL + the per-plugin copy | the live form |
| 2 | **anthropics/claude-plugins-official** | Anthropic-managed curated directory | Open a PR adding ForgeKits to its `.claude-plugin/marketplace.json` (read its CONTRIBUTING first; quality/security bar). Use the marketplace.json snippet in `listing-copy.md` | repo's CONTRIBUTING |
| 3 | **claudemarketplaces.com / claudepluginhub.com** | Large auto-indexed community dirs | Many auto-discover public marketplaces from GitHub; if there's a "Submit" button, paste the repo URL + marketplace one-liner | each site |
| 4 | **claudecodecommands.directory** | Community commands/agents dir | `…/submit` (commands) — optional, lower priority | the site |

Start with #1 and #2 (the Anthropic-tied ones). #3/#4 are quick extras.

## Step-by-step

1. **Sanity-check the marketplace is healthy.** Confirm
   `/plugin marketplace add weknct/forgekits` then `/plugin` lists all 4 Lite packs and
   each installs cleanly. (A reviewer will do exactly this.)
2. **Submit #1 (official form).** Open the current submission URL, sign in as
   admin@weknct.com, and submit the marketplace repo. Paste from `listing-copy.md`:
   the marketplace description, and per-plugin name + description + keywords + category
   + homepage as the form asks.
3. **Submit #2 (PR to the official directory).** Fork `anthropics/claude-plugins-official`,
   add the ForgeKits entry to its marketplace.json using the snippet in
   `listing-copy.md`, open a PR with the provided title/body. Address review notes.
4. **Submit #3/#4 (community dirs).** Paste the repo URL + one-liner into each site's
   submit form (or confirm they auto-indexed you).
5. **Track** below as each goes live.

## Submission tracker

| Destination | Submitted | Status |
|---|:--:|---|
| Official form (#1) | ☐ | — |
| claude-plugins-official PR (#2) | ☐ | — |
| Community dir(s) (#3) | ☐ | — |
| claudecodecommands (#4) | ☐ | — |

## Note on the "3 vs 4" packs

Older docs said "3 Lite plugins" — there are now **4** (MCP Builder Lite was added).
`listing-copy.md` covers all four. (Hub `01.BUILD-STATUS.md` line corrected.)
