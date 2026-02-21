---
layout: default
title: Configuration
nav_order: 4
---

# Configuration Guide

All settings are managed through **File > Settings** in the application. Settings are saved to `config/settings.json` and persist across restarts.

## Discord Settings

### Bot Token
Your Discord bot token from the [Developer Portal](https://discord.com/developers/applications). Required to connect to Discord.

### Channels

| Setting | Default | Description |
|---------|---------|-------------|
| Drop Links Channel | `drop-links` | Bot watches this channel for links |
| Analysis Output Channel | `analysis-output` | Full analyses are posted here |
| Daily Digest Channel | `daily-digest` | Morning summary posted here |

Enter channel names **without** the `#` prefix. Leave blank to disable a channel. DMs always work regardless of channel configuration.

## Claude API Settings

### API Key
Your Anthropic API key from [console.anthropic.com](https://console.anthropic.com/). Required for link analysis.

### Claude Model (Deep Analysis)
The model used for full link analysis. Options:
- `claude-sonnet-4-5-20250929` (recommended - best balance of quality/cost)
- `claude-haiku-4-5-20251001` (faster, cheaper)
- `claude-opus-4-6` (most capable, most expensive)

## Smart Triage (Two-Pass Routing)

### Enable Triage
When enabled, links go through a fast screening pass before deep analysis. Saves ~80% on API costs.

### Triage Model
The model used for the fast screening pass. Haiku is recommended for speed and cost.

### Relevance Threshold (1-10)
Links scoring below this threshold skip deep analysis and get a quick summary only. Default: 4.

- **Lower threshold (1-3):** More links get full analysis
- **Higher threshold (5-7):** Only highly relevant links get full analysis
- **React with magnifying glass:** Forces full analysis on any triaged link

## Daily Digest

### Digest Time
Set the hour and minute (24-hour format, local time) when the daily digest is posted. Default: 7:00 AM.

The digest includes:
- Total links analyzed
- Relevance breakdown
- Top picks with summaries
- Full list of everything processed

## Appearance

### Appearance Mode
- **Dark** - Dark background, light text (default)
- **Light** - Light background, dark text
- **System** - Follows your OS preference

### Color Theme
Choose from 20+ built-in color themes. The UI rebuilds immediately when you change themes.

## Other Settings

### Auto-Start Bot
When enabled, the bot starts automatically when you launch the application.

### Max Content Length
Maximum number of characters to extract from a web page for analysis. Default: 50,000. Increase for longer articles, decrease to reduce API costs.

## Settings File

Settings are stored in `config/settings.json`. This file is excluded from version control (`.gitignore`) to protect your tokens and API keys.

```json
{
  "discord_token": "your-token-here",
  "anthropic_api_key": "sk-ant-...",
  "claude_model": "claude-sonnet-4-5-20250929",
  "theme": "midnight",
  "appearance_mode": "dark",
  "drop_links_channel": "drop-links",
  "output_channel": "analysis-output",
  "digest_channel": "daily-digest",
  "enable_triage": true,
  "triage_model": "claude-haiku-4-5-20251001",
  "triage_threshold": 4,
  "digest_hour": 7,
  "digest_minute": 0,
  "auto_start_bot": false,
  "max_content_length": 50000
}
```
