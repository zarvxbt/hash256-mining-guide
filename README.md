# HASH256 Mining Guide

![status](https://img.shields.io/badge/mining-live-brightgreen)
![platform](https://img.shields.io/badge/platform-mac%20%7C%20windows-blue)

Community guide for running the HASH256 miner on Mac and Windows. No fluff. Step by step. Tested.

---

## What is HASH256

HASH256 is an on-chain Proof of Work mining protocol on Ethereum mainnet. Runs from your terminal. No ASIC needed.

- Solve keccak256(challenge || nonce) to earn HASH tokens
- Challenge is wallet-bound — each address gets a unique puzzle
- Difficulty adjusts on-chain per epoch automatically
- Solo mine from your terminal. No pool needed.
- Reward: 100 HASH per successful mine

**Contract:** 0xAC7b5d06fa1e77D08aea40d46cB7C5923A87A0cc
**Project:** https://hash256.org
**Miner Repo:** https://github.com/AuuCoder/hash

---

## Requirements

| Requirement | Details |
|---|---|
| Wallet | Burner ETH wallet — never use your main |
| ETH | ~0.0005 ETH for gas fees |
| Python | Python 3.x |
| Rust | For compiling the high-speed hash worker |
| Time | ~10 minutes |

---

## Guides

- [Windows Setup](./Windows-Guide.md)
- [Mac Setup](./Mac-Guide.md)
- [Troubleshooting](./Troubleshooting.md)
- [Updates](./Update.md)

---

## Expected Output

[worker] 181,272,576 hashes | 15.10 MH/s | 12.0s
[hit] nonce=0x...
[tx] submitted 0x... pending=1
[receipt] status=1 ✓

status=1 means confirmed. Reward received.

---

## Important Notes

- Never use your main wallet private key
- Use Flashbots RPC to prevent bots from frontrunning your transactions
- Apple Silicon Metal GPU runs 2-3x faster than CPU
- Gas per submission roughly $2-5 depending on network

---

*Guide by @zarvxbt*
