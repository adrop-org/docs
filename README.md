# Adrop docs

The thinking behind [Adrop](https://adrop.sh), the ad network that pays the viewer: business plan, research notes,
decisions and the pitch deck. Code: [adrop-org/adrop](https://github.com/adrop-org/adrop). Developer docs:
[docs.adrop.sh](https://docs.adrop.sh).

| Folder | What is in it |
|---|---|
| `business/` | `business-plan.md` (market, customers, pricing, revenue model; draft, numbers come from the research notes) and the diagrams used with agencies (`illustrations/`) |
| `research/` | Research notes, one question each: revenue splits, market and competitors, platform rules and tiered pricing, paid interactions, customers, on-chain vs server, audience tiers and data, ad SDK landscape, AI agents buying ads, browser extension |
| `decisions/` | Architecture decision records: stack, pluggable proof of personhood, paid actions, audience and personhood layers |
| `pitch/` | `adrop-pitch.pdf`, the pitch deck |

Each note starts with its status (Open, Draft, Done, Accepted) and date. Research notes end with what the owner decided.

This repo is a read-only mirror published by CI from the source repo on every change. Issues and pull requests are
accepted on [adrop-org/adrop](https://github.com/adrop-org/adrop). References such as "hq ADR-0007" or "hq #3" point
at the private operations repo. Text and diagrams are CC BY 4.0 (`LICENSE`).
