<a name="top"></a>

# Awesome Prediction Market APIs [![Awesome](https://awesome.re/badge-flat.svg)](https://awesome.re)

![Maintained](https://img.shields.io/badge/Maintained%3F-yes-brightgreen.svg)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-blue.svg)
![Entries](https://img.shields.io/badge/entries-67-informational.svg)

> A researched directory of the **developer side** of prediction markets: APIs, SDKs, MCP servers, historical order book data, and the agent tooling built on top of them.
> Covering Polymarket, Kalshi, Manifold, Limitless, Smarkets and the wider forecasting ecosystem.

Most prediction market lists index dashboards and Telegram bots. This one indexes the things you integrate against. Every entry was opened and checked in **September 2026**: licences and commit dates come from the GitHub API, pricing comes from the vendor's own page, and anything that could not be confirmed is written as **not publicly listed** rather than guessed.

**Pull requests welcome.** See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format and what gets checked.

---

<a name="featured"></a>

## ⭐ Featured: Predictefy

**[Predictefy](https://docs.predictefy.com/api/?utm_source=awesome-prediction-market-apis)** — _One normalized API across 16 prediction market venues._

Predictefy is unified prediction-market infrastructure: a single REST contract, TypeScript and Python SDKs, a CLI, and an MCP server, all speaking one normalized schema across **16 served venues** plus a `router` pseudo-venue that answers for every served venue at once. You integrate once and change the venue parameter to reach a different market, rather than writing and maintaining a client per exchange.

Every record carries honest-data fields (`asOf`, `provenance`, `capabilities`), and per-venue support is capability-qualified, so you read a venue's `has` map instead of discovering at runtime that a verb is unavailable. Cross-venue price gaps are labelled **indicative price discrepancies** unless a row passes a live executability assessment against real asks, depth, fees and resolution equivalence. Execution is non-custodial: orders are built server-side, signed **in your own process**, and relayed back, so key custody stays with you.

- **Best for:** building once against many venues instead of maintaining a client per exchange.
- **Surface:** 92 REST operations · WebSocket streaming · [`@predictefy/sdk`](https://www.npmjs.com/package/@predictefy/sdk) · [`predictefy`](https://pypi.org/project/predictefy/) on PyPI · [`@predictefy/cli`](https://www.npmjs.com/package/@predictefy/cli) · [`@predictefy/mcp`](https://www.npmjs.com/package/@predictefy/mcp) with 43 tools
- **Pricing:** free plan with 25,000 credits monthly, refilled, no invite needed. Endpoint-weighted credits beyond that.
- **Phase:** API live · packages on `1.0.0-beta.6` (npm) and `1.0.0b4` (PyPI), MIT.
- **Reviewed:** Sep 2026

👉 **Docs and a free key:** **https://docs.predictefy.com** · [portal.predictefy.com/keys](https://portal.predictefy.com/keys?utm_source=awesome-prediction-market-apis)

---

## Contents

- [🧩 Unified & Cross-Venue APIs](#unified--cross-venue-apis)
- [📡 Historical Order Book & Tick Data](#historical-order-book--tick-data)
- [📦 Venue SDKs & Client Libraries](#venue-sdks--client-libraries)
- [🤖 MCP Servers & Agent Tooling](#mcp-servers--agent-tooling)
- [🔀 Cross-Venue Comparison & Price Gaps](#cross-venue-comparison--price-gaps)
- [📊 Analytics, Terminals & Dashboards](#analytics-terminals--dashboards)
- [⚙️ Trading Bots & Market Making](#trading-bots--market-making)
- [🔔 Alerts & Monitoring](#alerts--monitoring)
- [🏛️ Venues With Public APIs](#venues-with-public-apis)
- [📚 Research & Reading](#research--reading)
- [🔗 Related Lists](#related-lists)

---

<a name="unified--cross-venue-apis"></a>

## 🧩 Unified & Cross-Venue APIs

One integration, many venues.

- **[Predictefy](https://docs.predictefy.com/api/?utm_source=awesome-prediction-market-apis)**: Normalized REST and WebSocket API across 16 venues with TypeScript, Python, CLI and MCP clients.
  See [the featured entry](#featured) above for the full write-up.
  - **Best for:** one schema and one key across many venues.
  - **Pricing:** free plan, 25,000 credits monthly.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Adanos Market Sentiment API](https://api.adanos.org/docs/)**: Market sentiment API with public documentation.
  - **Best for:** adding a sentiment signal alongside price data.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[SimpleFunctions](https://simplefunctions.dev/docs)**: Developer platform spanning a CLI, agents, HTTP APIs, real-time data, workflows and an MCP adapter.
  Broader than prediction markets, with a real-time data surface that reaches them.
  - **Best for:** teams already standardizing on one function and workflow runtime.
  - **Pricing:** not publicly listed.
  - **Phase:** beta · **Reviewed:** Sep 2026

- **[Bitquery Polymarket API](https://docs.bitquery.io/docs/examples/polymarket-api/)**: GraphQL access to Polymarket activity indexed from on-chain data.
  - **Best for:** on-chain queries and wallet-level joins across chains.
  - **Pricing:** not publicly listed on the example page; see Bitquery's own plans.
  - **Phase:** live · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="historical-order-book--tick-data"></a>

## 📡 Historical Order Book & Tick Data

The hardest data to get, and where most integrations stall. Midpoints are cheap; depth with size is not.

- **[Marketlens](https://marketlens.trade/)**: Tick-level Polymarket order book history with L2 snapshots and deltas, millisecond replay, trades, candles, Parquet exports and a Python client.
  - **Best for:** backtests that need exact book state rather than candles.
  - **Pricing:** free and paid tiers; API key required.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Probalytics](https://probalytics.io)**: Full-depth order book snapshots for Polymarket since Nov 2025 and Kalshi since May 2026, stored on every change.
  Snapshot-on-change rather than fixed-interval sampling, so the book is not smoothed.
  - **Best for:** microstructure work that cannot tolerate interpolated depth.
  - **Pricing:** free tier and a published pricing page; API key required.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PolyOrderbooks](https://polyorderbooks.com)**: One-second Polymarket order book history, plus a natural-language backtest tool that replays a described strategy over the archive.
  - **Best for:** replaying a strategy idea before writing any code.
  - **Pricing:** free tier and a published pricing page; API key required.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PolyBackTest](https://polybacktest.com/)**: Polymarket dataset with full historical order book depth at one-minute resolution, built for strategy backtesting.
  - **Best for:** minute-resolution backtests where per-tick fidelity is not required.
  - **Pricing:** free tier and a published pricing page; API key required.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[TickFoundry](https://tickfoundry.com/)**: Every order, book update and trade captured live from Polymarket and delivered as replayable history, including L1 quotes.
  - **Best for:** firms that want the raw tape delivered rather than collected.
  - **Pricing:** paid, with a published pricing page. Access is waitlisted.
  - **Phase:** waitlist · **Reviewed:** Sep 2026

- **[OrderbookTrade](https://www.orderbook.trade)**: Order book focused data service for prediction markets.
  - **Best for:** a second source when cross-checking depth.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Prediction Market Analysis](https://github.com/Jon-Becker/prediction-market-analysis)**: Open research repository analysing prediction market behaviour, with the analysis code published alongside.
  - **Best for:** reading a full methodology rather than trusting a chart.
  - **Licence:** MIT · **Stars:** 3.8k · **Last commit:** Aug 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Prediction Markets Scraper](https://apify.com/gratified_ashram/prediction-markets-scraper)**: Hosted Apify actor that scrapes Kalshi and Polymarket market listings on a schedule.
  - **Best for:** one-off collection without standing up a crawler.
  - **Pricing:** Apify usage-based; actor pricing on its listing page.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Polymarket Markets Data](https://dune.com/fergmolina/polymarket-markets-data)**: Community-maintained Dune dashboard over Polymarket's on-chain data.
  - **Best for:** SQL exploration without building an indexer.
  - **Pricing:** free to view; Dune plans apply for API export.
  - **Phase:** live · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="venue-sdks--client-libraries"></a>

## 📦 Venue SDKs & Client Libraries

Venue-specific clients and harnesses. Check the commit date before you build on one.

- **[py-clob-client](https://github.com/Polymarket/py-clob-client)**: Polymarket's own Python client for the CLOB API.
  ⚠️ **Archived by the owner.** Still the most-starred Polymarket client and still widely referenced, but it is no longer maintained upstream. Treat it as a reference implementation and check Polymarket's current docs before depending on it.
  - **Best for:** reading how CLOB auth and order signing actually work.
  - **Licence:** MIT · **Stars:** 1.2k · **Last commit:** May 2026 · **Archived:** yes
  - **Pricing:** free, open source.
  - **Phase:** archived · **Reviewed:** Sep 2026

- **[pykalshi](https://github.com/arshka/pykalshi)**: Python client for Kalshi with WebSocket streaming, automatic retries, rate limiting, pandas integration and local order book management.
  - **Best for:** Kalshi research in a notebook.
  - **Licence:** MIT · **Stars:** 123 · **Last commit:** Jul 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[manifoldpy](https://github.com/vluzko/manifoldpy)**: Python client and dataset helpers for Manifold Markets.
  - **Best for:** Manifold data pulls and academic work.
  - **Licence:** MIT · **Stars:** 41 · **Last commit:** Jul 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PyManifold](https://github.com/LivInTheLookingGlass/PyManifold)**: Alternative Python wrapper for the Manifold API.
  ⚠️ No commits since Aug 2023. Listed for completeness.
  - **Best for:** reference only.
  - **Licence:** MIT · **Stars:** 6 · **Last commit:** Aug 2023
  - **Pricing:** free, open source.
  - **Phase:** unmaintained · **Reviewed:** Sep 2026

- **[simmer-sdk](https://github.com/SpartanLabsXyz/simmer-sdk)**: Prediction market harness for AI agents, shipping skills, an MCP server and a Python SDK together.
  - **Best for:** giving an existing agent a trading surface.
  - **Licence:** MIT · **Stars:** 48 · **Last commit:** Sep 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026


[↑ Back to top](#top)

---

<a name="mcp-servers--agent-tooling"></a>

## 🤖 MCP Servers & Agent Tooling

Model Context Protocol servers and agent frameworks that reach prediction markets. The newest category here and the fastest moving.

- **[@predictefy/mcp](https://www.npmjs.com/package/@predictefy/mcp)**: MCP server exposing 43 tools over 16 venues: markets, order books, history, cross-venue intelligence, trader analytics, and a guardrailed execution set.
  Grouped and parameterized tools rather than one per endpoint, with server-side caps on rows, candles and response size. The ten execution tools register by default and are removed by setting `MCP_ENABLE_TRADE=false`.
  - **Best for:** giving Claude, Cursor or a custom agent a read surface over many venues at once.
  - **Licence:** MIT · **Version:** `1.0.0-beta.6`, published Sep 2026
  - **Pricing:** free tier via the Predictefy free plan.
  - **Phase:** beta · **Reviewed:** Sep 2026

- **[Aeon](https://github.com/aeonfun/aeon)**: Autonomous agent framework that runs unattended on GitHub Actions with self-healing skills, including scheduled monitoring of Polymarket and Kalshi.
  - **Best for:** scheduled, unattended market monitoring without hosting anything.
  - **Licence:** MIT · **Stars:** 723 · **Last commit:** Sep 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[MiroShark](https://github.com/MiroShark/MiroShark)**: Swarm-intelligence engine that simulates a prediction market alongside social platforms, with hundreds of grounded LLM personas trading and posting, plus per-agent MCP tools.
  - **Best for:** counterfactual scenario work rather than live trading.
  - **Licence:** AGPL-3.0 · **Stars:** 1.4k · **Last commit:** Sep 2026
  - **Pricing:** free, open source; the authors cite roughly $1 of model spend per run.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PolyClaw](https://github.com/chainstacklabs/polyclaw)**: Agent skill for Polymarket trading with order execution and LLM-assisted hedge discovery.
  - **Best for:** adding a Polymarket execution skill to an existing agent.
  - **Licence:** Apache-2.0 · **Stars:** 356 · **Last commit:** Apr 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[oracle3](https://github.com/YichengYang-Ethan/oracle3)**: Autonomous trading agent for Kalshi, Polymarket and Solana DFlow using Wang Transform pricing, constraint-based strategies and Kelly sizing.
  Backed by a published working paper, with the calibration set documented.
  - **Best for:** studying a quantitative agent whose method is written down.
  - **Licence:** Apache-2.0 · **Stars:** 255 · **Last commit:** May 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PredictOS](https://github.com/PredictionXBT/PredictOS)**: Agent operating layer aimed at prediction market workflows.
  - **Best for:** an opinionated starting scaffold.
  - **Licence:** MIT · **Stars:** 146 · **Last commit:** May 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Simmer](https://simmer.markets)**: Hosted harness that connects an AI agent to Polymarket and Kalshi with installable trading skills and paper-trading before live capital.
  - **Best for:** trying an agent strategy without funding it first.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Baozi MCP Server](https://github.com/bolivian-peru/baozi-mcp)**: MCP server for Baozi's Solana prediction markets, exposing 68 tools to agents.
  - **Best for:** Solana-native prediction market agents.
  - **Licence:** MIT · **Stars:** 1 · **Last commit:** Apr 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Polyrama](https://polyrama.io/)**: Live Polymarket and Kalshi tracking with 24-hour movers and smart-money views, with an accompanying MCP server.
  - **Best for:** a quick movers feed inside a chat client.
  - **Pricing:** not publicly listed.
  - **Phase:** beta · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="cross-venue-comparison--price-gaps"></a>

## 🔀 Cross-Venue Comparison & Price Gaps

Same outcome, different venues. A price gap observed on mid-prices is an **indicative discrepancy**, not an executable trade, until it is checked against live asks, depth, fees and resolution equivalence.

- **[MetaForecast](https://metaforecast.org/)**: Meta search across prediction markets and forecasting platforms, presenting and sharing probability estimates from many sources.
  The most cross-listed tool in this space, appearing in four of the eight source lists surveyed.
  - **Best for:** finding every venue that prices a given question.
  - **Pricing:** free. Run by the Quantified Uncertainty Research Institute, a nonprofit.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Predictions Network](https://www.thebestpredictionmarkets.com/)**: Compares the same outcome across 12 venues side by side and highlights the best price after fees, with quotes date-stamped from the underlying data.
  Read-only: no wallet connection and no execution.
  - **Best for:** checking which venue prices an outcome best before opening an account.
  - **Pricing:** free.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PredictionHero](https://predictionhero.com/)**: Compares odds and probabilities across Polymarket, Kalshi, Limitless, Predict.fun and Opinion, with trending, new and ending-soon views.
  - **Best for:** spotting where venues disagree on the same event.
  - **Pricing:** not publicly listed.
  - **Phase:** beta · **Reviewed:** Sep 2026

- **[Prediction Index](https://predictionindex.xyz)**: Maps and ranks prediction market venues and helps readers discover them.
  - **Best for:** venue discovery rather than price comparison.
  - **Pricing:** free.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Synthesis](https://synthesis.trade/)**: Cross-venue trading interface with developer documentation.
  - **Best for:** a lighter-weight terminal.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="analytics-terminals--dashboards"></a>

## 📊 Analytics, Terminals & Dashboards

- **[TREMOR](https://github.com/sculptdotfun/tremor)**: Open-source data terminal for Polymarket and Kalshi with SQL analytics and real-time market intelligence.
  ⚠️ No commits since Sep 2025.
  - **Best for:** self-hosting a SQL-first terminal.
  - **Licence:** MIT · **Stars:** 61 · **Last commit:** Sep 2025
  - **Pricing:** free, open source.
  - **Phase:** unmaintained · **Reviewed:** Sep 2026

- **[PolyAlertHub](https://polyalerthub.com/)**: Polymarket terminal combining analytics with real-time alerts, including fresh-wallet and smart-money tracking.
  - **Best for:** watching wallet behaviour rather than prices alone.
  - **Pricing:** free and paid tiers, with a published pricing page.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PredictFolio](https://predictfolio.com)**: Tracks prediction market traders and analyses PnL with community insights.
  - **Best for:** following specific wallets over time.
  - **Pricing:** free tier advertised.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Polyvision](https://polyvisionx.com)**: Copy-trading analysis for Polymarket, focused on systematizing rather than following blindly.
  - **Best for:** evaluating whether a trader is worth copying.
  - **Pricing:** free tier and a published pricing page.
  - **Phase:** beta · **Reviewed:** Sep 2026

- **[Polymarket Analytics](https://polymarketanalytics.com/)**: Analytics dashboards over Polymarket activity.
  - **Best for:** a quick read on venue-level activity.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PolymarketDash](https://www.polymarketdash.com/)**: Dashboard view of Polymarket markets and movement.
  - **Best for:** at-a-glance monitoring.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PolyData](https://www.polydata.org/)**: Polymarket data project.
  - **Best for:** a secondary data reference.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Dimes](https://dimes.fi)**: Leverage product for prediction markets.
  - **Best for:** teams evaluating leveraged exposure. Understand the liquidation mechanics first.
  - **Pricing:** paid; access is waitlisted.
  - **Phase:** beta · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="trading-bots--market-making"></a>

## ⚙️ Trading Bots & Market Making

Reference implementations. Read the licence and the last commit date before running anything with funds behind it.

- **[poly-maker](https://github.com/warproxxx/poly-maker)**: Open-source market making bot for Polymarket.
  - **Licence:** MIT · **Stars:** 1.5k · **Last commit:** Jul 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[polybot](https://github.com/ent0n29/polybot)**: Polymarket trading bot.
  ⚠️ No commits since Feb 2026.
  - **Licence:** MIT · **Stars:** 1.0k · **Last commit:** Feb 2026
  - **Pricing:** free, open source.
  - **Phase:** stale · **Reviewed:** Sep 2026

- **[Polymarket-bot](https://github.com/MrFadiAi/Polymarket-bot)**: Polymarket automation bot.
  - **Licence:** MIT · **Stars:** 713 · **Last commit:** Jun 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[kalshi-ai-trading-bot](https://github.com/ryanfrigo/kalshi-ai-trading-bot)**: AI-assisted trading bot for Kalshi.
  - **Licence:** MIT · **Stars:** 579 · **Last commit:** Jul 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[kalshi-trading-bot-cli](https://github.com/OctagonAI/kalshi-trading-bot-cli)**: Command-line Kalshi trading bot with deep research integration.
  - **Licence:** MIT · **Stars:** 384 · **Last commit:** Sep 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[OctoBot Prediction Market](https://github.com/Drakkar-Software/OctoBot-Prediction-Market)**: Prediction market module for the OctoBot trading framework.
  - **Licence:** GPL-3.0 · **Stars:** 113 · **Last commit:** Mar 2026
  - **Pricing:** free, open source.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[kalshi-market-making](https://github.com/nikhilnd/kalshi-market-making)**: Market making reference for Kalshi.
  ⚠️ No commits since May 2023, and no licence file, so reuse rights are unclear.
  - **Stars:** 80 · **Last commit:** May 2023 · **Licence:** none declared
  - **Phase:** unmaintained · **Reviewed:** Sep 2026

- **[Manifold market-maker](https://github.com/manifoldmarkets/market-maker)**: Market making bot published by the Manifold team.
  ⚠️ No commits since Jul 2024.
  - **Licence:** MIT · **Stars:** 44 · **Last commit:** Jul 2024
  - **Phase:** unmaintained · **Reviewed:** Sep 2026

- **[manifoldbot](https://github.com/microprediction/manifoldbot)**: Manifold trading bot from the microprediction project.
- [HostDeFi](https://hostdefi.com/api/v1/mcp) - Hosted MCP server: free token-safety scans (A+–F grades) across Solana and 7 EVM chains, plus x402-paid analytics endpoints.

  - **Licence:** MIT · **Stars:** 13 · **Last commit:** Jan 2026
  - **Phase:** stale · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="alerts--monitoring"></a>

## 🔔 Alerts & Monitoring

- **[PolyAlertHub](https://polyalerthub.com/)**: Real-time Polymarket alerts on fresh wallets and smart money, alongside its terminal.
  - **Pricing:** free and paid tiers.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Polyrama](https://polyrama.io/)**: Biggest 24-hour movers and top-trader views across Polymarket and Kalshi.
  - **Pricing:** not publicly listed.
  - **Phase:** beta · **Reviewed:** Sep 2026

- **[Aeon](https://github.com/aeonfun/aeon)**: Scheduled skills that monitor Polymarket and Kalshi and alert on probability shifts, running unattended on GitHub Actions.
  - **Licence:** MIT · **Stars:** 723 · **Last commit:** Sep 2026
  - **Phase:** live · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="venues-with-public-apis"></a>

## 🏛️ Venues With Public APIs

The exchanges themselves, listed where a documented public API exists.

- **[Kalshi](https://docs.kalshi.com/welcome)**: CFTC-regulated US event exchange with documented REST and WebSocket APIs.
  - **Pricing:** free API access with an account; trading fees apply.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Polymarket](https://docs.polymarket.com)**: Large crypto-settled prediction market with a documented CLOB API and public docs.
  - **Pricing:** free API access; trading fees and gas apply.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Manifold](https://docs.manifold.markets/api)**: Play-money social prediction platform with an open, well-documented API.
  - **Best for:** prototyping against a real API without capital at risk.
  - **Pricing:** free.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Metaculus](https://www.metaculus.com/)**: Forecasting platform with a long track record of scored community predictions and an API.
  - **Pricing:** free.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Limitless](https://limitless.exchange/)**: Onchain prediction market covering crypto prices, sports and world events.
  - **Pricing:** free to browse; trading fees apply.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Smarkets](https://smarkets.com)**: Low-commission prediction exchange for sports, politics and global events, with developer documentation.
  - **Pricing:** commission on winnings; API access with an account.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Futuur](https://futuur.com/)**: Prediction market running both play-money and USDC markets.
  - **Pricing:** free play-money side.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[PredictIt](https://www.predictit.org/)**: Long-running academic-affiliated political prediction market.
  - **Pricing:** free to browse; fees apply on trading.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Iowa Electronic Markets](https://iem.uiowa.edu)**: The original academic prediction market, run by the University of Iowa since 1988.
  - **Best for:** historical context and research citations.
  - **Pricing:** free.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Insight Prediction](https://insightprediction.com/)**: Prediction market covering politics, sports and current events.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Hypermind](https://www.hypermind.com)**: Forecasting platform used for corporate and institutional prediction exercises.
  - **Pricing:** not publicly listed.
  - **Phase:** live · **Reviewed:** Sep 2026

- **[Baozi](https://baozi.bet)**: Pari-mutuel prediction market protocol on Solana, with an open MCP server for agents.
  - **Pricing:** free to browse; trading in SOL.
  - **Phase:** beta · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="research--reading"></a>

## 📚 Research & Reading

- **[Quantified Uncertainty Research Institute](https://metaforecast.org/)**: Nonprofit researching forecasting and epistemics, and the group behind MetaForecast.
  - **Phase:** active · **Reviewed:** Sep 2026

- **[Prediction Market Analysis](https://github.com/Jon-Becker/prediction-market-analysis)**: Open analysis of prediction market behaviour with published code.
  - **Licence:** MIT · **Stars:** 3.8k · **Reviewed:** Sep 2026

- **[oracle3 working paper](https://github.com/YichengYang-Ethan/oracle3)**: Wang Transform pricing calibrated on resolved contracts, with the SSRN paper linked from the repository.
  - **Licence:** Apache-2.0 · **Reviewed:** Sep 2026

[↑ Back to top](#top)

---

<a name="related-lists"></a>

## 🔗 Related Lists

Other directories in this space. Worth reading alongside this one, since each weights the field differently.

- **[Awesome Prediction Market Tools](https://github.com/aarora4/Awesome-Prediction-Market-Tools)**: The broadest general directory, covering agents, analytics, dashboards, bots and more.
- **[awesome-prediction-markets](https://github.com/0xperp/awesome-prediction-markets)**: Earlier list with a protocol and research emphasis.
- **[awesome-prediction-market-analytics-tools](https://github.com/talhareltal/awesome-prediction-market-analytics-tools)**: Analytics-focused directory with per-entry review notes.

[↑ Back to top](#top)

---

## Scope

**In scope:** APIs, SDKs, MCP servers, data feeds, historical datasets, and the agent tooling built on them. Anything a developer integrates against.

**Out of scope:** general macroeconomic data APIs, generic LLM frameworks with no prediction market surface, referral links, and closed betas with no public documentation.

## A note on price gaps

Several tools here surface differences between venues pricing the same outcome. A gap measured on mid-prices is an **indicative price discrepancy**. It becomes executable only once it has been checked against live asks with size, open markets, fees and gas, and resolution equivalence between the two venues. No entry in this list is a claim that a displayed gap is a realizable profit.

## Licence

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, the contributors have waived all copyright and related rights to this work.
