# Security Checklist

## API Key Protection
- [x] API key encrypted via ZeroClaw's `enc2:` system — never stored as plaintext
- [x] API key saved in a password manager (not in notes, group chats, or code files)
- [x] OpenRouter hard spending limit set to $10 to prevent runaway costs

## Server Access
- [x] VPS password stored in a password manager
- [x] Forbidden paths configured — `/etc`, `/root`, `~/.ssh` are permanently blocked
- [x] Agent workspace restricted to designated directory (`workspace_only = true`)

## Agent Permissions
- [x] Autonomy level set to `supervised` — agent asks before sensitive operations
- [x] Telegram allowlist configured — only my account can send commands
- [x] Sub-agents (Nova) scoped to only the tools they need — no overstepping

## Cost Control
- [x] Daily spend cap configured in ZeroClaw's `[cost]` section
- [x] OpenRouter credit balance monitored regularly

## Data Sovereignty
- [x] Self-hosted on personal VPS — no third-party platform holds my data
- [x] No API keys shared with cloud-hosted agent services
