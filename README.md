<p align="center">
  <a href="https://veinpool.fr/?lang=en"><img src="assets/banner.jpg" alt="VEIN Pool — multi-coin mining pool, PPLNS & SOLO, own full nodes, EU" width="100%"></a>
</p>

<p align="center">
  <a href="https://veinpool.fr/?lang=en"><img src="https://img.shields.io/badge/website-veinpool.fr-f6c76e?style=for-the-badge" alt="website"></a>
  <img src="https://img.shields.io/badge/location-EU%20%F0%9F%87%AB%F0%9F%87%B7-2b6cb0?style=for-the-badge" alt="EU">
  <img src="https://img.shields.io/badge/modes-PPLNS%20%7C%20SOLO-28a745?style=for-the-badge" alt="modes">
  <img src="https://img.shields.io/badge/fee-1%25%20%C2%B7%20SOLO%20direct%200%25-ff8f4f?style=for-the-badge" alt="fees">
  <img src="https://img.shields.io/badge/lang-EN%20%7C%20FR-8a2be2?style=for-the-badge" alt="EN FR">
</p>

**VEIN** runs mining pools for small and new proof-of-work coins. Every pool sits on **its own full node** — no proxy, no rented hashrate — and gives you the choice between **PPLNS** (steady payouts, shared by merit) and **SOLO** (the whole block is yours).

<p align="center"><a href="https://veinpool.fr/?lang=en"><img src="assets/site-home.jpg" alt="veinpool.fr home: live hashrate gauges, most mined coins" width="92%"></a></p>

- ⚡ **Realtime dashboard** — your rigs appear the second they connect, with alerts when one drops or finds a block
- 🎯 **PPLNS or SOLO** on the same coin, just switch port
- 🪙 **SOLO direct** on Warthog, Dero and Zycord: our node builds the block template **for your own address**, the chain pays you directly — the pool never holds your funds (0 % fee)
- 🧮 **Pool vs solo calculator** and a live hardware ranking (GPUs and CPUs, net of electricity)
- 🔍 Every block the pool finds, with its rig, effort, confirmations and explorer link

### Coins

| Coin | Algo | Mode | | Coin | Algo | Mode |
|---|---|---|---|---|---|---|
| 🆕 [CapStash](https://veinpool.fr/coin/cap?lang=en) | WhirlpoolX2 (NVIDIA) | PPLNS · SOLO | | 🆕 [Nexa](https://veinpool.fr/coin/nexa?lang=en) | NexaPow | PPLNS · SOLO |
| 🆕 [LuckyPepe](https://veinpool.fr/coin/lpepe?lang=en) | YescryptR32 (CPU) | PPLNS · SOLO | | 🆕 [Kylacoin](https://veinpool.fr/coin/kcn?lang=en) | Flex (CPU) | PPLNS · SOLO |
| 🆕 [Cascoin](https://veinpool.fr/coin/cas?lang=en) | MinotaurX (CPU) | PPLNS · SOLO | | 🆕 [Tidecoin](https://veinpool.fr/coin/tdc?lang=en) | YespowerTIDE (CPU) | PPLNS · SOLO |
| [Quantus](https://veinpool.fr/coin/qtc?lang=en) | QPoW | PPLNS · SOLO | | [Xelis](https://veinpool.fr/coin/xel?lang=en) | XelisHash v3 | PPLNS · SOLO |
| [Firo](https://veinpool.fr/coin/firo?lang=en) | FiroPoW | PPLNS · SOLO | | [Tari](https://veinpool.fr/coin/xtm?lang=en) | RandomXT | PPLNS · SOLO |
| [Ravencoin](https://veinpool.fr/coin/rvn?lang=en) | KawPow | PPLNS · SOLO | | [Qubitcoin](https://veinpool.fr/coin/qubit?lang=en) | Qhash | PPLNS · SOLO |
| [Neurai](https://veinpool.fr/coin/xna?lang=en) | KawPow | PPLNS · SOLO | | [Ycash](https://veinpool.fr/coin/yec?lang=en) | Equihash 192,7 | PPLNS · SOLO |
| [Satoxcoin](https://veinpool.fr/coin/satox?lang=en) | KawPow | PPLNS · SOLO | | [Feelcoin](https://veinpool.fr/coin/feel?lang=en) | RandomX | PPLNS · SOLO |
| [Gaelium](https://veinpool.fr/coin/gael?lang=en) | KawPow | PPLNS · SOLO | | [WAM Coin](https://veinpool.fr/coin/wam?lang=en) | RandomX | PPLNS |
| [Neoxa](https://veinpool.fr/coin/neox?lang=en) | KawPow | PPLNS · SOLO | | [Zycord](https://veinpool.fr/coin/zcd?lang=en) | RandomX v2 | SOLO direct |
| [Kerrigan](https://veinpool.fr/coin/krgneq?lang=en) | Equihash 192,7 | PPLNS · SOLO | | [Epic Cash](https://veinpool.fr/coin/epic?lang=en) | ProgPow | PPLNS · SOLO |
| [Zano](https://veinpool.fr/coin/zano?lang=en) | ProgPowZ | PPLNS · SOLO | | [Dero](https://veinpool.fr/coin/dero?lang=en) | AstroBWTv3 (CPU) | SOLO direct |
| [Warthog](https://veinpool.fr/coin/wart?lang=en) | Janushash (GPU + CPU) | SOLO direct | | [Beam](https://veinpool.fr/coin/beam?lang=en) | BeamHash III | PPLNS · SOLO |
| [Grin](https://veinpool.fr/coin/grin?lang=en) | Cuckatoo32 | PPLNS · SOLO | |  | |  |

<table>
  <tr>
    <td width="50%"><a href="https://veinpool.fr/pools?lang=en"><img src="assets/site-pools.jpg" alt="Pool cards with live stats and blocks found by VEIN"></a></td>
    <td width="50%"><a href="https://veinpool.fr/blocks?lang=en"><img src="assets/site-blocks.jpg" alt="Every block found by VEIN, with rig, status and reward"></a></td>
  </tr>
  <tr>
    <td align="center"><sub>Every coin, with live hashrate and the blocks VEIN found on it</sub></td>
    <td align="center"><sub>Every block: rig, maturity, reward in coins and euros</sub></td>
  </tr>
</table>

### Quick start
```bash
# Warthog SOLO direct (GPU + CPU) — block paid straight to your address
bzminer -a warthog -w YOUR_ADDRESS.rig1 -p stratum+tcp://veinpool.fr:3340 --nvidia --amd --cpu

# Dero SOLO direct (CPU) — use a registered wallet (Engram / dero-wallet-cli)
dero-miner --wallet-address YOUR_ADDRESS --daemon-rpc-address veinpool.fr:3350 --mining-threads 8

# Ravencoin (KawPow) — wallet address = login, no account
t-rex -a kawpow -o stratum+tcp://veinpool.fr:3080 -u YOUR_ADDRESS.rig1 -p x
```
👉 All ports and ready-made commands for Windows, Linux, HiveOS and MMPOS: **[veinpool/mining-configs](https://github.com/veinpool/mining-configs)** · or the wizard on each coin page.

### Open source
- **[miningcore-live-rigs](https://github.com/veinpool/miningcore-live-rigs)** — realtime rig connect/disconnect events for Miningcore pools
- **[mining-configs](https://github.com/veinpool/mining-configs)** — stratum ports and miner commands for every VEIN coin

🌍 **https://veinpool.fr/?lang=en** · en français : **https://veinpool.fr** · 📫 contact@veinpool.fr
