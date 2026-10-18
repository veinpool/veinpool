# Changelog — veinpool.fr

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
