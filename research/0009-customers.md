# R-09: Who are our customers: ideal customer profile, segments, first ten targets

Date opened: 2026-10-07. Status: Done 2026-10-07 (desk research; interviews are the next step)
Feeds: `05-business-plan.md` §4, §6; hq #3 (founder quotes); R-08 (agencies); `06-agency-brief.md`

## Question
Who pays Adrop, in what order, and what do they need to see before they do?

## Criteria
1. Money: budget exists today and is already spent on something Adrop replaces or complements.
2. Speed: one decision maker, a buying trigger we can see, a sales cycle under a month.
3. Reference value: a logo or a quote that opens the next ten doors (the submission, `docs/VALIDATION.md`).
4. Fit with the product as built: web SDK, Solana devnet now, Seeker holders as the verified audience, x402 funding.

## Candidates
| Candidate | One line |
|---|---|
| A. Web3 marketing agencies | buy media for 5–20 clients at once; need inventory they can resell with a verifiable "human" claim |
| B. Direct advertisers: exchanges, wallets | biggest budgets in crypto; blocked or restricted on Google and Meta for most products |
| C. Direct advertisers: DeFi protocols, infra | pay $2–8 per wallet today, more for a swap or deposit; want on-chain attribution |
| D. Consumer apps and games (Solana, Seeker) | two roles: host (earn 20%) and advertiser (buy installs or quests from other hosts' users) |
| E. AI agents buying reach | programmatic buyers that pay over x402; no human sales cycle, but no budgets of their own yet |
| F. Host apps (supply side) | Seeker dApp Store apps and web games; the customer that makes every other customer possible |

## Method
Desk research, 2026-10-07: agency pricing pages and rankings, HypeLab 2026 benchmarks, NorthPoint "State of
Crypto Marketing 2026", Solana Mobile ecosystem posts, agentic-advertising trade press. No interviews yet; the
interview script below is for the owner's first ten calls. Time box: one session.

## Findings 1: budgets, triggers, decision makers (checked 2026-10-07)
| Segment | Budget today | Buying trigger | Decision maker | Sales cycle | Proof they need before paying |
|---|---|---|---|---|---|
| A. Agencies | retainers $10–15k/month entry, $30–50k full service, token launch $100k+ ([Crypto Traffic Market](https://www.cryptotrafficmarket.com/how-much-does-crypto-marketing-cost/)); 17 agencies in NorthPoint's sample, 7 of 10 named clients claimed by two or more agencies ([NorthPoint 2026](https://northpoint.fi/state-of-crypto-marketing-2026)) | a client launch or a KPI the agency cannot hit with display ("real users", "no bots") | agency media lead or founder | 2–4 weeks: a test budget on one client | a rate card, a sample report (counts and delivery, never addresses), a live demo they can run themselves |
| B. Exchanges, wallets | Coinbase $1.06B marketing in 2025 (SEC filing, NorthPoint); OKX $70M+ Man City deal; 18 of 27 crypto companies never disclosed a number; Google allows only certified exchanges and hardware wallets, blocks the rest ([Flexe.io 2026](https://flexe.io/blog/blockchain-ads/)) | a new market or product launch; a compliance-safe channel for restricted products | growth or performance marketing lead; legal signs off | 2–6 months, procurement and compliance | a brand-safety story (opt-in humans, labelled Sponsored), a pilot with a cap, invoicing in fiat or USDC |
| C. DeFi, infra | cost per wallet $1.86 (best) to $15–40 untargeted; ~60% of teams want CAC under $30, a third under $15; funded projects spend $5–30k/month ([Blockchain App Factory 2026](https://www.blockchainappfactory.com/crypto-marketing-budget-benchmarks), [KOL HQ](https://www.kolhq.com/blog/crypto-marketing-budget)); conversion after an ad: wallet connect 15–25%, swap 0.5–2%, deposit 0.2–0.8% ([HypeLab 2026-03-09](https://www.hypelab.com/blog/on-chain-attribution-wallet-ad-conversions)) | an incentive program, points season or TVL target; the quest platform bill ($5–25 per completion, R-02) | growth lead, often the founder | 2–4 weeks | an audience estimate for their segment (`dex_swap_30d`, "holds X"), a paid-action roadmap (ADR-0003), one case |
| D. Apps and games as advertisers | user acquisition at CPI; on Solana Mobile the store runs quests and SKR incentives, so paid reach is a known cost ([Solana Mobile](https://solanamobile.com/blog/sms-goes-global-and-season-2-wrapup)) | a dApp Store launch, a season | founder | 1–3 weeks | installs or opt-ins from verified Seeker owners, counted |
| E. AI agents | none of their own; today agentic buying runs through PubMatic AgenticOS, Adform's MCP server, IAB AAMP (2026-02-26), with human-set goals and guardrails ([ppc.land](https://ppc.land/agentic-ai-and-the-ad-stack-who-controls-the-buying-layer-now/), [Digiday 2026-05](https://digiday.com/marketing/digiday-programmatic-marketing-summit-may-recap-how-marketers-are-navigating-agentic-ad-buying/)) | an operator points an agent at a goal with a budget | the human behind the agent (segments B–D) | zero once the human decides | a machine-readable rate card and the x402 flow (shipped); an MCP tool later |
| F. Host apps | rewarded video pays the app $0.01–0.02 per view (R-03); Adrop pays the host $0.02 on a $0.10 untargeted view and $0.10–0.20 on a targeted one | a monetisation gap on Seeker (no AdMob for crypto content), a retention feature ("earn USDC in our app") | founder or lead dev | one afternoon to integrate (T23), weeks to decide | a working demo, the SDK README, a fill-rate promise (campaigns exist), store compliance (R-03) |

Supply numbers: 100k+ active Seeker devices, dApp Store from ~700 apps (March 2026) to 1,561 (June 2026)
([SolanaFloor](https://solanafloor.com/news/solana-mobile-june-recap-1-000-apps-publishing-portal-update-and-de-fi-portfolio-tracking),
[Solana Compass](https://solanacompass.com/learn/breakpoint-25/tech-talk-solana-mobile-solana-labs)). Most-used Seeker apps per Solana
Mobile: Jupiter, Moonwalk Fitness, Backpack, Drift, Phantom, LootGo, URNetwork, Sleepagotchi, STEPN GO, Honeyland, Octo Gaming
([Solana Mobile, Seeker Season](https://solanamobile.com/blog/seeker-season-10-dapps-you-should-download-right-now)).

## Findings 2: priority
| Rank | Segment | Why now | Why not first |
|---|---|---|---|
| 1 | F. Host apps on Seeker (3–5 of them) | without supply nothing else sells; every Seeker owner already holds the proof; integration is an afternoon | earns nothing until advertisers come; pick apps whose users are the audience advertisers want (DeFi users: Jupiter, Drift, Backpack users; lifestyle: Moonwalk, Sleepagotchi, LootGo) |
| 2 | C. DeFi and infra protocols on Solana | budgets of $5–30k/month exist, the buyer is the founder, they already pay $5–25 per quest completion and they can read a Merkle root; our `dex_swap_30d` segment is their audience | they will ask for paid actions (swap, deposit) which is ADR-0003, after the deadline; sell views now, actions in Q1 |
| 3 | A. Agencies (R-08) | one agency = many advertisers; they need a human-verified inventory story for clients blocked on Google | they need a rate card, a report and references first; after two direct campaigns |
| 4 | D. Apps and games as advertisers | natural cross-sell to hosts: a host buys installs from other hosts' users | small budgets; wait for 5+ hosts |
| 5 | B. Exchanges and wallets | largest budgets, strongest logo | months of procurement and compliance; a pilot through an agency (A) is the realistic path; ignore as a direct sale for a year |
| 6 | E. Agents | the x402 flow is the demo and the differentiator in the pitch | not a customer; a channel the segments above will use. Add an MCP tool when one of them asks |

## Findings 3: interview script (10 questions, 20 minutes)
1. What did you spend on user acquisition in the last 90 days, and on what channels?
2. What did a new active wallet cost you, and how do you measure "active"?
3. What share of that traffic do you believe was bots or farms? How do you know?
4. Which channels are closed to you (Google, Meta, app stores)? What did you do instead?
5. If you could pay only for views by verified humans in a segment you choose, what would a view be worth to you?
6. Would you pay more for a verified human who then does X (swap, deposit, mint)? What is X worth?
7. Who signs off a $5k test, and what has to be true in the report for the second $5k?
8. (Hosts) What do you earn per 1,000 rewarded video views today, and what would make you switch or add a second SDK?
9. (Hosts) Which store rules or legal questions stop you paying users in USDC?
10. Can we quote you, by name or by role, if the test works? (feeds `docs/VALIDATION.md`)

## Findings 4: first ten targets per segment (channel to reach them)
Owner fills the contact column; sessions do not store personal data here.
| Segment | Targets (first ten) | Channel |
|---|---|---|
| F. Hosts | Moonwalk Fitness, LootGo, Sleepagotchi, STEPN GO, Honeyland, Octo Gaming, URNetwork, Parallel Colony, AFK Heroes, one Seeker-only wallet or social app from the dApp Store top list | Solana Mobile builders Discord and Telegram, dApp Store publisher contacts, X DMs, Breakpoint side events |
| C. DeFi/infra | Jupiter, Drift, Kamino, Marginfi, Raydium, Orca, Jito, Sanctum, Meteora, Wormhole | growth leads on X, their Discord, Superteam, Colosseum network |
| A. Agencies | Coinbound, Lunar Strategy, NinjaPromo, MarketAcross, Single Grain, plus five Solana-native shops from R-08 ([MarketerHire](https://marketerhire.com/blog/best-web3-marketing-agencies), [AP Collective](https://www.apcollective.io/blog/best-web3-marketing-agencies)) | the agency brief PDF (`06-agency-brief.md`), inbound from the landing page |
| D. Apps as advertisers | the hosts above once live | same as F |
| B. Exchanges, wallets | Phantom, Backpack, Solflare, OKX Wallet, Coinbase Wallet (via an agency) | agency pilot only |

## Recommendation
Sell to Seeker host apps first (three live integrations in Q4 2026), then to Solana DeFi protocols with a
$5k capped test at targeted prices, then to agencies with the rate card and the first report. Exchanges and
wallets only through an agency; agents are a channel, not a segment. We give up the biggest logos for a year
and accept that DeFi buyers will push for paid actions (ADR-0003) early. What would change the answer: an
agency with three restricted-product clients asks for a pilot first, or World ID on Base lands and opens EVM
DeFi before Solana hosts reach five.

## Owner decision
2026-10-21: recommendation accepted; Q4 2026–Q1 2027 targets in plan §6 (3 hosts, 2 DeFi tests, 1 agency pilot; Rome = 10 conversations, 5 meetings). Interviews before Rome. Earlier note: owner runs the first five interviews (3 hosts, 2 DeFi) with the script; quotes go to
`docs/VALIDATION.md` (hq #3); R-08 fills the agency column.

## Sources (checked 2026-10-07)
- NorthPoint, State of Crypto Marketing 2026: https://northpoint.fi/state-of-crypto-marketing-2026
- HypeLab, on-chain attribution, 2026-03-09: https://www.hypelab.com/blog/on-chain-attribution-wallet-ad-conversions
- Crypto Traffic Market, crypto marketing cost 2026: https://www.cryptotrafficmarket.com/how-much-does-crypto-marketing-cost/
- Blockchain App Factory, budget benchmarks 2026: https://www.blockchainappfactory.com/crypto-marketing-budget-benchmarks
- KOL HQ, crypto marketing budget: https://www.kolhq.com/blog/crypto-marketing-budget
- Flexe.io, blockchain ads 2026 (Google policy): https://flexe.io/blog/blockchain-ads/
- MarketerHire, best web3 agencies 2026: https://marketerhire.com/blog/best-web3-marketing-agencies
- AP Collective, 25 best web3 agencies 2026: https://www.apcollective.io/blog/best-web3-marketing-agencies
- Solana Mobile, SMS goes global, Season 2: https://solanamobile.com/blog/sms-goes-global-and-season-2-wrapup
- Solana Mobile, Seeker Season 10 dApps: https://solanamobile.com/blog/seeker-season-10-dapps-you-should-download-right-now
- SolanaFloor, June recap 1,000 apps: https://solanafloor.com/news/solana-mobile-june-recap-1-000-apps-publishing-portal-update-and-de-fi-portfolio-tracking
- Solana Compass, Breakpoint 25 Solana Mobile talk: https://solanacompass.com/learn/breakpoint-25/tech-talk-solana-mobile-solana-labs
- ppc.land, agentic AI and the ad stack: https://ppc.land/agentic-ai-and-the-ad-stack-who-controls-the-buying-layer-now/
- Digiday, Programmatic Marketing Summit May 2026: https://digiday.com/marketing/digiday-programmatic-marketing-summit-may-recap-how-marketers-are-navigating-agentic-ad-buying/
