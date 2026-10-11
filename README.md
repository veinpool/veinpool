<p align="center">
  <a href="https://veinpool.fr"><img src="https://veinpool.fr/favicon-192.png" width="96" alt="VEIN Pool"></a>
</p>

<h1 align="center">VEIN Pool</h1>
<p align="center"><b>Multi-coin mining pool · EU (France) · PPLNS & SOLO · own full nodes</b></p>
<p align="center">
  <a href="https://veinpool.fr"><img src="https://img.shields.io/badge/website-veinpool.fr-8a2be2?style=for-the-badge" alt="website"></a>
  <img src="https://img.shields.io/badge/location-EU%20%F0%9F%87%AB%F0%9F%87%B7-2b6cb0?style=for-the-badge" alt="EU">
  <img src="https://img.shields.io/badge/modes-PPLNS%20%7C%20SOLO-28a745?style=for-the-badge" alt="modes">
  <img src="https://img.shields.io/badge/lang-EN%20%7C%20FR-f6c76e?style=for-the-badge" alt="EN FR">
</p>

---

**VEIN** runs mining pools for small and new proof-of-work coins, each backed by its own full node (no proxy, no rented hashrate).

- ⚡ **Realtime dashboard** — your rigs show up the second they connect, alerts when one drops
- 🎯 **PPLNS or SOLO** on the same coin, switch by port
- 🧮 **Profitability calculator** and hardware guide
- 🔍 Block explorer view of every block the pool finds

### Coins

| Coin | Algo | | Coin | Algo |
|---|---|---|---|---|
| [Ergo](https://veinpool.fr/coin/erg?lang=en) | Autolykos2 | | [Xelis](https://veinpool.fr/coin/xel?lang=en) | XelisHash v3 |
| [Firo](https://veinpool.fr/coin/firo?lang=en) | FiroPoW | | [Tari](https://veinpool.fr/coin/xtm?lang=en) | RandomXT |
| [Ravencoin](https://veinpool.fr/coin/rvn?lang=en) | KawPow | | [Quantus](https://veinpool.fr/coin/qtc?lang=en) | QPoW |
| [Neurai](https://veinpool.fr/coin/xna?lang=en) | KawPow | | [Qubitcoin](https://veinpool.fr/coin/qubit?lang=en) | Qhash |
| [Satoxcoin](https://veinpool.fr/coin/satox?lang=en) | KawPow | | [Ycash](https://veinpool.fr/coin/yec?lang=en) | Equihash 192,7 |
| [Gaelium](https://veinpool.fr/coin/gael?lang=en) | KawPow | | [Feelcoin](https://veinpool.fr/coin/feel?lang=en) | RandomX |
| [Kerrigan](https://veinpool.fr/coin/krgn?lang=en) | KawPow · Equihash 192,7 | | [WAM Coin](https://veinpool.fr/coin/wam?lang=en) | RandomX |
| [Epic Cash](https://veinpool.fr/coin/epic?lang=en) | ProgPow | | [Zycord](https://veinpool.fr/coin/zcd?lang=en) | RandomX v2 |

👉 All ports and ready-made commands: **[veinpool/mining-configs](https://github.com/veinpool/mining-configs)**

🌍 Site in English: **https://veinpool.fr/?lang=en** · en français : **https://veinpool.fr**

### Quick start
```bash
# KawPow example (Ravencoin): wallet address = login, no account
t-rex -a kawpow -o stratum+tcp://veinpool.fr:3080 -u YOUR_ADDRESS.rig1 -p x
```

📫 contact@veinpool.fr
