# ADR-0001: Hackathon stack and planning, decided by the owner without research notes

Date: 2026-10-05. Status: Proposed

## Context
Adrop is a Colosseum Crypto World's Fair entry due 2026-10-12. The owner arrived with a
finished spec and day plan (`source/SPEC.md`, `source/PLAN.md`) and the stack chosen.
Workspace ADR-0010 asks for a research note before each technical ADR and one planning
stage per session; that takes more sessions than the week has.

## Decision
- Stack as in hq `CLAUDE.md`, section "Code repo `adrop/`", not to be relitigated before submission:
  Anchor on Solana devnet; Node 20 + TypeScript + Express with x402 V2 reference packages;
  framework-free TypeScript SDK; Next.js demo host; Helius devnet RPC; one Hetzner VPS with
  Docker Compose. Seeker Genesis Token (devnet mock) as the only personhood proof. USDC only.
- No research notes for these choices. Any change after the hackathon gets a research note
  and a new ADR as ADR-0010 requires.
- All four planning stages were transcribed from the owner's documents in one session and
  marked Approved by the owner's "set everything up" on 2026-10-05. `SPEC.md` stays
  normative; the stage documents index it.

## Consequences
- Sessions build from `04-roadmap.md` tasks immediately.
- Post-hackathon (EVM settlement, other proofs, Unity) starts with research, as usual.
- Hosting deviates from workspace ADR-0002/0003 (iac-modules, OpenTofu); hq ADR-0001.
