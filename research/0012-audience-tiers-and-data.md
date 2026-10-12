# R-12: Audience tiers, advertiser-supplied wallets, and what Adrop stores

Date opened: 2026-10-08. Status: Open (owner decisions 1–3 recorded; k, DATA.md timing, v2 provider shape open)
Feeds: ADR-0004 (audience and personhood layers), R-03 (tiers), hq ADR-0007 (test audience), `05-business-plan.md` §3/§6,
`adrop/docs/IDENTITY.md`, a future `adrop/docs/DATA.md` covenant. Source: outside-session notes `hq/inbox/audience-tiers/NOTES*.md`.

## Question
Which audience offers does Adrop run, which data does it hold to run them, and where is the line it never crosses?

## Criteria
1. The viewer is paid for every use of their wallet, and Adrop never becomes a data company (owner).
2. Every paid view stays fraud-safe for the escrow (ADR-0002: a wallet is free, a farm drains escrow).
3. No code before 2026-10-12; docs and decisions only.

## Owner decision (2026-10-08)
1. Adrop sells nothing. It is a protocol; advertisers, hosts, viewers and audience providers run an economy over it.
   Adrop never builds, sells or exports audience data.
2. An advertiser that already holds wallet addresses (its own users, or a list bought from a data company) may run a
   campaign against that list. Adrop learns the list only to build the Merkle root and never hands wallets to anyone.
3. Personhood is a separate layer from the protocol: required for open audiences, not for closed lists, where the
   advertiser chose the wallets and bears the sybil risk. Adrop verifies proofs, never issues them.
4. Wallet-list wording in public copy: unchanged until after submission (default taken 2026-10-08; it describes what is built).

## Findings 1: three layers
- **Protocol.** Escrow per campaign, qualified-view rules (SPEC §2), Merkle membership against the campaign root, the global
  daily cap, 70/20/10. Always on; audience-blind: the program only sees "this identity is in this root". This is what the 10% pays for.
- **Audience.** The set behind the root. Built three ways, same root and same on-chain campaign: the advertiser's own list
  (*closed*); a public-chain behaviour segment Adrop builds, e.g. `dex_swap_30d` (*open*); later a root published by a
  third-party audience provider paid by the advertiser directly, Adrop not in the data path (*open or closed*).
  A root goes in, members never come out: advertisers and providers get counts, delivery and spend.
- **Personhood.** A proof (SGT, World ID, …) bound to an identity. It exists because an open audience exposes the escrow to
  anyone who can create wallets. A closed list has no such exposure.

| Audience | Personhood required | Sybil risk carried by |
|---|---|---|
| Open (untargeted, behaviour segment, third-party open root) | yes | the escrow, so Adrop gates it |
| Closed (advertiser list, third-party closed root) | no | the advertiser, by choosing the list |

On a list campaign the protocol still enforces nonce, dwell, attention, membership and the daily cap per identity. It cannot
stop one person holding ten listed wallets; that is the advertiser's list quality, paid for by the advertiser.

## Findings 2: audience axes (the owner's "targeted / personhood / unverified" are two axes)
Axis A, audience definition: A0 untargeted (built, `tags: []`); A1 contextual by host category (needs host registry, roadmap);
A2 behavioural from public chain data (built, the product); A3 advertiser list, closed (demo-only today via `test_wallets`,
becomes the first real list campaign); A4 viewer-declared interests, paid a premium (year 1); A5 cross-app behavioural profile
from SDK telemetry (**refused**: the mining the owner rejects); A6 lookalike over public-chain features only (later).
Axis B, proof tier (ADR-0002 unchanged): B0 strong personhood (SGT, World ID Orb, Coinbase Verifications), full price;
B1 device attestation (Play Integrity, App Attest), lower tier; B2 unverified wallet: never paid on open campaigns.
"Unverified" is not an earning tier; the cheap tier is A0×B0 (R-03).

## Findings 3: how others do it (checked 2026-10-08)
Brave: contextual IAB segments plus advertiser keyword segments, matched on device, no uploaded lists. Slise: public chain data,
no attribution beyond click. Blockchain-Ads: device-to-wallet graph across 37 chains, $10k/month minimum. Addressable: 23M
wallet-to-social matches, retargeting on X and Reddit. ChainAware: per-wallet profiles sold by API. Meta and Google customer
match: hashed upload, match count returned, minimum audience before serving (Meta ≥100, Google ≥1,000; verify). Chrome
Protected Audience: on-device auction with k-anonymity, being phased out. Crypto networks differentiate on *more* wallet data;
Adrop's difference is structural: the viewer is paid to opt in, the proof replaces the fraud graphs, segment data is public already.

