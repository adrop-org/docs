# R-02: Market, competitors, and how many views make $1M a year

Date opened: 2026-10-06. Status: Open
Feeds: `05-business-plan.md`, pitch deck, ADR on payout split (with R-01)

## Question
How big is the market Adrop sells into, who else pays users or sells verified wallets to
advertisers, and what volume (views, daily earners, advertiser spend) does Adrop need for
$1M a year of protocol revenue at different prices and take rates.

## Criteria
1. Numbers with a source and a date; ranges where sources disagree.
2. Competitors compared on the things Adrop claims: pays the user, proof of personhood, settlement, who funds.
3. The $1M table readable by an investor in one glance.

## Findings 1: market size (checked 2026-10-06)
| Market | 2025 → 2026 | Note |
|---|---|---|
| Global digital ad spend | $710B → $781B (TBRC); $836B (PPC Chief) | 10% CAGR |
| Mobile ad spend | $492–496B in 2026 | ~58% of digital |
| In-game advertising | $11–12.5B (narrow: ads sold inside games) to $119–131B (broad definitions) | definitions vary 10×; use the narrow one |
| Mobile in-game ad revenue | > $50B in 2026 | rewarded video is the highest-eCPM format |
| Mobile game ad revenue (Sensor Tower, 19 countries, checked 2026-10-08) | > $12B in 2025; games monetising with ads 45.1% (2021-07) → 55.6% (2026-05) while IAP stagnates; India 70% of game revenue from ads, US 22% | the narrow, sourced figure for the pitch; AppLovin + AdMob = 65% of it |
| Rewarded video eCPM, US | iOS $10–25 (≈$19.6 tier-1), Android $5–20 (≈$16.5) | = $0.01–0.02 per view to the app; completion > 95% |
| Crypto / web3 ad spend | $1.2B (crypto advertising, 2025); web3 marketing services $2.1–2.7B (2025) | one "$12B web3 ad spend" figure exists; outlier, do not use |
| Crypto project marketing | most funded projects $5–30k/month; Coinbase Q1 2025 marketing $247M | 40% of blockchain companies spend > 30% of budget on marketing |
| Web3 CAC (HypeLab, 2026-03) | verified wallet $1.86–3.12 best case; wallet-targeted display $25–75; quest completion $5–25; DeFi average $85; exchange $150 | wallet-targeted CPM $20–40 |
| Supply of personhood proofs | Seeker phones 150k+ (SKR airdrop 2026-01); World ID 18M Orb-verified humans, 40M app downloads | Seeker = Solana-native sybil gate; World ID = cross-chain |

Where Adrop sits: it sells a *verified human's qualified attention* at CPA-like prices (dollars),
not impressions (cents). The right comparison is web3 CAC ($2–85 per wallet action), not eCPM.
At $0.10–1.00 per view Adrop undercuts every paid channel in the HypeLab table while paying the
viewer 70%.

## Findings 2: competitors (checked 2026-10-06)
| | Pays the user | Proof of personhood | Settlement | Who funds / how | Platforms | Stage |
|---|---|---|---|---|---|---|
| **W3AP** (blocksky Inc., Tokyo; the "w3ad" from Japan) | yes, BWP / ViewP "USD-backed" token on Base, or the game's own ERC-20 | "verified users", mechanism not disclosed | Base, real-time airdrop after completed view | advertisers in ViewP; bid or fixed reward per view | Unity SDK (2025-06), Web, React Native; Flutter + Chrome ext. planned | claims 8.2M verified users (its View-Fi / BackWallet apps), 1000+ partners, 20+ advertisers; SEA-first; investors SBI Investment, Gaiax; 90%+ completion in beta |
| Brave Ads | yes, 70% in BAT | browser install, no personhood | off-chain, monthly BAT | advertisers, CPM | Brave browser only | $5.95M total ever shared with users; Brave ARR ~$100M; 109M MAU |
| Mode Mobile / EarnOS | yes, points, "a sliver" | none | off-chain | advertisers, opt-in budgets | Android lock screen, own phones | 50M accounts, EBITDA $11.8M (2025) |
| Adsgram (Telegram / TON) | app is paid in TON; user rewarded by the app | none | TON | advertisers, CPM $0.5–16 | Telegram mini apps | the model Telegram games use today |
| Blockchain-Ads, HypeLab, Slise, Coinzilla | no | none (wallet targeting) | fiat / off-chain | advertisers, CPM $3–40 | display across web3 sites | Coinbase paid $20 CPA via Blockchain-Ads |
| Galxe, Layer3, Zealy (quests) | yes, tokens / points | sybil filters, weak | token airdrops | project pays $5–10k + rewards | web | CAC $5–25 per completion |
| Unity Ads, AdMob, AppLovin (rewarded video) | indirectly, in-game currency paid by the app | none | fiat, net 30+ | advertisers, eCPM $10–30 | Unity, iOS, Android | the incumbent in games |

