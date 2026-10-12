# ADR-0004: Audience and personhood are separate layers

Date: 2026-10-08. Status: Accepted (owner, 2026-10-08). Supersedes the wallet-list sentence in hq ADR-0007 Consequences and R-03 §2.

## Context
Adrop recorded "targeting is pull, never wallet lists from advertisers" as a product principle (hq contract rule 4). The owner's
position is narrower: Adrop must never *be* a data company, but an advertiser that already holds wallets may use them. R-12
separates who defines the audience from how strong the viewer's proof is.

## Decision
- Adrop sells nothing. It is a protocol over which advertisers, hosts, viewers and audience providers run an economy.
  Adrop never builds, sells or exports audience data. A root goes in; members never come out.
- Three layers: **protocol** (escrow, qualified-view rules, Merkle membership, global daily cap, 70/20/10; always on,
  audience-blind), **audience** (the set behind the root: the advertiser's own list, an Adrop public-chain segment, or a
  third-party provider's root), **personhood** (a proof bound to an identity; Adrop verifies proofs, never issues them).
- Personhood is required for open audiences and not for closed lists:

| Audience | Personhood required | Sybil risk carried by |
|---|---|---|
| Open (untargeted, behaviour segment, third-party open root) | yes | the escrow, so Adrop gates it |
| Closed (advertiser list, third-party closed root) | no | the advertiser, by choosing the list |

- The viewer is paid either way.

## Consequences
- Public principle becomes: "Adrop never builds, sells or exports a wallet list. Advertisers may bring their own; the wallet
  owner is paid either way." Applied to hq rule 4 and HANDOFF now; public copy (README, docs, landing, deck, script) after
  the 2026-10-12 submission, since the list path is not built.
- Roadmap, nothing before 2026-10-12: `Identity.proof_type` gains "none, list-only"; a list-only registration path; closed
  campaigns labelled on the API and in the ad slot; the R-12 guards (hashed upload, minimum size, bucketed reach, viewer
  opt-out, price floor, membership-oracle rejection); `DATA.md` covenant; audience-provider v1 then v2.
- hq ADR-0007's `test_wallets` is a closed audience that still demands proof; it becomes the first real list campaign once
  the flag exists. "Fresh wallets earn nothing" stays true for every open campaign.
- Cost: one person holding ten listed wallets can claim ten times on a closed campaign; that is the advertiser's list quality.
