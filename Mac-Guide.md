# Mac Setup Guide (Apple Silicon)

Full step-by-step guide for running the HASH256 miner on Mac. Apple Silicon gets Metal GPU backend — significantly faster than CPU.

---

## Prerequisites

- Mac with Apple Silicon (M1/M2/M3) or Intel
- A burner ETH wallet address and private key
- ~0.02 ETH in that wallet for gas fees

---

## Step 1 — Install Homebrew (if missing)

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

---

## Step 2 — Install Dependencies

brew install python

Install Rust:
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

Restart terminal after, then verify:
python3 --version
rustc --version

---

## Step 3 — Clone the Repo

git clone https://github.com/AuuCoder/hash
cd hash

---

## Step 4 — Set Up Python Environment

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

You should see (.venv) at the start of your terminal line.
Rust worker compiles automatically on first run. Takes 1-2 mins. Normal.

---

## Step 5 — Configure .env

cp .env.example .env
nano .env

Set the following values:

HASH256_RPC_URL=https://ethereum-rpc.publicnode.com
HASH256_MINER_ADDRESS=0xYourBurnerWalletAddress
HASH256_PRIVATE_KEY=0xYourBurnerWalletPrivateKey
HASH256_BACKEND=metal
HASH256_BATCH_SIZE=1048576
HASH256_SUBMIT=1
HASH256_SUBMIT_RPC_URL=https://rpc.flashbots.net/fast
HASH256_MAX_PENDING_SUBMISSIONS=1

Apple Silicon: use HASH256_BACKEND=metal (GPU, 2-3x faster)
Intel Mac: use HASH256_BACKEND=cpu instead

Important: Every line must have a value after =
Comment unused lines with # at the start

Save: Ctrl+O → Enter → Ctrl+X

---

## Step 6 — Run the Miner

python3 miner.py

---

## Step 7 — Verify It Is Working

Good output:

[rpc] chain_id=1 block=...
[worker] 181,272,576 hashes | 45.30 MH/s | 12.0s
[hit] nonce=0x...
[tx] submitted 0x... pending=1
[receipt] status=1 ✓

status=1 = confirmed. Reward received.
Apple Silicon typically achieves much higher MH/s via Metal GPU.

---

## Restarting the Miner

Every new terminal session run this first:

cd ~/hash
source .venv/bin/activate
python3 miner.py

---

## Why Flashbots RPC

Public mempool = bots frontrun your valid nonce before it confirms.
Flashbots sends directly to validators, bypassing public mempool.
Always use https://rpc.flashbots.net/fast for submissions.

---

See Troubleshooting.md for common errors and fixes.

*Guide by @zarvxbt*
