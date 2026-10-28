# 05 Business plan

Status: Draft. Built from R-01 (revenue splits), R-02 (market, competitors, $1M table) and R-20 (cost per view, profitability matrix, 2026-10-21).
Lines marked **owner** need the owner's numbers; nothing there is invented.

## 1. One paragraph
Adrop is the rail between an advertiser's budget and a verified person's attention. An app drops in one SDK; a user opts in with a
wallet and one proof of personhood; an advertiser, an agency or an AI agent funds a campaign into an on-chain contract and buys
reach by on-chain behaviour, never wallet lists. Every qualified view, and every verified action after it, pays out from the
contract in one transaction: 50% to the person, 20% to the app, 30% to Adrop. Adrop never holds the money, never builds a
profile, and never pays a chain fee; the campaign does. Solana and the Seeker Genesis Token first; proof, chain and platform are
pluggable. (§1–§2 approved by the owner 2026-10-21.)

## 2. Problem
- Web3 user acquisition costs $2–85 per wallet action and most of it is bots and mercenaries (R-02, HypeLab 2026). Advertisers cannot
  tell a human from a farm, and nobody sells them one: every network that targets by wallet is a profile collector that pays
  publishers only (R-18).
- Apps earn 1.5¢ per rewarded video view and the user earns nothing (US eCPM $10–30). The people whose attention is sold are the
  only party not paid.
- Pay-the-user models failed on price, not on principle: Brave shared $5.95M with users in six years because an impression is
  worth a fraction of a cent. A verified human's qualified view is worth dollars, not cents (quest completions $5–25, wallet CPA
  $2–8), and that price pays everyone.

## 3. Product and pricing
- Price per qualified view set by the advertiser per campaign. Every viewer is a verified human;
  **targeting sets the price** (R-03): untargeted = every registered identity, $0.10–0.25;
  targeted = a behaviour segment such as `dex_swap_30d`, $0.50–1.00; high-intent segments $1–5.
  "Categories" = segment tags. Demo today: targeted at $0.10; plan: targeted $0.50–1.00, untargeted $0.10.
- Split: protocol share and viewer share are protocol parameters (R-01, candidate B). Owner 2026-10-21: **viewer 50 / host 20 /
  protocol 30**; the hackathon's 70/20/10 is a demo setting. Per-host negotiated share on the roadmap.
- Qualified view = registered identity, in the campaign's committed audience, ≥50% visible
  ≥3 s with focus and a pointer event, under the daily cap, attester co-signed. SPEC §2.
- Revenue: protocol share of every paid view. Later: audience estimates over x402 ($0.01 per
  query, stretch), premium segments, per-host terms.
- Roadmap, decided (ADR-0003, R-04): a second price per campaign for a verified **action**
  after the view (on-chain action against the advertiser's program, a Blink signed in the ad slot,
  an in-ad quiz, a host postback; never a paid click, clicks are reported free as a metric), from a separate action budget in
  the same escrow. Floor **$1.00** per action (owner 2026-10-21), advertiser sets anything above with its own thresholds and hold
  windows; same 50/20/30 split as views; $1–5 against web3 cost-per-wallet of $2–8. Three prices, one escrow, one verified human.

## 4. Market (R-02)
- Crypto ad spend $1.2B (2025); web3 marketing services $2.1–2.7B; Coinbase alone $247M in Q1 2025.
- Rewarded video is the top mobile format; mobile in-game ad revenue > $50B in 2026.
- Supply of proofs: 150k Seekers, 18M World ID humans.
- Target: $1M protocol revenue = $3.3M advertiser spend at 30% share (R-01, 2026-10-21), 0.28% of crypto ad spend.
- Supply bound (R-20 sub-question 5): views/day ≤ verified identities × claims/day. 10k views/day needs 5k active verified viewers,
  100k needs 50k: 3% and 33% of today's 150k Seekers, or a rounding error of World ID's 18M. Growth beyond Solana needs the second proof.
