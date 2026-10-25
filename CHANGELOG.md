# Changelog — veinpool.fr

## 25 October 2026 — Dogecoin SOLO, Epic Cash on CPU

- **Dogecoin** opens in SOLO on our own Dogecoin Core node: `3630` mini Scrypt miners, `3632` Scrypt ASIC. One block a minute, 10,000 DOGE per block. At the network hashrate of 25 October (~2.7 PH/s), an Antminer L9 (16 GH/s) finds a block about every 4 months on average. DOGE only: no merged Litecoin.
- **Epic Cash** pool now accepts RandomX (CPU) shares as well as ProgPow (GPU) on port `3150`: run SRBMiner `randomepic` on the CPU and `progpow_epic` on the GPU with the same address. Shares count only on blocks of their own algorithm.
- Epic Cash payouts are automatic (epicbox), with a delivery check: an unanswered transaction is cancelled and sent again.

## 24 October 2026 — Bitcoin Cash & Litecoin SOLO (ASIC)

- **Bitcoin Cash** opens in SOLO on our own BCHN node: `3610` NerdMiner / ESP32, `3611` Bitaxe / NerdAxe, `3612` SHA-256 ASIC (TLS `13610`–`13612`). The network is about 325 times smaller than Bitcoin's: at the hashrate of 24 October, a 200 TH/s Antminer S21 finds a block every ~109 days on average (vs ~97 years solo on Bitcoin). Whole block to the finder: 3.125 BCH + fees, minus 1 %.
- **Litecoin** opens in SOLO on our own Litecoin Core node: `3620` mini Scrypt miners, `3622` Scrypt ASIC (TLS `13620` / `13622`). An Antminer L9 (16 GH/s) has about a 70 % chance per year to hit a whole 6.25 LTC block. LTC only: no merged Dogecoin.
- Coin pages now list **every miner of the pool**: address, hashrate, pool share and, in PPLNS, the live share of the next block with the small-miner bonus.
- Mobile: smoother scrolling (no backdrop blur on phones, animations paused off screen, blocks shown before they scroll into view).
- Videos: [BCH](https://youtu.be/zVRQ4VzgS2I) · [LTC](https://youtu.be/4ZqekUTB25o) · Shorts [BCH](https://youtu.be/RwRtEX_PN50) · [LTC](https://youtu.be/9UyeZsjDlTs)
- Next: Dogecoin (`3630` / `3632`) once its node is in sync.

## 23 October 2026 — Bitcoin SOLO lottery (NerdMiner, Bitaxe, ASIC)

- **Bitcoin** opens in SOLO on our own Bitcoin Core 31.1 node: port `3600` for NerdMiner / ESP32 (start difficulty 0.0005, so a ~50 kH/s device sees its shares), `3601` for Bitaxe / NerdAxe / NerdQAxe, `3602` for SHA-256 ASICs. TLS on `13600`–`13602`.
- The miner who finds a block receives the whole 3.125 BTC + transaction fees, minus the 1 % pool fee, paid automatically (minimum 0.001 BTC).
- Site: ASIC badge and filter, ASIC hardware in the calculator (NerdMiner, Bitaxe Gamma / Supra, NerdQAxe++, Antminer S21 / S21 Pro / S19k Pro, Whatsminer M60S), and a setup wizard that shows the settings to type in the device's web page instead of a command line.
- Video: https://youtu.be/1s79oCt-czA · Short: https://youtu.be/DAZfuFHHP5Y
- Next: Bitcoin Cash (ports `3610`–`3612`), Litecoin (`3620` / `3622`) and Dogecoin (`3630` / `3632`) nodes are syncing; their SOLO pools are configured and open as soon as each node is in sync.

## 22 October 2026 — small-miner bonus

- **Every PPLNS pool** (Miningcore coins, Kerrigan, Riecoin, WAM and the VEIN pool servers for Quantus, Tari, Xelis, Epic Cash, Grin, Zephyr, Salvium) now applies the small-miner bonus: an address holding less than 10 % of a block's shares gets its share raised by up to 5 %.
- Funded **only by the pool fee** of that block; the other miners' share is never reduced. All bonuses of a block together never exceed that block's fee: rate = min(5 %, fee ÷ rewards of all small miners).
- Credited automatically, shown as *Bonus petit mineur* in the payout history. No retroactive effect (blocks credited from 22 Oct 2026 16:57 UTC).
- Site: bonus band on the home page and /pools, chip on every coin page, calculator note, FAQ entry, terms of use §2 (FR + EN).
- Also today: one H1 / title / description per page shared by the pre-render and the app, one miner table and command generator, realistic profitability (your hashrate joins the network), aggregated public API `/api/pools` (all 35 coins, TLS ports declared), HSTS preload.

## V3.1 — 19 October 2026

### New pool cards
- Every pool card was redrawn. Each card shows:
  - a larger logo tile in the coin's colour and a *LIVE* badge;
  - the price with its 24 h change and a 24 h price curve from the exchange ticker;
  - VEIN hashrate, miners and network hashrate;
  - a bar for VEIN's share of the network;
  - blocks found and a *Mine* button.
- The cards update in place every 10 s (DOM morph, no flicker). Hover effects run on the compositor only (`transform` / `opacity`).

### Pool grid toolbar (home and /pools)
- Live search by name, ticker or algorithm.
- GPU / CPU / *With blocks* filters.
- Sort by *Most mined* (VEIN share of the network, the default), *Most blocks*, *24 h change* or *Name*.

### Live figures in the hero
- The hero shows live figures: open pools, blocks found, miners online and the fee.

### Open pools only
- The site now lists only pools that are open. Coins that are not mineable on a pool yet are no longer shown: Keryx, Parano1d, Riecoin, Dilithion, Monetarium and Kaspa.
- Their pages left the sitemap, and old links redirect to /pools.

### Speed and testing
- Idle CPU on the home page stays at the V3 level, about 12 % of a core.
- Checked on desktop, on mobile (390 px) and in English, with no errors.

## V3 — 18 October 2026

### Live markets
- **Market data service** (`vein-tradecache`, Python, systemd): reads each coin's main exchange market and writes small static JSON files that nginx serves directly, so visitors never wait on (or get rate-limited by) an exchange.
  - Exchanges: MEXC, Binance, Gate, XT.com, BigONE and NonKYC. The market for each coin is chosen by 24 h volume (from CoinGecko tickers).
  - 24 coins tracked: candles in 15 min, 1 h, 4 h and 1 day (300 bars each), plus a ticker file holding last price, 24 h change, high, low, volume, a 24 h sparkline and the EUR/USD rate.
  - Refresh rates: last price every 15 s, 15-min candles every minute, daily candles every 30 min. That is about one exchange request every 2 seconds in total, whatever the number of visitors. The service is capped at 120 MB of RAM and runs at low priority (nice 10).
- **Candlestick chart on every coin page**: [TradingView Lightweight Charts™](https://www.tradingview.com/lightweight-charts/) 4.2.3 (Apache-2.0).
  - The library is self-hosted and loaded only on coin pages.
  - Candles or line view, a volume histogram and an OHLC legend that follows the crosshair. Price precision adapts from 0.000000007 to 100 000.
  - The last candle moves with the live price every 10 s, and the candles are re-read every minute.
  - The chart is freed as soon as you leave the page.
- **Live price header** on coin pages: pair and exchange, last price in USDT and EUR, 24 h change, high, low, volume and sparkline. The price flashes green or red on each move.
- **Live markets screener** on the home page (new *Markets* menu entry). It is sortable by name, price, 24 h change or volume, and refreshes every 10 s with a flash on each change. Click a row to open that coin's chart.
- Coins without a CoinGecko listing (CapStash, LuckyPepe…) now take their EUR price from the exchange ticker. Block values, the calculator, the cards and the miner dashboard use it.

### Official links
- Every coin page now has a row of official links: website, block explorer, GitHub, X, Discord, *Trade on <exchange>* and *Open on TradingView* (MEXC, Binance and Gate pairs).
- Sources: CoinGecko project links or the projects' own repositories, each one opened and checked. Explorers come from the block-link table, whose entries were verified block by block.
- A known-hijacked explorer domain is deliberately left out.

### Fluidity
- About 15 infinite decorative animations were rebuilt to run on the compositor only (`transform` / `opacity`). They used to animate `box-shadow`, `text-shadow`, `background-position` or registered `@property` angles under blur filters, which made the browser repaint 60 times a second.
  - Status dots now use a scaling ring instead of a growing box-shadow.
  - The gold shimmer on titles is now static, and the glowing block counters use a static glow.
  - The fire border of the "most mined" cards now breathes with opacity instead of spinning.
- Hero canvas ("veins"):
  - per-frame `shadowBlur` was replaced by layered translucent strokes (same look, a fraction of the cost);
  - device-pixel ratio capped at 1.25;
  - about 40 fps;
  - still paused when off-screen or when the tab is hidden.
- The page background is no longer `background-attachment: fixed`, which repainted the whole page on every scroll step. The glow lives on a single fixed composited layer.
- The page transition no longer animates a full-page blur filter.
- Each coin card is a layout island (`contain: layout style`): a live number changing in one card no longer re-lays out the grid.
- **Measured** (headless Edge, 20 s idle, desktop):

  | Page | Idle CPU before | Idle CPU after |
  |---|---|---|
  | Home | ~34 % of a core | ~10 % |
  | Coin page | ~10 % | < 1 % |

  On the coin page, 1,145 layouts in 20 s became 12.
- Fixed a sideways scroll on phones when arriving on /pools from another page (decor image bleeding past the viewport): `overflow-x: clip`, which keeps sticky headers working.

### Server
- Live feed polling is now every 8 s instead of 5 s, so each visitor makes about 40 % fewer API calls.
- Docker logs are trimmed daily (containers keep running). Disk use went from 93 % to 76 %.
- No pool or Miningcore restart was needed: every miner stayed connected during the upgrade.

### Pools
- **Satoshi Cash (SCASH)** is live: PPLNS on `3520` / `3521` (servers), SOLO on `3522`.
  - Miner: SRBMiner `--algorithm randomscash`. XMRig has no SCASH variant.
- New in the last days: Zephyr (ZEPH), Salvium (SAL) and Yerbas (YERB).
  - Zephyr and Salvium run on our own RandomX pool server, which asks the node for a block template per miner session (no blob parsing). Built-in payouts.
  - Yerbas (Ghostrider) has founder and smartnode payees taken from the node's template.