## Findings 4: what Adrop stores, and the line
Must hold: `identities(wallet, proof_type, nullifier)` (on-chain); `impressions(identity, campaign, nonce, issued_at, dwell,
paid)` for caps and the attester signature, 90 days then aggregate; `segments(tag, wallet)` as a rebuildable cache of public
queries, tag definitions in the public repo; campaign roots on-chain.
Never build, and say so publicly: no per-identity profile across hosts, no interest inference from views, no wallet-to-device
or wallet-to-social matching, no pixel, no SDK telemetry beyond the qualified-view check; no export (counts, delivery, spend
only; `/audiences/estimate` returns `reachable` only as a bucket at or above k, proposed k = 100); no resale, no data-partner
programme, no lookalike seeded from private data.
Leak that exists regardless: every payout is a public transfer escrow → viewer, so anyone can join "which identities saw which
advertiser". Mitigations are roadmap: aggregated payout batching, `rotate_identity_wallet`, a viewer opt-out from closed campaigns.
Guards for closed lists: hashed upload (sha256 of pubkey), raw list dropped after the root is built; minimum matched size k;
viewer consent text and opt-out; price floor at the targeted tier (≥ $0.25, R-01); reject lists of one or lists differing by
one wallet (membership oracle); label closed campaigns on `GET /campaigns/:id` and in the ad slot.

## Findings 5: delivery model and who owns identity (from code on main `8600d12`)
Advertisers push once (`POST /campaigns` + fund, audience frozen in the root); every host's `loadAd()` pulls the first active
campaign whose leaves contain the identity, under caps and budget. The campaign follows the person across hosts; the
advertiser never picks hosts (host scope is roadmap). Limits: no channel to a wallet that has not opted in anywhere (push =
Blink or wallet notification, stretch); hosts must be on the allow-list; selection is first-match, not highest price
(add `ORDER BY price_per_view DESC`).
Identity: read and verify, never issue. Issuing proofs means biometric or KYC liability. Two partner roles: proof providers
(Solana Mobile, World, Coinbase, Play Integrity) answer "one human?"; audience providers (the advertiser, Addressable,
Blockchain-Ads, a wallet or dapp) answer "who is eligible?". Provider integration v1: list handed to Adrop under contract,
Adrop builds root and proofs, exports nothing. v2 (target): provider publishes root plus count; the SDK fetches the membership
proof from the provider at claim time; Adrop never sees members. Needs the root's provider on the campaign and an attester
that verifies a proof it did not build.

## Side note: can targeting be hidden entirely? (owner question, 2026-10-08; research task)
Open question for a later note: can Adrop hide *who* is targeted, even from itself and from chain observers? Candidates to
evaluate: provider v2 above (Adrop never holds members); encrypted or hashed lists with blind matching (private set
intersection between the advertiser's list and the identity registry, so neither side learns the other's members); on-device
matching as in Chrome Protected Audience; zero-knowledge membership proofs against the root (the viewer proves membership
without revealing which leaf, hiding the viewer from the advertiser's delivery logs); and payout privacy (aggregated or
shielded payouts) since the public escrow → viewer transfer is the larger leak. Criteria: viewer still paid, escrow still
fraud-safe, attester still able to enforce caps. Time box one session after the deadline.

## Recommendation
Record decisions 1–3 as ADR-0004 now. Before 2026-10-12 nothing else changes except factual fixes to the deck. After: the
`DATA.md` covenant next to `IDENTITY.md`; list-only `proof_type` and a registration path; `ORDER BY price` on selection; host
scope; audience-provider v1 then v2; then the side note above. A5 never. Wallet-list wording switches to "Adrop never builds,
sells or exports a wallet list; advertisers may bring their own, and the wallet owner is paid either way" after submission.

## Sources
- Brave Ads targeting: https://ads-help.brave.com/campaign-performance/targeting
- Web3 platforms compared (vendor-written): https://chainaware.ai/blog/web3-growth-platforms-compared-2026/
- Blockchain-Ads: https://www.blockchain-ads.com/technology ; Addressable: https://cryptonews.net/news/blockchain/30776607/
- Customer-list upload (Meta, Google): https://www.accuracast.com/faq/custom-audiences-upload/
- Chrome Protected Audience: https://privacysandbox.google.com/relevance/protected-audience-api
- World ID: https://docs.world.org/world-id ; SGT: https://docs.solanamobile.com/solana-mobile-stack/seeker-genesis-token.md
