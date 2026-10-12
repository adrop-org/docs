# R-11: Which parts of the server logic could move into the program, and which should

Date opened: 2026-10-07. Status: Open (owner asked for the option to be documented; decide after the deadline)
Feeds: SPEC §3, §4; ADR after the hackathon; MF-1, MF-6, Q18

## Question
Today the Anchor program enforces the money and identity invariants; the server (attester) enforces policy. The
owner wants the option laid out: what else could live on-chain, what it buys, what it costs.

## Where the line is today (SPEC §2, §3)
| Check | On-chain today | Server today |
|---|---|---|
| One identity per proof (SGT mint), proof validity at registration | yes (`register_identity`) | looks the proof up (Helius) and builds the tx |
| Audience membership | yes (Merkle proof against `segment_root`) | builds the segment and the proof |
| Unused impression (nonce) | yes (`Impression` PDA) | issues the nonce |
| Global daily cap per identity | yes (`views_today`) | pre-checks |
| 70/20/10 split from escrow | yes | builds the tx |
| Attester approval of the view | yes (attester must sign) | the attention policy itself: dwell, visibility, focus, pointer, elapsed |
| Per-campaign frequency cap | no | yes |
| Host account is a real host | no (`host_ata.mint == usdc` only) | yes, allow-list (`HOST_ATAS`, MF-1) |
| Campaign funding | escrow balance only | x402 settlement, then forward + `activate_campaign` |
| Proof still held at pay time | no (MF-6) | no |
| Campaign scoped to a host (Q18) | no | no |

## Candidates
| # | Move on-chain | Buys | Costs | Verdict |
|---|---|---|---|---|
| A | **Host registry**: `Host` PDA (host wallet → host ATA, status), `pay_view` requires `host_ata == Host.ata` | removes the server allow-list and the trust that the attester names the right host; hosts self-register with a signature; prerequisite for host-scoped campaigns and per-host terms | one account, one instruction `register_host`, 32 bytes more in `pay_view`'s account list (watch the 4 KB stack: box the token accounts first) | **do first**, planned anyway (CLAUDE.md out-of-scope list → roadmap) |
| B | **Per-campaign frequency cap**: `Impression` PDA seeded by (campaign, identity, day, n) or a per-(campaign, identity) counter account | the advertiser's cap cannot be bypassed by a misbehaving attester; auditable | an extra account per (identity, campaign) or a counter in the proof; rent paid by the fee payer | do with A; small |
| C | **Proof re-check at pay time** (MF-6): `pay_view` reads the identity's SGT token account and requires balance 1 | a sold or moved Seeker token stops earning immediately | one more account in `pay_view`, one Token-2022 read; the identity must store the token account or derive it | do; needed for mainnet |
| D | **Campaign host scope** (Q18): `Campaign.hosts: Vec<Pubkey>` or a `CampaignHost` PDA; `pay_view` requires membership | host-sold campaigns are enforced by the chain, not by the server's pick | layout change (devnet reset) or an extra PDA per (campaign, host) | after A; needed when the first host sells its own inventory |
| E | **Attention policy parameters on-chain**: `Config.min_visibility`, `Campaign.min_dwell_ms` already stored; add the elapsed floor and make the attester sign a struct the program checks (`dwell_ms`, `issued_at` slot) | the policy becomes public and versioned; the attester cannot be softened silently | the attention *measurement* is still off-chain; the program can only check numbers the attester reports; adds bytes to `pay_view` | document, do not build: it moves trust, not truth |
| F | **Funding without the server**: advertiser transfers USDC to the escrow ATA and calls `activate_campaign` directly (permissionless already) | no server in the money-in path at all; an agent or a wallet funds with a plain transfer | loses the x402 receipt and the 402 flow that makes the agent story; keep both doors | **already possible**; document as the third funding door for wallets that do not speak x402 |
| G | **Impression issuance on-chain** (nonce as a PDA created before the view) | the server cannot issue impressions out of policy | one tx per ad shown, paid by someone, before anybody knows if the view qualifies: too expensive at $0.10 views | no |
| H | **Attention measurement on-chain** | none: the chain cannot see a screen | n/a | no; this is why there is an attester |
| I | **Multi-attester** (`Config.attesters: Vec<Pubkey>`, threshold) | removes the single attester as a point of trust | coordination, latency, one more signature per view | roadmap, after a second operator exists |

## Recommendation (for the ADR after the deadline)
Move A, B, C into the program in one devnet reset together with R-01 B (split as Config) and ADR-0003 (`pay_action`):
one layout change, one SPEC revision, one test campaign. Document F now as a funding door. Keep E, G, H off-chain:
the program should enforce *who, how much and how often*, never *what happened on a screen*. D follows A when the
first host-sold deal exists; I when there is a second operator.

## Owner decision
Pending.