What W3AP has that Adrop does not: a shipped Unity SDK, SEA distribution, a user app with
claimed millions of users, institutional investors. What Adrop has that W3AP does not: a
personhood gate enforced on-chain (one proof → one identity, SGT today, World ID next), payout in
USDC not a house token, the split auditable in one transaction, campaigns fundable by an AI agent
over x402, audience commitments (Merkle root) the advertiser can verify, chain-agnostic design.
Agents (checked 2026-10-10): W3AP has no advertiser API, MCP or x402 path; its roadmap lists "AI Agent for Full
Process Automation" (w3ap.org, no date). Pitch frame 7 shows "✗ on roadmap".

Precedent to respect: Brave paid users $5.95M in total over six years. Paying users is not the
moat; the price per unit of attention is. Brave sold impressions at cents; Adrop sells verified
actions at dollars.

## Findings 3: what $1M a year of protocol revenue takes
Protocol revenue = views × price per view × protocol share. Daily earners assume 3 claims a day
(cap is 10). Advertiser spend = $1M ÷ share.

| Price / view | Protocol share | Views / year | Views / day | Daily earners @3/day | Advertiser spend / yr | Viewer earns / yr (70%, 3/day) |
|---|---|---|---|---|---|---|
| $0.05 | 10% | 200M | 548k | 183k | $10M | $38 |
| $0.10 | 10% | 100M | 274k | 91k | $10M | $77 |
| $0.25 | 10% | 40M | 110k | 37k | $10M | $192 |
| $0.50 | 10% | 20M | 55k | 18k | $10M | $383 |
| $1.00 | 10% | 10M | 27k | 9.1k | $10M | $767 |
| $2.00 | 10% | 5M | 13.7k | 4.6k | $10M | $1,533 |
| $0.50 | 20% | 10M | 27k | 9.1k | $5M | $383 |
| $1.00 | 20% | 5M | 13.7k | 4.6k | $5M | $767 |
| $1.00 | 30% | 3.3M | 9.1k | 3.0k | $3.3M | $767 |

Reading it against the market:
- $10M advertiser spend is 0.8% of 2025 crypto ad spend ($1.2B) and 4% of Coinbase's one-quarter
  marketing budget. Reachable in principle; the constraint is supply of verified earners.
