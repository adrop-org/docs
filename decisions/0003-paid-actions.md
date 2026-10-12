# ADR-0003: Campaigns pay for a verified action after a view, from a separate action budget

Date: 2026-10-06. Status: Accepted (owner, 2026-10-06: "document that we can and will integrate into
adrop protocol these kinds of actions")

## Context
Adrop pays a verified human for a qualified view. The market sells three things at three prices:
a view, an engagement, an action; the action (CPA) is the line advertisers already budget, and in
web3 it is priced at $2–8 per wallet (R-04). The owner wants a second payout when the viewer
interacts, from an additional budget, through a new endpoint and a new program instruction.

## Decision
- A campaign may carry a second price, `price_per_action`, and an `action_budget`, in the same
  escrow as the view budget. Views are unchanged; a campaign without an action budget behaves as today.
- Action kinds, in build order: `onchain` (the identity's wallet signs a tx against the advertiser's
  program or mint meeting an advertiser-set threshold, within a window), `blink` (the ad's CTA is a
  Solana Action signed in the slot, memo carries the impression id), `engage` (one-question quiz,
  poll or playable in the creative), `postback` (advertiser-signed off-chain conversion).
  **No paid clicks**, ever: a click may be required for a view, never paid as an event.
- One paid action per impression: `Action` PDA at `["action", impression]`, existence = paid.
  `pay_action` reuses the impression's identity and proof; signers viewer, attester, fee payer;
  checks window, action budget, escrow; pays with the Config split (R-01 B).
- Money in stays x402: `POST /campaigns/:id/fund` charges view budget + action budget in one payment.
  Advertisers set two prices and two budgets, nothing else; they still never receive wallet lists.
- Built after the 2026-10-12 deadline, in the same devnet reset as the Config split (R-01 B).
  Until then it is a roadmap slide: "view, engage, act: three prices, one escrow, one verified human".

## Consequences
- `Campaign` grows about 50 bytes: box the token accounts in `PayView` first (4 KB frame).
- SPEC.md gains a "Paid action" section (§2 qualified action, §3 `Action` + `pay_action`, §4 `/actions`,
  `/actions/:id/submit`, `/campaigns/:id/conversions`, `GET /identity/:wallet.pending_actions`) when built.
- Incentivised actions are discounted by advertisers; thresholds and hold windows are the answer.
  Hold windows mean delayed payouts the SDK shows on the next visit.
- Paying for financial on-chain actions can be an inducement (UK FCA cryptoasset promotion rules);
  owner and counsel decide per launch market before `onchain` on financial products.
- An on-chain action reveals the acting wallet to the advertiser's program; it is public already.
