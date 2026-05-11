# Windows Setup Guide (WSL/Ubuntu)

Full step-by-step guide for running the HASH256 miner on Windows using WSL (Ubuntu).

---

## Prerequisites

- Windows 10 or 11
- WSL installed with Ubuntu
- A burner ETH wallet address and private key
- ~0.02 ETH in that wallet for gas fees

---

## Step 1 — Check Dependencies

Open Ubuntu terminal and run:

python3 --version
rustc --version
cargo --version

If Rust is missing:

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

Restart terminal after installing Rust.

---

## Step 2 — Clone the Repo

git clone https://github.com/AuuCoder/hash
cd hash

Note: Public repo. Do not enter GitHub password when prompted — just clone directly.

---

## Step 3 — Install Python venv Package

sudo apt-get update
sudo apt install python3.12-venv -y

---

## Step 4 — Set Up Python Environment

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

You should see (.venv) at the start of your terminal line after activation.
Rust worker compiles automatically on first run. Takes 1-2 mins. Normal.

---

## Step 5 — Configure .env

cp .env.example .env
nano .env

Set the following values:

HASH256_RPC_URL=https://ethereum-rpc.publicnode.com
HASH256_MINER_ADDRESS=0xYourBurnerWalletAddress
HASH256_PRIVATE_KEY=0xYourBurnerWalletPrivateKey
HASH256_BACKEND=cpu
HASH256_SUBMIT=1
HASH256_SUBMIT_RPC_URL=https://rpc.flashbots.net/fast
HASH256_MAX_PENDING_SUBMISSIONS=1

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
[worker] 181,272,576 hashes | 15.10 MH/s | 12.0s
[hit] nonce=0x...
[tx] submitted 0x... pending=1
[receipt] status=1 ✓

status=1 = confirmed. Reward received.

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
