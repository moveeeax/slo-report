# slo-report

> Error budget delivered as a message, not as a dashboard nobody opens.

**Status:** 🚧 In development

## Overview

Periodic SLO burn report delivered to Slack or Telegram, showing budget remaining, burn rate and which SLI moved, rather than a dashboard nobody opens.

## Features

- Computes budget remaining and multi-window burn rate (1h/5m and 6h/30m) per SLO
- Names the SLI that moved and by how much, instead of collapsing everything into one number
- SLO definitions in YAML with explicit good/total PromQL, versioned next to the service they describe
- Scheduled delivery to Slack or Telegram: a compact digest, with the per-SLI detail in the thread
- Quiet when the budget is healthy and nothing moved; loud when the fast burn window trips
- One-shot mode with a non-zero exit, so a release pipeline can refuse to ship on a burning budget

## Stack

Go + cobra, prometheus/client_golang API client for PromQL, slack-go/slack and go-telegram-bot-api for delivery.

## Usage

```bash
slo-report run --config slos.yaml --window 30d --deliver telegram --chat-id "$SLO_CHAT_ID"
```

## License

MIT
