# A step-by-step guide to installing and connecting OpenClaw (local AI agent) with Tempo (wallet + payment layer) for automated Web3 + AI execution on your own Linux infrastructure.

🔹 Overview 
OpenClaw is a local AI agent that connects to models via API. Tempo acts as its wallet and payment layer for paid requests.



---



## Requirements

| Requirement | Details |
|-------------|---------|
| OS | Ubuntu 22.04 or 24.04 |
| Access | Terminal with `sudo` privileges |
| API Key | OpenAI, Anthropic, or Google |
| Wallet | Tempo account with funded balance |

> ⚠️ **Recommended:** Use a VPS for better security and uptime.

---

## Step 1 — Prepare Your System

Update packages and install core dependencies:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl git -y
```

---

## Step 2 — Install OpenClaw

> ⚠️ You can inspect the install script at `https://openclaw.ai/install.sh` before running it.

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

The installer will automatically:

- ✔ Check system requirements
- ✔ Install Node.js if needed
- ✔ Install OpenClaw
- ✔ Launch onboarding (select model + add API key)

---

## Step 3 — Verify Installation

```bash
openclaw --version
openclaw gateway status
```

Then open the dashboard:

```bash
openclaw dashboard
```

> 💡 **What is Gateway?**  
> Gateway is the core of OpenClaw — all messages, commands, tools, and agent tasks flow through it. If `gateway status` shows an error, setup is not yet complete. Run `openclaw onboard --install-daemon` to finish.

---

## Step 4 — Install Tempo

> ⚠️ You can inspect the install script at `https://tempo.xyz/install` before running it.

```bash
curl -fsSL https://tempo.xyz/install | bash
source ~/.tempo/env
```

> If `tempo` is not found after installation, open a new terminal or re-run `source ~/.tempo/env`.

---

## Step 5 — Add Required Modules

```bash
tempo add request
tempo add wallet
```

| Module | Purpose |
|--------|---------|
| `request` | Make paid requests to MPP services |
| `wallet` | Handle authorization and wallet access |

---

## Step 6 — Connect Your Wallet

1. Go to [tempo.xyz](https://tempo.xyz) → Register or log in → Confirm your email → Copy your Access Key
2. Run the following:

```bash
export TEMPO_ACCESS_KEY='your_access_key'
tempo wallet whoami
```

✔ If your wallet address is displayed — you're connected.

---

## Step 7 — Fund Your Wallet

Go to the **Tempo dashboard → Deposit** and add funds.

> ⚠️ Some features will not work without a funded balance.

---

## Step 8 — Test the Connection

```bash
tempo request https://mpp.dev/api/ping/paid
```

A successful response confirms:

- ✔ Tempo is installed
- ✔ Access key is working
- ✔ Wallet is connected
- ✔ Paid requests are active

---

## Step 9 — Load Available Services into OpenClaw

In the OpenClaw chat or dashboard, send this message:

```
Read this page: https://mpp.dev/services/llms.txt
```

This tells OpenClaw which services, endpoints, and models are available through Tempo.

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| `openclaw` not found | Close and reopen terminal, then run `openclaw --version` |
| `tempo` not found | Run `source ~/.tempo/env` or open a new terminal |
| Setup incomplete | Run `openclaw onboard --install-daemon` |
| Gateway error | Run `openclaw doctor` then `openclaw gateway status` |
| General shell issue | Run `source ~/.bashrc` |

---

## Summary

You now have a fully configured local AI agent connected to a Web3 payment layer.

| Component | Role |
|-----------|------|
| OpenClaw | Local AI agent |
| Tempo | Wallet + payment system |
| Together | Automated Web3 + AI execution |

➡️ **Your system is ready.**

---

## Learn More

- 💬 **Discord:** `atkw3`
- 🐦 **Twitter / X:** [@Ladin90A](https://twitter.com/Ladin90A)
- 🐙 **GitHub:** [@oxatik](https://github.com/oxatik)