- Gaming is the host side, not the buyer side: mobile game ad revenue > $12B, 56% of games monetise with ads, rewarded video pays the app
  1.5¢ a view and the player nothing; Adrop's floor pays the app 5¢ and the player 12.5¢. For the SiGMA / AIBC crowd (iGaming, affiliates)
  the buyer story is the same as DeFi's: verified humans at a price per view, no bots, no wallet lists.
- Buyers (R-09): funded crypto projects spend $5–30k a month on marketing; 60% want CAC under $30; agencies run
  $10–50k monthly retainers; exchanges spend most (Coinbase $1.06B in 2025) but buy through agencies and procurement.

## 5. Competition (R-02 table)
Direct: W3AP (blocksky Inc., Tokyo): Unity/Web/RN SDK shipped 2025-06, pays in its own
USD-pegged token on Base, "verified users" undisclosed, SEA-first, SBI-backed. Adjacent: Brave
Ads, Mode Mobile (web2 pay-for-attention), Adsgram (Telegram), wallet-targeting networks
(Blockchain-Ads, HypeLab, Slise), quest platforms (Galxe, Layer3). Incumbents in games: Unity
Ads, AdMob, AppLovin.
Adrop's edge: personhood enforced on-chain (one proof, one identity), USDC payout, auditable
split, agent-fundable campaigns (x402), verifiable audience commitments, chain-agnostic.
R-18 matrix (15 rivals, six fields, 2026-10-12) and R-19: **wallet targeting and paying the viewer never meet.** Everyone who targets by
wallet (Blockchain-Ads, Addressable, Slise, Spindl, HypeLab) is a profile collector that pays publishers only; everyone who pays the
viewer (Brave, Mode, W3AP, Adsgram apps) targets by context or nothing. Adrop is alone in "wallet-level audience + pays the viewer + holds
no profile". Three names to use: **Blockchain-Ads** when an agency asks "why not just buy wallets" (BVI wallet DMP, $10k minimum, cannot
pay a viewer or prove a human); **Hakuhodo × Tools for Humanity × LG** as the thesis validated by a $10B agency (World App PoC, Japan,
summer 2025: 10 advertisers, 3,500 users, CTR up 7× with incentives) and the one to watch, single app, no SDK, no wallet audiences;
**Spindl** (Coinbase) as the only wallet-keyed in-app delivery, inside Coinbase's own apps, nothing on Solana. Positioning sentence:
*Adrop is the rail between an advertiser's budget and a verified person's attention: the contract pays the person and the app, the
advertiser gets proof, nobody gets a profile.*

## 6. Go-to-market
Customers in order (R-09): Seeker host apps first (supply; three integrations in Q4 2026), then Solana DeFi and
infra protocols with a $5k capped test at targeted prices (they pay $5–25 per quest completion today and
$1.86–40 per wallet), then web3 agencies with the rate card and the first report (R-08). Exchanges and wallets
only through an agency for a year; AI agents are a channel the others use, not a segment. Interview script and
first ten targets per segment: R-09.
First quarter after Rome, Nov 2026 – Jan 2027 (owner 2026-10-21): **3 Seeker host apps live** with the SDK (Moonwalk, LootGo,
Sleepagotchi first); **2 Solana protocols on a $5k capped test** at targeted prices (Jupiter, Drift, Kamino, Marginfi); **1 agency
pilot** after the first campaign report, February at the earliest. AIBC Rome (02–05 Nov) is the field test for buyers: 10 advertiser
or agency conversations, 5 follow-up meetings, logged (`source/AIBC_ROME_CHECKLIST.md`). The five R-09 interviews (3 hosts, 2 DeFi)
happen before Rome and feed the sent deck and `docs/VALIDATION.md`. Why these counts: $10k/month profit is 2–6 advertisers at $15k
carried by 1,600–4,000 verified viewers (§7.11), i.e. two or three hosts with a few thousand daily users plus the first two buyers.
1. Solana (now): Seeker dApp store apps; every Seeker owner already holds the proof. Hackathon
   demo and devnet deployment 2026-10. **owner**: first 3 host apps to approach (R-09 list: Moonwalk, LootGo, Sleepagotchi, ...).
