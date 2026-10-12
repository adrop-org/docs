# R-15: Should Adrop ship a browser extension, and in which form?

Date opened: 2026-10-11. Status: Open (first pass only, desk research, high level)
Feeds: `04-roadmap.md`

## Question
Would a browser extension work for Adrop, and what does it change for viewer, host, advertiser and protocol?

## Criteria
To agree with the owner. Draft:
1. Keeps the host's 20% and the "apps opt in" model.
2. Reaches people who hold the proof of personhood (Seeker Genesis Token).
3. Passes Chrome Web Store review.
4. Does not make bot farming easier than the SDK path.

## Candidates
| Candidate | One line |
|---|---|
| A. SDK companion | Extension holds opt-in and identity; ads still only in host apps that embed `adrop-sdk` |
| B. Own surfaces | Ads on the extension's new tab / popup (Brave, Gener8 model); extension is the host |
| C. Ad injection | Ads inserted into third-party pages |

## Method
Desk research, first pass 2026-10-11. Next: current Chrome Web Store policy text, Seed Vault seed export, session-key or batched claims in the program.

## Findings
- C: Chrome allows injectors only with clear disclosure; deceptive injection gets extensions disabled.
  Sites get nothing, which breaks the host share. Rejected. ([Google, 2015](https://security.googleblog.com/2015/03/out-with-unwanted-ad-injectors.html?m=1))
- B: works (Gener8 rewards mode, Swash, Brave in-browser ads), but competes with the hosts.
  ([Swash review](https://paidfromsurveys.com/swash-review), [Gener8 listing](https://extscope.org/zh/extension/agplbamogoflhammoccnkehefjgkcncl))
- A, per side:
  - Viewer: opts in once in the extension; a session key could sign claims, so no signature per view.
  - Host: same SDK; it detects the extension and skips opt-in, so more viewers convert.
  - Advertiser / agent: unchanged x402 campaign; the extension measures attention better, but it is client-side code to trust.
  - Protocol: escrow and 70/20/10 unchanged; new work = extension, store review, session-key or batched `pay_view` (program change).
- Risks:
  - Device mismatch: the Genesis Token lives in the Seed Vault Wallet on the Seeker, keys in hardware; extensions are desktop.
    Seed export to a desktop wallet not confirmed. ([Solana Mobile](https://blog.solanamobile.com/post/seed-vault-wallet----solana-seekers-native-mobile-wallet))
  - Automation: an extension is easier to farm; personhood plus daily caps still bound it.
  - "Install an extension" adds friction against the one-signature story.

## Recommendation
A, as a roadmap line only ("desktop companion: opt in once, earn everywhere"), after the Seeker-on-desktop question is answered.
Open: Seed Vault export; World ID or other proofs that live on desktop; Chrome policy for crypto payouts.

## Owner decision
