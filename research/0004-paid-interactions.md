# R-04: Should Adrop pay extra when a viewer interacts with an ad, and how?

Date opened: 2026-10-06. Status: Done 2026-10-06
Feeds: ADR-0003 (paid actions); `05-business-plan.md` §3, §7.10, §8, §10

## Question
The owner's idea (2026-10-06): a view pays one amount; an *interaction* pays a second amount from
a separate budget, through a new server endpoint and a new program instruction. Decide which
interactions are worth paying for, who verifies them, how they fit the escrow / attester / x402
design, what they are worth, and when to build.

## Criteria
1. The advertiser values the interaction more than the view and can verify it. Otherwise it is
   "incentivised traffic", which the market prices down or refuses (findings 1).
2. Fraud surface no larger than views: one identity, one paid action per impression, a window,
   the chain or the attester as judge.
3. Fits the current design: payouts stay program transfers from the campaign escrow (contract rule 1),
   money in stays x402, no new trusted party. One program layout change, done together with R-01 B.
4. The advertiser sets one price per view, one price per action and an action budget. No splits.
5. Nothing before 2026-10-12 (hq `CLAUDE.md`: conversion bonus is roadmap). A slide in the pitch now.

## Findings 1: how the market prices view, engagement, click and action (checked 2026-10-06)
| Level | Who pays for it today | Price precedent | Fraud / quality signal |
|---|---|---|---|
| View (CPM, CPV) | every network; Adrop today | rewarded video pays the app $0.01–0.02 (R-01); Adrop targeted $0.50–1.00 (R-03) | viewability, dwell, attention checks (SPEC §2) |
| Engagement (CPE) | Google Lightbox: advertiser pays when the user hovers 2 s to expand ([AdSense help](https://support.google.com/adsense/answer/4643299)); offerwalls bill per event, e.g. "reach level 2" ([Unity, 2016](https://unity.com/blog/user-acquisition-offerwall-cpe)) | cents to dollars; Unity's example: pay $30 for a player who reaches level 5 and is worth $40 | engagement is measurable but says nothing about intent |
| Click (CPC) | display and Telegram networks; Adsgram CPC from $0.01, CPM from $0.20 ([Adsgram 2025](https://adsgram.ai/blog/adsgram/10-best-telegram-advertising-platforms)) | rewarded-video end cards: ~3% post-view CTR (Tapjoy), 4% in a Fox campaign ([Marketing Dive](https://www.marketingdive.com/news/20th-century-fox-drives-4-ctr-from-interactive-cards-in-video-ad/507531/)); playables 30–40% higher CTR than video | Pixalate Q2 2025: **35% of mobile-app clicks and 19% of desktop clicks invalid** ([ExchangeWire 2025-10-07](https://www.exchangewire.com/blog/2025/10/07/pixalates-q2-2025-north-america-click-fraud-benchmark-reports-for-mobile-apps-desktop-web-mobile-web/)); Google forbids paid-to-click outright and counts "encouraging clicks" as invalid, "except for rewarded inventory" ([AdSense policies](https://support.google.com/adsense/answer/2660562)) |
| Action (CPA, CPI, CPE in offerwalls) | affiliate and offerwall networks; web3: HypeLab, Blockchain-Ads, Addressable; quests: Galxe, Layer3 | web3 cost per wallet $2–8; wallet connect 15–25% of landing visitors, swap 0.5–2%, mint 0.3–1.5%, deposit 0.2–0.8%; targeted campaigns convert 2–3× untargeted ([HypeLab 2026-03-09](https://www.hypelab.com/blog/on-chain-attribution-wallet-ad-conversions)); quest completion $5–25 (R-02) | ~22% of non-organic installs carry fraud signals, click flooding and SDK spoofing dominant ([AppsFlyer 2026 edition](https://www.appsflyer.com/resources/reports/mobile-ad-fraud-state)) |
| Incentivised action | offerwalls: the user gets in-game currency, the publisher 30–60% of the advertiser's payout (Xsolla up to 90%) ([Adapty](https://adapty.io/glossary/offerwall/), [Xsolla](https://developers.xsolla.com/sdk/offerwall/)); offerwall users show 3.8× D14 retention ([Unity](https://unity.com/blog/rewarded-ads-how-value-exchange-shapes-mobile-monetization)) | non-incent CPI pays $1–8 more than incent for the same offer ([Mobile Commerce Daily](https://www.retaildive.com/ex/mobilecommercedaily/5-tips-to-ensure-the-effectiveness-of-mobile-ad-campaigns)); mislabelled incent traffic is treated as fraud ([Impact](https://discover.impact.com/?p=15363)) | "the device is genuine, the human is genuine, the interest is close to zero" ([Adex](https://adex.com/blog/?p=6007)) |

What this says:
- The industry already sells three things at three prices: a view, an engagement, an action. The
  owner's idea is the normal shape of the market, not an invention. Adrop's novelty stays the same:
  the person doing it is a verified human and gets paid on-chain.
- **A paid click is the weakest product.** It buys curiosity, a third of clicks are invalid even
  without a reward, and the one network everybody benchmarks against bans paying for it. Do not
  pay for clicks as a separate event.
- **A paid on-chain action is the strongest.** It is deterministic ("a swap is a swap"), attributable
  without cookies by the wallet address, and already priced in dollars by web3 networks. Coinbase
  bought Spindl in 2025 for exactly this attribution ([The Block](https://www.theblock.co/post/338276/coinbase-acquires-web3-adtech-platform-spindl));
  Blockchain-Ads sells on-chain conversion tracking at a $1,000/month minimum ([Coinbound](https://coinbound.io/crypto-ad-network-attribution/)).
  None of them pays the user; quests (Galxe, Layer3) pay the user but have weak sybil filters (R-02).
- **Paying the user for an action makes it incentivised traffic.** Advertisers will price it below
  non-incent CPA. The answer is thresholds the advertiser sets (minimum swap size, hold period,
  deposit kept N days), so the payout is for a customer, not a click. Offerwalls prove the model
  works at scale when the event is meaningful (level 5, not install).

## Findings 2: which interactions, who verifies, what they are worth
| Kind | Viewer does | Verified by | Weakness | Suggested price |
|---|---|---|---|---|
| `click` | opens `cta_url` | SDK event, attested like dwell | pays for curiosity; counts as the view's pointer interaction already | none as a separate payout; a campaign may *require* a click for the view |
| `engage` | answers a one-question quiz or poll in the creative, or plays a playable ≥ 10 s | SDK event + answer, attested; correctness checkable server-side | moderate; brand-lift value only | +$0.05–0.25 on the view |
| `onchain` | within a window after the view, the identity's wallet signs a tx against the advertiser's program or mint that meets a threshold (amount, duration) | the chain: attester reads the wallet's signatures since `paid_at` (Helius enhanced transactions or [webhooks](https://docs.helius.dev/docs/webhooks)), checks target and threshold | wash activity → thresholds and hold windows set by the advertiser; delayed payout for holds | $2–8 (CPW range), $1 floor |
| `blink` | the CTA is a Solana Action: the ad returns a tx the viewer signs in the slot (swap, mint, deposit) with memo `adrop:<impression_id>` | the chain, no window and no lookup: the tx carries the impression id | needs the advertiser to host an Action (or Adrop to wrap one) | same as `onchain`; the cleanest demo |
| `postback` | an off-chain conversion (sign-up, purchase) | advertiser signs `{impression_id, kind}` with its campaign key; the viewer then claims | advertiser can under-report; it only pays for what it confirms, so the risk is to the viewer, not the escrow; reputation fixes it | advertiser's CPA |

Attribution: the SDK appends `?adrop=<impression_id>` to `cta_url` (HypeLab's click-id pattern); windows
1 / 7 / 30 days as the market uses them, default 7. The viewer's wallet is public on-chain anyway, so
`onchain` and `blink` reveal nothing new to the advertiser; the "no lists" rule (contract rule 4) holds
because the advertiser still never receives an audience list, only the actions its own program saw.

Order to build: `onchain` and `blink` first (strong, demoable, priced), `engage` second (cheap, SDK-only),
`postback` third (needs advertiser key management). `click` never as a payout.

## Findings 3: how it fits the program, server and SDK
Candidates for where the action money lives:
| Candidate | One line | Criteria |
|---|---|---|
| A. Two prices, one escrow, separate action budget | `Campaign` gains `price_per_action`, `action_budget`, `action_spent`, `action_kind`, `action_window_s`, `action_target`; new `Action` PDA per impression; `pay_action` instruction | meets 1–5; one layout change, devnet reset (do with R-01 B) |
| B. Separate action campaign linked by id | own account, own escrow, second x402 payment | meets 1–4; doubles accounts, funding and withdraw paths for no gain |
| C. Server-held action pool | server pays actions from a protocol wallet | breaks contract rule 1 (payouts from escrow by the program) |

A in detail:
- Program: `Action { impression, kind: u8, paid_at }` at `["action", impression]`; existence = paid, so one
  action per impression and the view's Merkle proof, identity and nonce are reused, not re-proved.
  `pay_action(evidence_hash)`: signers viewer, attester, fee payer; checks `impression.identity == identity`,
  `identity.owner == viewer`, campaign Active, `now - impression.paid_at ≤ action_window_s`,
  `action_spent + price_per_action ≤ action_budget`, escrow ≥ price; transfers with the Config split
  (R-01 B) and the campaign PDA as authority. No Merkle proof and no identity counter: smaller frame
  than `pay_view`. `Campaign` grows ~50 bytes, so box the token accounts in `PayView` first (handoff
  note on the 4 KB frame). `withdraw_unspent` returns both pools; `activate_campaign` unchanged.
- Funding: `POST /campaigns` body gains `action: {kind, price, budget, window_s, target, min_amount}`;
  `POST /campaigns/:id/fund` charges `budget + action.budget` in one x402 payment and forwards the
  total to the escrow. The advertiser still sets two prices and two budgets, nothing else.
- Server: `POST /actions {impression_id, kind, evidence}` verifies per kind (`onchain`: Helius signatures
  for `identity.owner` after `paid_at`, parsed, target and threshold; `blink`: the tx signature and memo;
  `engage`: the SDK report; `postback`: a stored advertiser-signed conversion), builds the `pay_action`
  tx, signs as attester and fee payer, returns `{action_id, tx_base64}`; `POST /actions/:id/submit`
  as for claims. `POST /campaigns/:id/conversions` for postbacks. `GET /identity/:wallet` adds
  `pending_actions` so a hold-window payout shows on the next visit.
- SDK: the creative shows "Watch $0.35 · Act +$2.00"; `onReward` fires for both; `cta_url` carries the
  impression id; a `blink` creative renders the Action's button in the slot.
- Devnet demo: `action_target` = the advertiser's wallet, action = "send ≥ 1 devnet USDC", or a Blink
  that does it. Same mock as the `dex_swap_30d` segment.
- Effort: program ½ day (state, instruction, 6 tests: happy path, second action on the same impression,
  window expired, action budget exhausted, wrong viewer, escrow short; devnet reset), server ½–1 day,
  SDK and demo ½ day. About two days, after the deadline.

Split for actions: same Config split as views to start. Offerwalls give the publisher 30–60% of an
action, more than the 20% a host gets on a view; if hosts push, add `action_host_bps` to Config later.

## Findings 4: what it adds to the numbers (`model.py` table H, business plan §7.10)
Assumptions, to be replaced by real campaigns: paid actions as a share of targeted views 1 / 3 / 5%
(HypeLab: 0.5–2% swaps from landing visitors, 2–3× for targeted; Adrop viewers already hold a wallet,
sit in a behaviour segment and are paid to act), price per action $1 / $3 / $5 (CPW $2–8, incent discount).
| | Worst | Realistic | Best |
|---|---|---|---|
| Actions per year | 7.3k | 219k | 1.6M |
| Action spend | $7k | $657k | $8.21M |
| Protocol revenue, views + actions | $10k | $1.01M | $9.31M |
| Share of protocol revenue from actions | 7% | 13% | 18% |
| One viewer earns per year (extra from actions) | $36 ($3) | $302 ($39) | $776 ($137) |

The realistic case crosses $1M protocol revenue with actions; without them it needs year 2 of the ramp
(§7.5). The action layer matters less for revenue than for the pitch: it is the piece advertisers
already budget for (CPA), and it turns the viewer's $0.30 view into a $2–3 event.

## Risks
- Incentivised-action discount: advertisers pay below non-incent CPA. Mitigation: advertiser-set thresholds
  and hold windows; sell it as "verified human who did X", not "paid click".
- Wash actions (swap $1 back and forth): thresholds, one action per impression, the global daily cap.
- Regulatory: paying someone to make a financial transaction can be an inducement. The UK FCA cryptoasset
  financial-promotion rules (in force 2023-10-08) ban incentives to invest, such as refer-a-friend bonuses;
  other jurisdictions differ. **Owner + counsel** before `onchain` actions on financial products; `engage`
  and `postback` on non-financial products carry none of this.
- Hold-window payouts need the viewer back in a host app to sign; `pending_actions` handles it, and a
  viewer-less `pay_action` for `onchain` (the wallet already signed the action itself) is a later option.

## Recommendation
Build candidate A after the deadline, kinds `onchain` and `blink` first, `engage` second, `postback` third,
no paid clicks; do the layout change together with R-01 B in one devnet reset. Put it in the pitch now as
the roadmap line "view, engage, act: three prices, one escrow, one verified human". We give up simplicity
in `Campaign` and one more instruction to audit. What would change the answer: advertisers in the first
three real campaigns refuse to pay for incentivised on-chain actions at ≥ $1, or counsel rules out paying
for financial actions in the launch markets.

## Owner decision
Accepted 2026-10-06: Adrop will integrate these action kinds (no paid clicks), after the deadline,
with R-01 B in one devnet reset. Recorded as ADR-0003.