2. Base / EVM (next): Coinbase Verifications and World ID as proofs; same server, EVM settlement.
3. Games: Unity package on **Android** (Google Play with the blockchain-content declaration, Solana
   dApp Store without conditions), **Epic Games Store** and web. Not iOS native (Apple 3.1.5(v)
   forbids crypto for completing tasks) and not Steam (crypto ban); iOS players use the web SDK
   in a browser or wallet. Proofs there: World ID, or Play Integrity / App Attest as a weaker device-level proof. Meets W3AP with USDC and a real sybil gate. R-03.
4. Telegram / TON: volume play, later, once a proof exists there.

## 7. Unit economics and scenarios
Model: protocol revenue = daily earners × claims per day × 365 × price × protocol share.
Viewer share 50–70%, protocol 10–30%, host the rest. Tables generated by `research/model.py`
(`python3 model.py csv data` also writes `research/data/*.csv` for Excel). Change inputs there,
not here. Host benchmark: rewarded video pays the app $0.015 per view (US eCPM $10–30).

### 7.1 Split options: what each party gets per view and per day

| split viewer host protocol | price per view | viewer per view | viewer per day 2 claims | viewer per year | host per view | host vs rewarded video x | protocol per view |
|---|---|---|---|---|---|---|---|
| 70/20/10 | $0.25 | $0.17 | $0.35 | $128.00 | $0.05 | 3× | $0.03 |
| 70/20/10 | $0.50 | $0.35 | $0.70 | $255.00 | $0.10 | 7× | $0.05 |
| 70/20/10 | $1.00 | $0.70 | $1.40 | $511.00 | $0.20 | 13× | $0.10 |
| 60/20/20 | $0.25 | $0.15 | $0.30 | $110.00 | $0.05 | 3× | $0.05 |
| 60/20/20 | $0.50 | $0.30 | $0.60 | $219.00 | $0.10 | 7× | $0.10 |
| 60/20/20 | $1.00 | $0.60 | $1.20 | $438.00 | $0.20 | 13× | $0.20 |
| 50/25/25 | $0.25 | $0.12 | $0.25 | $91.00 | $0.06 | 4× | $0.06 |
| 50/25/25 | $0.50 | $0.25 | $0.50 | $182.00 | $0.12 | 8× | $0.12 |
| 50/25/25 | $1.00 | $0.50 | $1.00 | $365.00 | $0.25 | 17× | $0.25 |
| 50/30/20 | $0.25 | $0.12 | $0.25 | $91.00 | $0.07 | 5× | $0.05 |
| 50/30/20 | $0.50 | $0.25 | $0.50 | $182.00 | $0.15 | 10× | $0.10 |
| 50/30/20 | $1.00 | $0.50 | $1.00 | $365.00 | $0.30 | 20× | $0.20 |
| 70/10/20 | $0.25 | $0.17 | $0.35 | $128.00 | $0.03 | 2× | $0.05 |
| 70/10/20 | $0.50 | $0.35 | $0.70 | $255.00 | $0.05 | 3× | $0.10 |
| 70/10/20 | $1.00 | $0.70 | $1.40 | $511.00 | $0.10 | 7× | $0.20 |

### 7.2 Three scenarios, targeted campaigns only, steady-state year

| metric | Worst | Realistic | Best |
|---|---|---|---|
| assumes | Seeker only, advertisers pay rewarded-video prices, one claim of each a day | Solana + Base, World ID as second proof, 3–5 host apps, Android/Unity live | 20+ hosts incl. Unity games on Android/Epic, advertisers compete for verified humans |
| price_per_view | $0.10 | $0.50 | $1.00 |
| daily_earners | 2.0k | 10.0k | 30.0k |
| claims_per_day | 1 | 2 | 3 |
| split | 70/20/10 | 60/20/20 | 50/30/20 |
| views_per_year | 730.0k | 7.3M | 32.9M |
| advertiser_spend_per_year | $73k | $3.65M | $32.85M |
| protocol_revenue_per_year | $7k | $730k | $6.57M |
| paid_to_viewers_per_year | $51k | $2.19M | $16.43M |
| paid_to_hosts_per_year | $15k | $730k | $9.86M |
| one_viewer_earns_per_year | $26.00 | $219.00 | $548.00 |
| one_host_earns_per_1000_views | $20.00 | $100.00 | $300.00 |
| share_of_2025_crypto_ad_spend_pct | 0.01% | 0.3% | 2.74% |
| earners_pct_of_150k_seekers | 1% | 7% | 20% |

