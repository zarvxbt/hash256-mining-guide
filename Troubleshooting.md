# Troubleshooting

Common errors and how to fix them.

---

## No module named 'eth_account'

Cause: Python virtual environment is not activated.

Fix:
source .venv/bin/activate

You should see (.venv) at the start of your terminal line. Then run python3 miner.py again.

---

## invalid .env line: HASH256_PRIVATE_KEY

Cause: The line exists in .env but has no value assigned after =

Fix: Open .env and comment the line out:
nano .env

Change:
HASH256_PRIVATE_KEY=

To:
#HASH256_PRIVATE_KEY=0xYourPrivateKey

Or fill in your actual private key if you want auto-submit enabled.

---

## invalid .env line: HASH256_MAX_PENDING_SUBMISSIONS

Cause: Line has no value.

Fix:
nano .env

Change:
HASH256_MAX_PENDING_SUBMISSIONS

To:
HASH256_MAX_PENDING_SUBMISSIONS=1

---

## No connection adapters found for 'HASH256_RPC_URL=https://...'

Cause: RPC URL line in .env is malformed — duplicate line or wrong format.

Fix:
nano .env

Make sure the line looks exactly like this:
HASH256_RPC_URL=https://ethereum-rpc.publicnode.com

No spaces, no quotes, no duplicate prefix.

---

## metal backend unavailable

Cause: You are on Windows or Linux. Metal GPU is macOS only.

Fix:
nano .env

Change:
HASH256_BACKEND=metal

To:
HASH256_BACKEND=cpu

---

## Authentication failed for github.com

Cause: GitHub removed password authentication for git operations.

Fix: The miner repo is public — no login needed. Just clone directly:
git clone https://github.com/AuuCoder/hash

If it asks for credentials press Ctrl+C and try again without entering anything.

---

## bash: .venv/bin/activate: No such file or directory

Cause: Virtual environment was not created successfully.

Fix:
sudo apt-get update
sudo apt install python3.12-venv -y
python3 -m venv .venv
source .venv/bin/activate

---

## The virtual environment was not created successfully because ensurepip is not available

Cause: python3-venv package is missing on Ubuntu/WSL.

Fix:
sudo apt-get update
sudo apt install python3.12-venv -y
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

---

## Mining not starting / shows 未开始

Cause: Mining was not open on-chain yet when you ran the script.

Fix: Mining is now live. Just run the script again:
python3 miner.py

---

## Still stuck?

Drop a reply on Twitter @zarvxbt with your error message.

*Guide by @zarvxbt*
