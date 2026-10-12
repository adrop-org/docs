# ADR-0002: Personhood proof is pluggable; Seeker Genesis Token is the first, not the design

Date: 2026-10-05. Status: Accepted (owner, 2026-10-05: "keep sgt as recommended i agree with everything")

## Context
Every qualified view pays USDC from an advertiser's escrow. Without a one-human-once gate, one
person with a thousand wallets drains any campaign. The owner wants Solana as the entry point
only: other chains, every kind of dapp, games. The concern was that the Seeker Genesis Token
(SGT) ties Adrop to one device and one chain and makes a poor on-ramp for everyone else.

## Decision
- The gate is *a proof of personhood*, not a token. On-chain `Identity` stores `proof_type: u8`
  and a 32-byte nullifier; campaigns, impressions and payouts never look at the proof again.
  Adding a proof = one more register path, nothing else moves.
- Hackathon: SGT is the only implemented proof (`proof_type 0`, nullifier = sha256(mint)).
  Reasons: free, already in every Seeker owner's wallet, zero sign-up, native Solana story for
  the judges. Devnet uses a mock mint with the same Token-2022 layout; only the group address
  in config differs.
- Roadmap order of further proofs, each a `proof_type`: World ID (cross-chain, largest base,
  works in games), Coinbase Verifications (EVM attestation), Play Integrity / App Attest
  (mobile games, device level, weaker tier). A user with no proof can run the host app but
  does not earn until verified once.
- Not an on-ramp: email or phone alone. Fraud farms hold those in bulk; advertisers pay the bill.
  A lower-priced unverified tier is a later pricing question, not a proof.
- Pitch: "first of several proofs, World ID next"; the proof-type abstraction goes on the
  architecture slide. No second proof before submission; if one is forced in, it is World ID
  on devnet, traded against the Blink stretch item, never against the core demo.

## Consequences
- `register_identity` stays SGT-only in code; SPEC §3 unchanged.
- Public doc for users and judges: code repo `docs/IDENTITY.md`.
- Post-hackathon: research note on World ID's Solana verifier before its ADR (workspace ADR-0010).