### 7.3 Protocol revenue per year by price and daily earners (20% share, 2 claims a day)

| price per view | earners 2000 | earners 5000 | earners 10000 | earners 30000 | earners 100000 |
|---|---|---|---|---|---|
| $0.10 | 29.2k | 73.0k | 146.0k | 438.0k | 1.5M |
| $0.25 | 73.0k | 182.5k | 365.0k | 1.1M | 3.6M |
| $0.50 | 146.0k | 365.0k | 730.0k | 2.2M | 7.3M |
| $1.00 | 292.0k | 730.0k | 1.5M | 4.4M | 14.6M |
| $2.00 | 584.0k | 1.5M | 2.9M | 8.8M | 29.2M |

### 7.4 Daily earners needed for $1M protocol revenue (2 claims a day)

| split viewer host protocol | at 0.25 | at 0.50 | at 1.00 | viewer per year at 0.50 |
|---|---|---|---|---|
| 70/20/10 | 54.8k | 27.4k | 13.7k | $255.00 |
| 60/20/20 | 27.4k | 13.7k | 6.8k | $219.00 |
| 50/25/25 | 21.9k | 11.0k | 5.5k | $182.00 |
| 50/30/20 | 27.4k | 13.7k | 6.8k | $182.00 |
| 70/10/20 | 27.4k | 13.7k | 6.8k | $255.00 |

### 7.5 Ramp, three years, 60/20/20, untargeted campaigns from year 2

| year | markets | daily earners | targeted price | targeted claims per day | untargeted price | untargeted claims per day | views | advertiser spend | protocol revenue | viewers paid | hosts paid |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Solana mainnet, Seeker apps | 3.0k | $0.25 | 2 | $0.00 | 0 | 2.2M | $548k | $110k | $328k | $110k |
| 2 | + Base, World ID, Android | 10.0k | $0.50 | 2 | $0.10 | 2 | 14.6M | $4.38M | $876k | $2.63M | $876k |
| 3 | + Unity games, Epic | 30.0k | $0.75 | 2 | $0.15 | 2 | 43.8M | $19.71M | $3.94M | $11.83M | $3.94M |

### 7.6 Targeting tiers and suggested prices (every viewer is a verified human)

| tier | audience | price low | price high | campaign freq cap | host per view at low vs rewarded video x | viewer per view at low 60pct |
|---|---|---|---|---|---|---|
| Untargeted | every registered identity (verified human, no segment) | $0.10 | $0.25 | 3 | 1.3× | $0.06 |
| Targeted | a behaviour segment, e.g. dex_swap_30d | $0.50 | $1.00 | 1 | 6.7× | $0.30 |
| High-intent | narrow segment, e.g. >$10k DeFi volume 30d, NFT collector | $1.00 | $5.00 | 1 | 13.3× | $0.60 |

### 7.7 Three scenarios with untargeted campaigns added (same humans, more claims)

| metric | Worst | Realistic | Best |
|---|---|---|---|
| daily_earners | 2.0k | 10.0k | 30.0k |
| targeted_price | $0.10 | $0.50 | $1.00 |
| targeted_claims_per_day | 1 | 2 | 3 |
| untargeted_price | $0.03 | $0.10 | $0.25 |
| untargeted_claims_per_day | 1 | 2 | 2 |
| split | 70/20/10 | 60/20/20 | 50/30/20 |
| targeted_ad_spend | $73k | $3.65M | $32.85M |
| untargeted_ad_spend | $22k | $730k | $5.47M |
| total_ad_spend | $95k | $4.38M | $38.33M |
| protocol_revenue | $9k | $876k | $7.67M |
| protocol_revenue_from_untargeted_pct | 23% | 17% | 14% |
| viewers_paid | $66k | $2.63M | $19.16M |
| hosts_paid | $19k | $876k | $11.50M |
| one_viewer_earns_per_year | $33.00 | $263.00 | $639.00 |

