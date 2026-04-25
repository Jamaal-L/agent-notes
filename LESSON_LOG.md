# Lesson Log
Super Individual Founding Workshop — Week by Week

---

## Week 1 — Build
**Goal:** Get the agent online and talking to you.

**What I did:**
- Purchased a Hetzner VPS via Zeabur (Ubuntu 22.04, 2 vCPU, 4GB RAM)
- Connected via SSH and learned basic Linux navigation
- Installed Rust, build dependencies, and ZeroClaw from source
- Set up an OpenRouter API key (Route C) and configured it as an environment variable
- Created a Telegram bot via BotFather, configured the allowlist so only my account can issue commands
- Sent my first message to the agent and received a reply
- Set up ZeroClaw as a persistent background service

**Key takeaway:** The hardest part isn't the tech — it's trusting the process. Once SSH clicks, everything else follows.

---

## Week 2 — Secure
**Goal:** Lock down permissions and protect API keys.

**What I did:**
- Learned the three autonomy levels (ReadOnly, Supervised, Full) and kept mine on Supervised
- Configured forbidden paths to block access to `/etc`, `/root`, and `~/.ssh`
- Verified API key is encrypted via ZeroClaw's `enc2:` system — never stored in plaintext
- Set a hard spending limit on OpenRouter ($10) and a daily cost cap in ZeroClaw's `[cost]` section
- Configured `auto_approve` for routine tasks like cron scheduling
- Understood the three layers of defence: Telegram allowlist, forbidden paths, and cost circuit-breaker

**Key takeaway:** Security isn't optional — it's the foundation. Set your hard limits before you give your agent any real power.

---

## Week 3 — Upgrade
**Goal:** Build a sub-agent (Nova) and learn delegation.

**What I did:**
- Designed a workflow for YouTube video analysis
- Created Nova's four identity files: IDENTITY.md, SOUL.md, USER.md, STYLE.md
- Installed Node.js and yt-dlp on the VPS
- Configured the YouTube MCP server in config.toml
- Registered Nova as a named route via Telegram with scoped tool access
- Created SKILL.md to define Nova's task flow and output format

**Blockers I hit and how I solved them:**
1. **YouTube authentication error** — The original `@anaisbetts/mcp-youtube` package broke because YouTube tightened bot detection. Fix: migrated to the Apify YouTube MCP server, which uses an API token instead of browser cookies.
2. **OpenRouter credits ran out** — Got a 402 error because the agent requested 64k tokens but my balance couldn't cover it. Fix: topped up $5 on OpenRouter. Also learned I could lower `max_tokens` or switch to a cheaper model like `google/gemini-2.0-flash`.
3. **Tool registration mismatch** — After switching to Apify, Nova's allowed tools needed updating from `youtube__download_youtube_url` to `apify-youtube__streamers--youtube-scraper` and `apify-youtube__get-actor-output`.

**Key takeaway:** Delegation is the real unlock. Once you see the main agent hand off a task to Nova and get a structured brief back, you realise you're no longer using a tool — you're running a team.

---

## Week 4 — Document
**Goal:** Turn everything into a public knowledge base.

**What I did:**
- Created the `agent-notes` GitHub repo
- Pushed SOUL.md, Security Checklist, and this Lesson Log
- Building a knowledge base site with GitHub Pages

**Key takeaway:** If you can't explain what you built, you don't fully own it yet. Documentation forces clarity.
