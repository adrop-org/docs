# 05 Business plan

Status: Draft. Built from R-01 (revenue splits) and R-02 (market, competitors, $1M table).
Lines marked **owner** need the owner's numbers; nothing there is invented.

## 1. One paragraph
Adrop is a rewarded-ads SDK that pays verified humans in USDC for qualified attention. An app
drops it in; users opt in with a wallet and one proof of personhood; advertisers fund campaigns
over x402 and buy reach by on-chain behaviour, never wallet lists. Every qualified view pays out
on-chain in one transaction, split viewer / host app / protocol. Solana and the Seeker Genesis
Token first; proof, chain and platform are pluggable.

## 2. Problem
- Web3 user acquisition costs $2–85 per wallet action and most of it is bots and mercenaries
  (R-02, HypeLab 2026). Advertisers cannot tell a human from a farm.
- Apps earn $0.01–0.02 per rewarded video view (US eCPM $10–30) and users earn nothing.
- Pay-the-user models failed on price, not on principle: Brave shared $5.95M with users in six
  years because an impression is worth a fraction of a cent.

## 3. Product and pricing
- Price per qualified view set by the advertiser per campaign. Every viewer is a verified human;
  **targeting sets the price** (R-03): untargeted = every registered identity, $0.10–0.25;
  targeted = a behaviour segment such as `dex_swap_30d`, $0.50–1.00; high-intent segments $1–5.
  "Categories" = segment tags. Demo today: targeted at $0.10; plan: targeted $0.50–1.00, untargeted $0.10.
- Split: protocol share and viewer share are protocol parameters (R-01, candidate B); launch
  70 / 20 / 10, planning case 70 / 10 / 20. Per-host negotiated share on the roadmap.
- Qualified view = registered identity, in the campaign's committed audience, ≥50% visible
  ≥3 s with focus and a pointer event, under the daily cap, attester co-signed. SPEC §2.
- Revenue: protocol share of every paid view. Later: audience estimates over x402 ($0.01 per
  query, stretch), premium segments, per-host terms.
- Roadmap, decided (ADR-0003, R-04): a second price per campaign for a verified **action**
  after the view (on-chain action against the advertiser's program, a Blink signed in the ad slot,
  an in-ad quiz; never a paid click), from a separate action budget in the same escrow. $1–5 per
  action against web3 cost-per-wallet of $2–8. Three prices, one escrow, one verified human.

## 4. Market (R-02)
- Crypto ad spend $1.2B (2025); web3 marketing services $2.1–2.7B; Coinbase alone $247M in Q1 2025.
- Rewarded video is the top mobile format; mobile in-game ad revenue > $50B in 2026.
- Supply of proofs: 150k Seekers, 18M World ID humans.
- Target: $1M protocol revenue = $5M advertiser spend at 20% share, 0.4% of crypto ad spend.
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

## 6. Go-to-market
Customers in order (R-09): Seeker host apps first (supply; three integrations in Q4 2026), then Solana DeFi and
infra protocols with a $5k capped test at targeted prices (they pay $5–25 per quest completion today and
$1.86–40 per wallet), then web3 agencies with the rate card and the first report (R-08). Exchanges and wallets
only through an agency for a year; AI agents are a channel the others use, not a segment. Interview script and
first ten targets per segment: R-09.
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

Cost lines to keep in view (**owner** to confirm): fee payer pays ~0.002 SOL once per new viewer
(USDC account creation) plus ~0.000005 SOL per claim; Helius
plan; facilitator fee if any on mainnet; attester hosting. 10k new verified viewers ≈ 20 SOL of rent.

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
## 8. Roadmap (from `04-roadmap.md`, business view)
- 2026-10: hackathon submission, devnet, SGT proof, web SDK, x402 funding.
- **owner**: mainnet date, first paying advertiser, World ID proof, EVM settlement, Unity package.
- After the deadline (ADR-0003): paid actions (`pay_action`, action budget, `/actions`), built
  with the Config split change (R-01 B) in one devnet reset, about two days.

## 9. Team, costs, funding
- **owner**: team, monthly burn, infra cost (Hetzner cluster, Helius, facilitator fees), legal
  (ad disclosure, payouts, stablecoin handling by jurisdiction), funding ask and use of funds.

## 10. Risks
- Advertisers will not pay $1 for a verified view → test with 3 campaigns at $0.25 / 0.50 / 1.00.
- Identity supply too thin on Seeker alone → World ID as second proof (ADR-0002).
- W3AP's distribution in SEA and games → differentiate on identity, USDC, audit; do not race on Unity first.
- iOS native and Steam are closed to crypto-paying ad SDKs (R-03) → web SDK for iOS, Epic for PC; Google
  Play policy may tighten → keep the Solana dApp Store and web as channels that need no store approval.
- No wallet-only tier: it would reintroduce the farms the personhood gate removes. Cheap reach is
  "untargeted verified humans", not unverified wallets (R-03).
- Attester is a single trusted key → multi-attester or TEE on the roadmap.
- Paid actions are incentivised traffic: advertisers discount it, and paying someone to make a financial
  transaction can be an inducement (UK FCA cryptoasset promotion rules ban investment incentives) →
  advertiser-set thresholds and hold windows; **owner** + counsel before on-chain actions on financial products (R-04).
- Regulatory: paying users in stablecoins and ad disclosure rules differ by country → **owner** + counsel.
