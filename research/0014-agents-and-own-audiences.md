# R-14: Can AI agents buy campaigns, and can anyone target their own list, on today's ad networks?

Date opened: 2026-10-10. Status: Done 2026-10-10 (facts); owner reads "Implications"
Feeds: pitch comparison frame (replaces the bots frames, owner 2026-10-10), R-02, R-13.

## Question
1. Do the big ad networks let an AI agent create and pay for a campaign?
2. Can any advertiser run a campaign targeted at their own list of people?

## Method
Web search 2026-10-10. Primary pages where found (Google policy); otherwise trade press and vendor pages, marked.

## Findings

### 1. AI agents
- **Meta: yes.** Ads MCP server open to any developer with a Meta app since 2026-07-21; agents can create, edit and
  delete campaigns, ad sets, ads and custom audiences. Write connectors for Claude and ChatGPT since 2026-04. No partner
  approval. *Source: Relevant Audience, citing PPC Land; Meta's own page not found.*
- **Google: yes, through the API.** The Google Ads API writes campaigns; Google's official MCP server is read-only.
  Both need a developer token and per-user OAuth. Third-party MCP servers add writes.
- **Industry standard:** AdCP (Ad Context Protocol, 2025-10-15; Yahoo, PubMatic, Scope3, Magnite and others) lets buyer
  agents discover inventory and create media buys over MCP/A2A.
- **What none of them offer:** buying without an account. Every path needs an ad account, a login (OAuth) and a billing
  method set up by a human first. Paying per campaign from a wallet, with no account, exists only in hackathon and demo
  projects (ad-402 at ETHGlobal 2025, Crossmint's x402 ad-agent demo). *Not checked: AppLovin, Unity and other mobile
  SDK networks' campaign APIs; they also sit behind advertiser accounts.*

### 2. Targeting your own list
- **Meta:** any advertiser can upload a customer list (email, phone) as a Custom Audience; floor about 100 matched people;
  match rates 30–70%. *Vendor guides; Meta's terms not read.*
- **Google Customer Match:** targeting needs 90 days of account history **and over $50,000 lifetime spend**, plus good
  policy and payment history; below that, lists work only for observation and exclusion. *Google Ads policy page.*
- **Wallets:** Google, Meta and X take emails, phones and device IDs, not wallet addresses. Addressable maps wallets to
  ad IDs on X and Reddit (vendor claims: 900M wallets processed). HypeLab targets by installed wallet app, detectable on
  about 20% of its traffic (HypeLab's own figure).
- **Live case:** Polkadot spent $144K on X through Addressable (Dec 2023–Apr 2024): 161M impressions, ~830k users
  engaged; fee 15% of spend + $800/month (public treasury proposal). Reddit: vendor claim only, no case found.
- **Viewer pay:** none of them pays the person who is targeted (R-13).

## Implications for Adrop (for the owner, not decisions)
1. **"Ad networks can't take AI agents" is false** for Meta and Google. The true difference: on Adrop an agent pays for a
   campaign in one x402 request from a wallet, with no account, login or card.
2. **Own-list targeting** is open on Meta and gated on Google ($50k). Adrop's difference: the list is wallet addresses,
   and each one belongs to one verified person who is paid for the view (ADR-0004: Adrop never sells or exports the list).
3. The comparison frame should state these three differences, not "they have no agents".

## Sources
- https://www.relevantaudience.com/meta/meta-ads-mcp-open-to-developers/ (Meta ads MCP, 2026-07-21)
- https://www.scalekit.com/blog/google-ads-mcp-vs-api (Google MCP read-only, API writes)
- https://www.adweek.com/media/adcp-ad-context-protocol-agentic-advertising-standard/ (AdCP)
- https://support.google.com/adspolicy/answer/6299717 (Customer Match policy)
- https://www.addressable.io/blog/guide-to-crypto-advertising-in-2026 (wallet audiences on X)
- https://www.hypelab.com/blog/wallet-detection-crypto-advertising-binary-signals (20% wallet detection)
- https://ethglobal.com/showcase/ad-402-5bnqt , https://www.mintlify.com/Crossmint/crossmint-agentic-finance/examples/ad-agent
- https://decrypt.co/232826/web3-targeting-success-polkadots-twitter-campaigns-thrive-with-addressable , https://polkadot.subsquare.io/referenda/298

## Owner decision
