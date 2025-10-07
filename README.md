# Sartaj Ahmad — DHK Align LLC

Founder of **[DHK Align](https://dhkalign.com)** — building tools that bridge **Banglish ↔ English** and cultural context for the Bengali diaspora and anyone engaging with it.

### What I’m shipping now
- **DHK Align MVP** (prod):  
  - Frontend: React (Vite) SPA  
  - Edge: Cloudflare Worker (auth + KV cache + quotas)  
  - Origin: FastAPI on Fly.io (SQLite DB seeded; GPT fallback on miss)  
  - Fallback model: **gpt-4o-mini** (cheap, smart) → auto-inserts into DB  
  - Metrics: `/metrics` (Prometheus) with `db_hit`, `gpt_fallback`, `gpt_fail`, latency
- **Free tier**: everyday + cultural packs (safety ≤ 1), client-cached  
- **Pro tier**: slang, profanity, dialect packs (safety ≥ 2), API-key gated

### How it works (30s)
User → React SPA → CF Worker (KV cache, quotas) → Fly FastAPI → SQLite
└── GPT-4o-mini fallback (miss only) → auto-insert → DB/edge cache warm
### Status (live)
- Worker health: https://dhkalign-edge-production.tnfy4np8pm.workers.dev/edge/health  
- Origin health: https://backend.dhkalign.com/health  
- Metrics: https://backend.dhkalign.com/metrics

### Looking for early testers
- Free usage: try everyday phrases and tell me what’s missing.  
- Pro access: DM for a test key (or use Stripe test checkout).  
- Feedback welcome on slang/dialect accuracy, tone, and “sounds like us.”

### Tech choices (why)
- **CF Worker**: cheap, global, fast; shields origin; easy KV cache + quotas  
- **Fly.io**: simple container hosting; volume for SQLite; health checks  
- **SQLite**: perfect for curated packs; grows as GPT fills gaps; easy to back up  
- **gpt-4o-mini**: fast + cost-effective; good enough for slang/nuance; each miss only billed once

### Roadmap (near-term)
- Vite migration polish (dev UX + bundle size) ✅ in progress  
- `/version` endpoint (worker + origin) for release traceability  
- Simple metrics dashboard (Grafana/Alloy)  
- Sylheti / Chittagonian seed packs (pro)  
- Stripe hardening + receipts; one-time `/billing/key` fetch (already live)

### Contact
- Site: https://dhkalign.com  
- Email: **info@dhkalign.com**  
- Twitter/LinkedIn: DM for access / feedback

---

> **DHK Align LLC** — bridging cultural and linguistic gaps, one phrase at a time.
