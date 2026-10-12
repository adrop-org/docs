# R-01: How is advertiser money split today, and who should set Adrop's split?

Date opened: 2026-10-06. Status: Open
Feeds: ADR on payout split (configurable protocol share, viewer/host split)

## Question
Which party sets the viewer / host / protocol split, and at what level (program constant,
admin config, per campaign, per host), given how ad money is split in today's market.

## Criteria
1. Hosts have a reason to integrate: their absolute take per view beats what rewarded ads pay them now.
2. Viewers have a reason to opt in and claim: their take is visible and meaningful.
3. Protocol take is in line with what networks keep, and changeable without a redeploy.
4. Advertisers see one price per qualified view; they do not negotiate splits.
5. Cheap to build before 2026-10-11.

## Findings: where an advertiser's dollar goes today
Figures from public statements and industry studies as remembered on 2026-10-06; verify each
link before any of this is published (pitch, README).

| Channel | Advertiser → | Intermediary keeps | Publisher / app gets | User gets |
|---|---|---|---|---|
| Open-web programmatic display (ISBA/PwC 2020, UK) | agency, DSP, verification, SSP | ~49% incl. ~15% untraceable | ~51% | 0 |
| Programmatic, ANA 2023 (US) | same chain + made-for-advertising sites | roughly two thirds lost to fees and waste | ~a third effective | 0 |
| Google AdSense | Google | 32% (content), 49% (search) | 68% / 51% | 0 |
| YouTube Partner Program | Google | 45% | 55% to creator | 0 |
| Meta in-stream video ads | Meta | 45% | 55% to creator | 0 |
| Mobile rewarded video (AdMob, AppLovin, Unity Ads) | network / mediation | share not published, order of 30% | the rest; eCPM $10–30 US → ~$0.01–0.02 per view to the app | in-game currency only, paid by the app |
| Brave Ads (opt-in notification ads) | Brave | 30% | – (no publisher) | 70%, in BAT, a few $ a month |
| App stores (purchases, benchmark for platform take) | Apple / Google | 30% (15% small business) | 70–85% | 0 |
| Web3 quests (Galxe, Layer3, Zealy) | platform | undisclosed fee | – | tokens or points for completing actions |
| Web3 user acquisition (your DEMO_SCRIPT figure, unsourced) | – | – | – | advertisers pay $2–8 per verified wallet action |

Pattern: the network keeps 30–45%, the place that shows the ad gets 50–70%, the user gets
nothing. The two exceptions that pay the user: Brave (70%, failed on value per impression, not
on the split) and rewarded video (user paid indirectly, in-game, by the app).

## Findings: who sets the split today
- Networks fix the publisher share for everyone (AdSense 68%, YouTube 55%). Not per campaign.
- Advertisers never set splits; they set a bid or a price per outcome (CPM, CPC, CPA).
- Publishers negotiate only floor prices (minimum CPM) and, for large ones, a private rev-share.
- So "advertiser sets viewer/host split per campaign" has no precedent, and the advertiser
  bears none of its consequences (splits change who is motivated, not what the advertiser pays).

## What this means for Adrop's 70 / 20 / 10
- Protocol 10%: the lowest take in the table. Networks keep 30–45%. Room to raise later; keep it
  admin-settable, not a constant.
- Host 20%: looks small as a percentage, but compare absolute money. At $0.10 per qualified view
  the host gets $0.02, already at the top of rewarded-video payouts per view. At web3 CPA prices
  ($2–8 per wallet action, if the DEMO_SCRIPT figure holds) the host gets $0.40–1.60 per view,
  20–80× any ad network. The percentage is not the host's problem; the price per view is.
- Viewer 70%: the differentiator. Brave proved users accept 70% as fair; what killed Brave Ads
  was ~$0.001 per impression. Adrop sells a verified wallet action, not an impression.

## Candidates for where the split lives
| Candidate | One line | Criteria |
|---|---|---|
| A. Program constants (today) | 7000/2000/1000 bps in `pay_view.rs`; change = program upgrade | fails 3 (redeploy) |
| B. Config fields, admin-set | `viewer_bps`, `protocol_bps` in Config; host = remainder; `set_split` admin ix | meets 1–5; one layout change, devnet reset |
| C. Per-campaign, advertiser-set | `viewer_share` on `POST /campaigns`, stored on Campaign | meets 5; fails 4 and has no market precedent |
| D. Per-host, host-set | host registers a minimum share; roadmap with host registry | meets 1 best; fails 5 |

## Recommendation
B now: both shares in Config, set by the admin key, defaults 70/20/10, read by `pay_view` at
claim time (a campaign funded under one split pays under the current split; acceptable for the
hackathon, snapshot-on-campaign is a one-line follow-up). D is the real market structure
(publishers negotiate their share with the network) and goes on the roadmap with the host
registry. C is dropped: advertisers buy a price per qualified view, nothing else.
What would change the answer: evidence that hosts refuse 20% at Adrop's price points.

## Owner decision
Pending.
