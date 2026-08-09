# 🦞 Clow Studio v2.0

**10 specialized AI bots. One 15MB binary. Deploy anywhere.**

Clow Studio is a **production-grade Go server** that runs an entire ecosystem of AI assistants from a single process. Strategic analysis, travel, crypto security, job search, productization, investment, legal, wellness, global intelligence, African digital money — all in one deploy.

---

## 🚀 Quick Start (5 minutes)

```bash
# Prerequisites: Go 1.21+, flyctl (for cloud deploy)

git clone https://github.com/dnzengou/clow-studio-reloaded.git
cd clow-studio-reloaded
cp .env.template .env
# Edit .env with your bot tokens and LLM key

CGO_ENABLED=1 go build -ldflags="-s -w" -o clow-studio .
source .env && ./clow-studio
```

**Your bots are now live.** Dashboard at `http://localhost:8080/dashboard`.

---

## 🎯 What You Get

| Bot | Handle | What It Does |
|-----|--------|-------------|
| 🧠 **Deep Systems** | @deeptechx_bot | Strategic analysis, geopolitics, economy, water, wildfire, supply chain |
| 🗺️ **WanderSync** | @wandersync_bot | Travel AI — flights, trains, accommodation, destination intelligence |
| 🔒 **ChainShield** | @chaincypher_bot | Crypto security — contract risk, tokenomics, quantum readiness |
| 💼 **JobPulse** | @gigclow_bot | Job search AI — 65+ curated roles, resume review, salary insights |
| 🛠️ **Productize** | @productization_bot | Turn expertise into products — audit, package, price, launch |
| 📈 **Claw Invest** | @investclawd_bot | Investment research — screen, analyze, portfolio, risk scoring |
| ⚖️ **Legal Agent** | @legalclow_bot | Legal AI for founders — contracts, compliance, venture setup |
| 🌿 **Elara Wellness** | @elarawellness_bot | Holistic wellness — ancestral wisdom + modern science |
| 🌍 **WorldMonitor** | @wmagentic_bot | Global intelligence — 150+ sources, AI agent-driven briefings |
| 🌍💰 **AFRI Network** | @afri_agent_bot | African digital money — P2P order book, merchant economy |

**Plus:** Dashboard, QRNG (true quantum randomness), payment engine, evolution engine, circuit breakers, audit logs.

---

## 💰 Pricing

No free tier. No community edition. This is production infrastructure.

| Tier | Model | Price | What You Get |
|------|-------|-------|-------------|
| **Self-Host Pro** | You run it | **$29/mo** | Binary + updates + priority support + config templates |
| **Managed Solo** | We run it | **$49/mo** | 3 bots, 1 user, predefined personas |
| **Managed Pro** | We run it | **$99/mo** | 5 bots, 5 users, custom personas |
| **Managed Business** | We run it | **$199/mo** | 10 bots, 25 users, full customization |
| **Enterprise** | We run it | **$299/mo** | Unlimited, white-label, dedicated infra |

### Cost to Run (If Self-Hosted)

| Item | Cost |
|------|------|
| **Infrastructure** (Fly.io) | $3/mo |
| **LLM API** (DeepSeek) | ~$0.50/mo |
| **Total** | **~$3.50/mo** |

10 specialized AI assistants for the price of a coffee.

---

## 🏗️ Architecture

```
main.go
├── bot/         → Telegram polling, message routing, reactivity
├── config/      → Bot definitions, system prompts, skills
├── engine/      → Payment, evolution, QRNG, legal, AFRI, supply chain
├── db/          → SQLite persistence
├── llm/         → DeepSeek / Ollama client
├── web/         → Dashboard, metrics, health checks
├── platform/    → Telegram, Discord, WhatsApp adapters
└── util/        → Circuit breaker, sanitizer, logger
```

---

## 🛠️ Commands

```bash
CGO_ENABLED=1 go build -ldflags="-s -w" -o clow-studio .
source .env && ./clow-studio
flyctl deploy
bash one-shot-deploy.sh
```

---

## 🎤 Client deck

The pitch / productized-service deck for Clow Studio lives in [`web/deck.html`](web/deck.html) and ships in the same repo as the binary.

- **Live (GitHub Pages):** https://dnzengou.github.io/clow-studio-reloaded/deck.html
- **Landing:** https://dnzengou.github.io/clow-studio-reloaded/
- **Deep-link a slide:** `deck.html?slide=8` (opens on the pricing slide) or `?slide=14` (three-routes-in CTA)
- **Speaker mode:** press `N` for speaker notes, `S` to copy a shareable link, `P` for a print-friendly export.

### Serving `/deck` from the Go binary

Two integrations ship in the repo:

**1. Standalone `deck-server` (works today, stdlib-only, no CGO):**

```bash
go build -o deck-server ./cmd/deck-server
STATIC_DIR=./web PORT=8080 ./deck-server
# open http://localhost:8080/deck
```

Deploy it on Fly.io in place of the main app with the alternate config:

```bash
flyctl deploy --config fly.deck.toml
# → https://clow-studio-deck.fly.dev/deck
```

**2. Wired into the main `clow-studio` binary (via `internal/web/deck.go`):**

`main.go` calls `web.RegisterDeck(webServer.Mux(), web.DefaultStaticDir())`
right after building `webServer`. Once `internal/web/server.go` is in
place (with a `Mux() *http.ServeMux` accessor), the same binary serves
`/dashboard`, `/health`, `/metrics`, **and** `/deck` / `/deck.html` / `/`
off the same port. `STATIC_DIR` overrides the default lookup order
(`./web` → `/app/web`).

---

## 📄 License

MIT — free to use, modify, distribute. Managed hosting ($49-299/mo) and self-host support ($29/mo) available.

---

Built by [@desireyavro](https://t.me/desireyavro). 10 bots, 18+ skills, one binary, $3/mo.

*"The lightest AI ecosystem on the planet."*
