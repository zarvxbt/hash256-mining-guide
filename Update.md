# Updates

Latest news and status updates for HASH256 mining.

---

## 11 May 2026 — Mining is Live

HASH256 on-chain mining is now open on Ethereum mainnet.

- Mining contract is active
- Submissions are being accepted
- Reward: 100 HASH per successful mine
- Era 1 is live

If you already set up the miner, update your .env:

HASH256_PRIVATE_KEY=0xYourBurnerPrivateKey
HASH256_SUBMIT=1
HASH256_SUBMIT_RPC_URL=https://rpc.flashbots.net/fast

Then restart:
python3 miner.py

---

## Pre-launch — Search Mode

Before mining went live, the miner ran in search-only mode:

- No transactions submitted
- No ETH needed
- Miner searched for valid nonces in the background
- Output showed 未开始 (not started)

That phase is over. Mining is live now.

---

*Guide by @zarvxbt*