### 7.8 What the tables say
- **Price beats share.** 50% of $1.00 pays the viewer $0.50 a view; 70% of $0.50 pays $0.35.
  The viewer's income is set by the price advertisers pay, not by the split. Sell the price.
- **The host is fine at 20% from $0.25 upward**: $0.05 a view is 3× rewarded video, $0.10 at $0.50
  is 7×. Below $0.25 the host's advantage over Unity Ads disappears; $0.25 is the floor for verified.
- **10% protocol share doubles the volume needed.** At $0.50, $1M needs 27k daily earners at 10% but
  14k at 20%. 20% is still below every ad network (30–45%, R-01).
- **Worst case is irrelevance, not a loss**: $73k of ad spend, $7k to the protocol. It happens if
  the price stays at rewarded-video levels, which is the first risk to test with real campaigns.
- **Realistic case, verified only** (60/20/20, $0.50, 10k daily earners, 2 claims): $730k protocol
  revenue on $3.65M ad spend; a viewer earns $219 a year; a host $100 per 1,000 views.
- **Untargeted campaigns add about a fifth** (7.7): the same verified humans also see cheap untargeted
  ads ($0.10, two a day). Realistic: $876k protocol revenue on $4.38M ad spend, 17% from untargeted.
  No new population, no new fraud surface: every viewer is still a verified human (R-03).
- **$1M protocol revenue** lands in year 2 of the ramp (7.5) with 10k daily earners on Solana + Base.
- **A paid action layer adds 7–18%** (7.10) and takes the realistic case to $1.01M. It matters more for
  the pitch than for revenue: it is the line advertisers already budget (CPA), and it turns a $0.30 view
  into a $2–3 event for the viewer (R-04).

### 7.9 Suggested splits and prices
| When | Split v/h/p | Why |
|---|---|---|
| Hackathon and launch | 70/20/10 | user-first story, matches pitch and Brave's 70%; both shares as Config parameters (R-01) |
| Mainnet plan case | 60/20/20 | protocol sustainable at half the volume; viewer still $219/yr at $0.50 |
| Games / distribution push | 50/30/20 | host 30% = $0.30 a view at $1, 20× rewarded video, to win Unity studios from W3AP |
| Floors | viewer ≥ 50%; host ≥ 20%; targeted price ≥ $0.25; untargeted price ≥ $0.10 | below these one party stops showing up |