- At $0.10 per view (today's demo price) $1M needs 91k daily earners, 61% of all Seekers ever
  shipped. Not credible on Seeker alone. At $1.00 it needs 9.1k, 6% of Seekers, or 0.05% of
  World ID holders. At $1 per verified-human view Adrop is still 2–85× cheaper than every channel
  in the HypeLab table.
- So the price per view must be dollars, not cents, and the identity supply must widen past
  Seeker (World ID, R-01's proof types). Both are pitch statements, not code for this week.
- Protocol share: 10% needs 3× the volume of 30%. Networks keep 30–45% (R-01). A 20% share at
  $1 per view is 4.6k daily earners for $1M: the most defensible single row.

## Findings 4: expansion map (chains, apps, games)
| Target | Personhood proof available | USDC | SDK surface | Incumbent | Note |
|---|---|---|---|---|---|
| Solana apps + Seeker dApp store | SGT (150k), World ID (Solana support, verify) | native | web SDK (done), React Native | none paying users | first market; Seeker owners already hold the proof |
| Base / EVM L2s | Coinbase Verifications (EAS attestations), World ID | native | web SDK, same API | W3AP, HypeLab | W3AP's home turf; Coinbase Verifications is the natural proof |
| World Chain / OP stack | World ID native | yes | web SDK | – | largest proof pool, 18M |
| Telegram mini apps / TON | none strong; Telegram Premium ≠ personhood | USDT mostly | web SDK in mini app | Adsgram | high volume, low CPM, sybil-heavy; later |
| Mobile games (Unity, iOS, Android) | Play Integrity / App Attest (device tier) + World ID app | needs embedded wallet | Unity package | Unity Ads, AdMob, W3AP Unity SDK | W3AP is here first; Adrop's edge is the personhood tier + USDC |

## Findings 5: competition from the "plug-in ad network" angle (checked 2026-10-09)
The pitch now sells one thing: an agency pushes one campaign and it runs in every app that plugged in. Compared on that claim:

| | One campaign → every app | Host adds | Pays the person | One person, one identity | Paid in | Agency funds by |
|---|---|---|---|---|---|---|
| **Adrop** | yes, the campaign follows the person | one line | 70% USDC per view | yes, proof of personhood on-chain | USDC | one payment request (x402), human or AI agent |
| Unity Ads, AdMob, AppLovin | yes, across apps on the network | SDK + mediation setup | no (the app may pay in-game currency) | no | fiat, net 30+ | insertion order, self-serve dashboard |
| Adsgram (Telegram) | yes, across mini apps | SDK + block id | no, the app is paid | no | USDT on TON | dashboard; self-claims 75k advertisers / 35k publishers (2026-08) |
| Brave Ads | no, one browser | n/a | 70% in BAT | no, one browser install | BAT | managed sales, monthly invoice |
| W3AP / ViewFi (blocksky, Tokyo) | yes, Unity, Web, React Native | SDK | yes, ViewP house token on Base | "verified users", undisclosed | house token | advertiser dashboard; roadmap TGE Q3–Q4 2026; no 2026 press |
| HypeLab, Blockchain-Ads, Slise, Coinzilla | yes, web3 sites | tag | no | no, wallet targeting | fiat | sales, CPM $3–40 |
| Galxe, Layer3, Zealy (quests) | no, one quest page | n/a | tokens / points | sybil filters | tokens | project pays $5–10k + rewards |

What nobody else has, each verified against the vendor's own pages: a person paid in USDC from an auditable on-chain split,
a personhood gate that makes one human one identity, and a campaign an AI agent can fund without a sales call
(x402 is used to sell marketing *tools*, AdPrompt.ai 2026-02, not ad reach). What the incumbents have: scale, fill, mediation,
fiat billing. Adrop is not cheaper per impression; it is the only network where the budget reaches the viewer and the agency
knows the view was a real person.

Pitch line (slide 6, "why us"): "Ad networks reach every app, but the person earns nothing and bots count as views.
Earn apps pay people, but only inside one app or browser. Adrop is both: every app, every person paid, every view a real human."

## Recommendation
Position Adrop as "verified-human CPA for web3, paid out on-chain", priced in dollars per
qualified view, with the proof of personhood pluggable (ADR-0002) and the split a protocol
parameter (R-01). Name W3AP as the direct competitor and differentiate on identity, USDC, x402 and
audit, not on "we pay users" (Brave and W3AP already do). Target row for the plan: $1 per view,
20% protocol share, 4.6k daily earners → $1M protocol revenue on $5M advertiser spend.
What would change the answer: evidence that advertisers will not pay $1 for a verified view,
or that W3AP's identity layer is real sybil resistance.

## Owner decision
Pending.

## Sources (checked 2026-10-06; Findings 5 2026-10-09)
- W3AP Unity SDK release (openPR, 2025-06): https://www.openpr.com/news/4052717/earn-crypto-just-by-watching-ads-w3ap-launches-unity-ready
- blocksky Inc. PR TIMES (JP): https://prtimes.jp/main/html/rd/p/000000007.000133779.html ; W3AP site: https://w3ap.org/ ; Messari: https://messari.io/project/blocksky
- HypeLab, Crypto UA cost benchmarks 2026: https://www.hypelab.com/blog/crypto-user-acquisition-cost-benchmarks-2026
- Web3 growth platforms compared: https://chainaware.ai/blog/web3-growth-platforms-compared-2026/ ; https://www.blockchain-ads.com/post/best-web3-ad-networks
- Mobile game ad revenue 2025 (Sensor Tower via WN Hub, 2026): https://wnhub.io/news/analytics/item-51344 ; gaming ad stats: https://levvvel.com/statistics/gaming-advertising/
- Rewarded video eCPM 2026: https://blog.playio.co/rewarded-ad-benchmarks-2026 ; https://www.businessofapps.com/ads/rewarded-video/
- Digital / mobile / in-game ad spend: https://www.thebusinessresearchcompany.com/report/digital-ad-spending-global-market-report ; https://ppcchief.com/digital-ad-spend-statistics ; https://www.blog.udonis.co/advertising/mobile-advertising-market ; https://www.researchandmarkets.com/reports/5790772/in-game-advertising-market-report ; https://www.snsinsider.com/reports/in-game-advertising-market-11261
- Brave Ads: https://brave.com/blog/brave-ads-launch/ ; https://yipzap.com/brave-browser-valuation-revenue-model-and-user-stats-2026/
- Mode Mobile: https://www.fool.com/investing/2026/05/21/the-pre-ipo-stock-no-one-is-talking-about-that-pay/ ; https://kingscrowd.com/mode-mobile-on-dealmaker-securities-2026/
- Adsgram: https://docs.adsgram.ai/publisher/ ; https://richads.com/blog/5-best-adsgram-alternatives-to-consider/
- Web3 marketing spend: https://coinbound.io/web3-marketing/ ; https://www.blockchainappfactory.com/crypto-marketing-budget-benchmarks ; https://www.mordorintelligence.com/industry-reports/web3-marketing-services-market
- Seeker: https://www.theblock.co/post/381266/solana-mobile-skr-token-launch-in-january ; https://solanacompass.com/learn/breakpoint-25/update-from-solana-mobile-the-seeker-economy
- World ID: https://www.businesswire.com/news/home/20260417530721/en/ ; https://world.org/blog/world/world-faqs
- Findings 5: https://w3ap.org/ ; https://w3ap.org/aboutUs ; https://messari.io/project/blocksky ; https://adsgram.ai/blog/adsgram/adsgram-and-hilltopads-for-publishers-formats-requirements-and-payouts ;
  https://briefglance.com/articles/adsgrams-gambit-to-unify-telegrams-fractured-advertising-frontier ; https://community.brave.app/t/how-does-the-70-revenue-share-work-regarding-exchange-rate-flactuations/78570 ;
  https://martechseries.com/sales-marketing/programmatic-buying/adprompt-ai-marketing-and-advertising-agentic-solution-available-on-x402-utilizing-x402-for-pay-per-use-payments-settled-on-base-l2/ ;
  https://coinbound.io/top-crypto-ad-networks/ ; https://chainaware.ai/blog/best-crypto-advertising-networks/
