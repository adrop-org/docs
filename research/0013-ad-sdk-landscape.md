# R-13: How many ad SDKs are there, and how widely are they used?

Date opened: 2026-10-10. Status: Done 2026-10-10 (facts); owner reads the "Implications" section
Feeds: pitch (`source/PITCH_NOTES_VOLAREVIC.md`, the reviewer's "competition" and "distribution" points), R-02 (market and
competitors), R-09 (host apps as first customers), a later decision on a mediation adapter.

## Question
R-02 compared Adrop only with networks that pay the viewer. How big is the whole field of ad SDKs that apps already embed,
and what does that mean for Adrop's place in it?

## Criteria
1. Counts from a source that scans the stores, dated, not vendor claims.
2. Both stores, Google Play and the Apple App Store.
3. Says whether any of the big SDKs pays the viewer.

## Method
42matters SDK analysis (scans store binaries; pages updated 2026-10-08 and 2026-10-10), cross-checked with AppBrain
(scans every Play APK; updated 2026-10-09). Free public pages only; the full 42matters SDK list sits behind a paid API.
- https://42matters.com/sdk-analysis/top-ad-networks-sdks (Android, top 20)
- https://42matters.com/sdk-analysis/app-store/top-ad-networks-sdks (iOS, top 20)
- https://42matters.com/google-play-statistics-and-trends , https://42matters.com/ios-apple-app-store-statistics-and-trends (store totals)
- https://www.appbrain.com/stats/libraries/ad-networks (Android, top 50)

## Findings

### How many
- **No public total.** 42matters tracks 2,300+ SDKs across all categories; AppBrain publishes a ranked list of **50 ad
  network SDKs**, and its tail is tiny (#50, Fyber: 0.05% of apps). The field that matters is about **20 SDKs**.
- **Store size (42matters, 2026-10-10):** Google Play 2.61M apps; App Store 2.71M apps.
- **Apps with at least one ad SDK:** Android ≈ **784k** (30% of Play), derived from AdMob = 674.98k apps = 86.13% of the
  ad-SDK apps. iOS ≈ 592k (22%), but 42matters counts Apple's AppTrackingTransparency in this category, so the real iOS
  figure is lower.
- **Apps stack them.** On Android the top-20 shares add up to ~297%, so an app that shows ads carries about **3** of these
  SDKs. Weighted by downloads the sum is ~600%: popular apps carry about **6**, through mediation (AppLovin MAX, ironSource,
  AdMob mediation).

### Who (Android, 42matters, share of ad-SDK apps / share of their downloads)
| # | SDK | Apps | App share | Download share |
|---|---|---|---|---|
| 1 | Google AdMob | 675k | 86.1% | 87.4% |
| 2 | IAB Open Measurement (measurement, not a network) | 192k | 24.5% | 53.4% |
| 3 | Meta Audience Network | 181k | 23.1% | 53.5% |
| 4 | Unity Ads | 159k | 20.3% | 44.7% |
| 5 | AppLovin MAX | 136k | 17.4% | 43.7% |
| 6 | Vungle (Liftoff) | 106k | 13.5% | 40.4% |
| 7 | ironSource | 103k | 13.2% | 32.7% |
| 8 | Pangle (ByteDance) | 98k | 12.6% | 34.7% |
| 9 | Mintegral | 98k | 12.5% | 33.7% |
| 10 | InMobi | 78k | 10.0% | 29.9% |
| 11–20 | ironSource AdQuality, Google IMA, DT Exchange, Chartboost, BIGO, Yandex, Monetization.com, Appodeal, BidMachine, Start.io | 34–85k each | 4–11% | 2–27% |

iOS has the same names in a different order: AdMob is in 31.5% of ad-SDK apps (187k), then Meta, Unity, AppLovin MAX,
Vungle, Pangle, ironSource; plus Moloco and AdColony in the top 20.

### Does any of them pay the viewer?
- **No.** All of them pay the **app** (the publisher). "Rewarded" formats reward the viewer with in-app items (coins,
  lives, a hint) that the app grants; no money reaches the viewer. *Inference from the SDKs' published descriptions and
  R-02/R-03; no network in the top 20 advertises viewer payouts.*
- So the viewer-paying field from R-02 (Brave, W3AP, earn apps) is a niche next to a ~20-SDK mainstream that runs on
  about 30% of all Android apps.

## Implications for Adrop (for the owner to weigh, not decisions)
1. **Pitch:** "every ad network pays the app; none pays the person" now has a scanned base: 784k Android apps,
   top 20 SDKs, zero viewer payouts.
2. **Distribution:** apps already carry 3–6 ad SDKs and add them through mediation. Adrop as *one more SDK*, or as a
   **mediation adapter** (AdMob or AppLovin MAX custom network), fits how apps work today, instead of asking them to replace
   AdMob. That needs a research note before any build (after the deadline).
3. **Market sizing:** the reviewer asked for bottom-up numbers. Today's wedge stays the Seeker dApp Store (R-09:
   1,561 apps, 100k+ phones); the 784k ad-monetised Android apps are the ceiling of the host side, not a target.

## Recommendation
Use the counts in the pitch Q&A and the "sent" deck; keep the competition framing ("every ad SDK pays the app") rather than
naming 20 rivals. Open a follow-up note on a mediation adapter after 2026-10-12. What would change this: a top-20 network
launching viewer payouts, or 42matters' paid category list showing a larger viewer-paying tail.

## Owner decision