Cost lines, corrected 2026-10-21 (R-20): the hackathon code also locks 0.00122428 SOL (≈ 13¢) of `Impression` rent per paid
view, paid by our fee payer, never returned; this line was missing here. ADR-0006: that rent goes, and every chain cost of a campaign
(fees, priority fees, the viewer's 16¢ USDC account) is funded by the campaign creator, host or viewer, never by Adrop. Remaining
Adrop costs: Helius plan, servers, team. Full matrix: §7.11.

### 7.10 Three scenarios with a paid action layer added (R-04, ADR-0003)
Assumes paid actions at 1 / 3 / 5% of targeted views and $1 / $3 / $5 per action (R-04 findings 4);
both are guesses until the first real campaigns.

| metric | Worst | Realistic | Best |
|---|---|---|---|
| daily_earners | 2.0k | 10.0k | 30.0k |
| targeted_views_per_year | 730.0k | 7.3M | 32.9M |
| price_per_action | $1.00 | $3.00 | $5.00 |
| actions_pct_of_targeted_views | 1% | 3% | 5% |
| actions_per_year | 7.3k | 219.0k | 1.6M |
| action_spend | $7k | $657k | $8.21M |
| view_spend_from_7_7 | $95k | $4.38M | $38.33M |
| total_ad_spend | $102k | $5.04M | $46.54M |
| protocol_revenue | $10k | $1.01M | $9.31M |
| protocol_revenue_from_actions_pct | 7% | 13% | 18% |
| viewers_paid | $72k | $3.02M | $23.27M |
| hosts_paid | $20k | $1.01M | $13.96M |
| one_viewer_earns_per_year | $36.00 | $302.00 | $776.00 |
| one_viewer_extra_from_actions_per_year | $3.00 | $39.00 | $137.00 |
### 7.11 Real-life profitability (R-20, `research/cost_model.py`, 2026-10-21)
Owner direction: the $0.10 demo price is out of every model; the business is views plus paid actions (ADR-0003 kinds).
Three mixes, protocol share 30% (owner 2026-10-21), chain fees on the campaign (ADR-0006):

| Mix | Views | Actions | Gross $/1k views | Protocol $/1k |
|---|---|---|---|---|
| Launch | 60% untargeted $0.25, 40% targeted $0.50 | 1% of targeted @ $1 | 354 | 106 |
| Growth | 40% $0.25, 50% targeted $0.75, 10% high-intent $1.50 | 3% @ $3 | 679 | 204 |
| Scale | 30% $0.25, 50% targeted $1.00, 20% high-intent $2.50 | 5% @ $5 | 1,250 | 375 |

- **Adrop has no variable cost.** Profit = 30% × ad spend − team − infra; infra (Helius, servers) is under $1.3k/month even at
  1M views/day. Chain fees, paid by the campaign, are 0.1–2% of ad spend.
- **$10k/month profit = $34k/month of ad spend with no payroll, $84k with a $15k team**: 2 to 6 advertisers at $15k/month
  (R-09 range $5–30k). The mix only sets how many views and viewers carry that spend: Launch 95k views/month from ~1,600
  verified viewers claiming twice a day; Scale 27k views from ~450.
- **Break-even on a $15k team**: 4,700 views/day (Launch), 2,500 (Growth), 1,300 (Scale). On $40k: 12,600 / 6,500 / 3,600.
- **Actions move the number more than price**: Launch → Growth doubles protocol revenue per 1,000 views, half of it from 3% of
  targeted views converting at $3. Targeted and action-heavy campaigns cut the viewers needed for the same spend by 3–4×.
- **The ceiling is sales and supply, not tech**: 10k views/day = $106k/month of Launch-mix spend = 7 advertisers, and 5k active
  verified viewers; 100k/day = $1M/month and 50k viewers. Assumptions to replace with owner numbers: team tiers, mixes, action
  rates, share, average advertiser.

## 8. Roadmap (from `04-roadmap.md`, business view)
- 2026-10: hackathon submission, devnet, SGT proof, web SDK, x402 funding.
- **owner**: mainnet date, first paying advertiser, World ID proof, EVM settlement, Unity package.
- After the deadline (ADR-0003): paid actions (`pay_action`, action budget, `/actions`), built
  with the Config split change (R-01 B) in one devnet reset, about two days.

## 9. Team, costs, funding
- Break-even and the $10k-profit line by team size: §7.11 and R-20 Tables 3 and 5. The only Adrop cost that scales is people.
- Owner, 2026-10-21: **team = the owner alone**, full time, no salary drawn; Milan Volarević as Marketing Advisor (deck). **Burn ≈ $10/month**
  (share of the operator's Hetzner cluster; Helius free tier). **No entity yet**; jurisdiction after R-16 and counsel. **Raise: wanted,
  undecided** on instrument, amount and valuation; owner asked for help, see §9.1. **Use of funds: partner integrations first**
  (fiat-to-USDC partner per ADR-0007, World ID, Unity/Android SDK, the first three host apps), hires second.
- **owner** (still open): monthly burn once a salary is drawn, infra cost (Hetzner cluster, Helius, facilitator fees), legal
  (ad disclosure, payouts, stablecoin handling by jurisdiction), funding ask and use of funds.

### 9.1 Raise options (2026-10-21, for the owner's decision)
Stage: solo founder, working prototype on devnet, no entity, no revenue, burn ≈ $10/month. Use of funds: partner integrations.
What the money has to buy, from the plan: the fiat-to-USDC partner (ADR-0007), World ID as second proof, the Unity/Android SDK,
three host integrations, and the owner's time until the first $10k/month (§7.11: $34k/month of ad spend, 2 advertisers, solo).

| Option | Size | Terms seen (checked 2026-10-21) | Fits because | Cost |
|---|---|---|---|---|
| A. Grants first | $1–10k per grant | Superteam / Solana Foundation instagrants, $1–10k, decided in days (superteamdao.notion.site) | no entity needed, no dilution, pays for one integration each | small, repeated applications; no runway |
| B. Colosseum accelerator | $250k pre-seed | standard offer to hackathon winners; SAFE + token warrant or Colosseum's STAMP; equity % not published (blog.colosseum.com, solanacompass.com) | the submission is in; 8 weeks, investor demo day, Solana network | acceptance under 1% of entrants; decided by the hackathon result, not by us |
| C. Pre-seed SAFE from angels and Solana funds | $150–400k | post-money SAFE, cap set by comparable pre-revenue Solana pre-seeds | 12–18 months: owner salary, one engineer, the integrations, sales | needs an entity first, a lead, and traction lines (hosts live, first paid campaign) |
| D. Bootstrap to $10k/month | $0 | — | §7.11 says two advertisers and two hosts get there | slow without partner integrations; the owner alone does sales, code and ops |

Suggested order: A now (one grant per integration), B if the hackathon result opens it, C only after the first paid campaign and
with an entity, D as the floor. Numbers for the Rome lounge: "pre-seed, $500–600k (18 months), SAFE, use of funds audit, three developers,
marketing, partner integrations; not raising today, opening in Q1 2027 after the first paid campaigns". Owner 2026-10-21: accepted, order A → B → C, D as floor. Owner 2026-10-28: raise $500–600k, Delaware C-corp to be opened.

## 10. Risks
Re-ranked 2026-10-21 after R-20, ADR-0006 and ADR-0007; top first.
1. **Sales, not tech, is the bottleneck.** Profit is 30% of ad spend minus people; $10k/month needs 2–6 advertisers and a solo founder
   doing sales, code and ops → the Q4–Q1 targets in §6, Rome as the field test, the first hire is sales-side or a partner-integrations engineer so the owner sells.
2. **Supply is bounded by verified identities.** 10k views/day = 5k active Seeker viewers (3% of all Seekers); 100k = a third of them → World ID as
   second proof (ADR-0002) before the Growth mix; host apps chosen for daily active users, not logos.
3. **Advertisers will not pay the floors** ($0.25 / $0.50 / $1.00, actions $1) → the two $5k capped tests price-discover; floors are
   config, not code.
4. **The money path for invoice payers depends on a partner** (ADR-0007) → until the fiat-to-USDC partner is live, only USDC-holding
   buyers and agencies can fund; pick the partner in R-21 before the agency pilot.
5. **The per-view rent and the fee-payer design must change before mainnet** (ADR-0006): today's code loses 13¢ a view → devnet reset
   with ADR-0005, SOL-holding mechanics decided in the SPEC first.
6. **Key-person and entity risk**: one person, no company → entity after R-16 and counsel; runbooks and the public repo as the bus-factor hedge;
   grants and Colosseum before a SAFE (§9.1).
7. **A $10B agency already validated the thesis** (Hakuhodo × Tools for Humanity × LG, World App, Japan) and could commercialise with World ID
   distribution first → Adrop's edge is the SDK for any app plus wallet-level audiences; ship World ID support before they ship an SDK.
8. **Attester is a single trusted key** → multi-attester or TEE on the roadmap (R-20 criterion 2, ADR-0005 C2/C5).
9. **Paid actions are incentivised traffic** and paying for financial transactions can be an inducement (UK FCA) → advertiser-set thresholds
   and hold windows; owner + counsel before actions on financial products (R-04).
10. **Regulatory**: stablecoin payouts to users, ad disclosure, KYC/tax thresholds differ by country → owner + counsel (R-16); viewer payouts
    stay small and disclosed.
11. **Platform policy**: iOS native and Steam closed to crypto-paying SDKs; Google Play may tighten → web SDK for iOS, Epic for PC, Solana
    dApp Store and web need no approval (R-03).
12. **W3AP's distribution in SEA and games** → differentiate on identity, USDC and audit; do not race on Unity first.
Kept as a rule, not a risk: no wallet-only tier; cheap reach is untargeted verified humans (R-03).
