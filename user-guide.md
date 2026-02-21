---
layout: default
title: User Guide
nav_order: 2
---

# User Guide

## Overview

Link Lens is a Discord bot with a desktop GUI that automatically analyzes links you share. Drop a link in a Discord channel or DM, and the bot triages it with Haiku, does a deep analysis with Sonnet, saves everything to a persistent archive, and posts a daily digest every morning.

## Getting Started

### 1. Launch the Application

```bash
python run.py
```

The main window opens with three tabs: **Dashboard**, **History**, and **Prompt Editor**.

### 2. Configure Settings

Open **File > Settings** and fill in:

- **Discord Bot Token** - From the Discord Developer Portal
- **Anthropic API Key** - From console.anthropic.com
- **Channel Names** - Match the channels you created in Discord
- Click **Save Settings**

### 3. Start the Bot

Click **Start Bot** on the Dashboard tab, or use **File > Start Bot** from the menu.

## Discord Channels

Link Lens uses three dedicated channels (names are configurable in Settings):

| Channel | Purpose |
|---------|---------|
| `#drop-links` | Drop links here — bot watches and analyzes |
| `#analysis-output` | Full analyses posted for organized browsing |
| `#daily-digest` | Morning summary of all overnight analyses |

DMs always work as a fallback, even without server channels configured.

## Two-Pass Triage (Smart Model Routing)

When enabled, every link goes through two passes:

1. **Pass 1 (Haiku - fast/cheap):** Scores relevance 1-10, one-sentence summary (~2 seconds)
2. **Pass 2 (Sonnet - deep):** Full analysis with your custom prompt (~15-30 seconds)

Links scoring **below the threshold** (default: 4) skip the deep analysis. This saves ~80% on API costs for low-relevance links.

You can force full analysis on any triaged link by reacting with the magnifying glass emoji on the bot's reply.

### Configuring Triage

In **File > Settings** under "Smart Triage":

- **Enable/disable** the triage system
- **Choose triage model** (Haiku recommended for speed/cost)
- **Set threshold** (1-10) - higher means more selective

## Daily Digest

Every day at the configured time (default: 7:00 AM), the bot posts a summary to `#daily-digest`:

- Total links analyzed
- Relevance breakdown (High / Medium / Low)
- Top picks with summaries
- Full list of everything processed

Configure the digest time in **File > Settings** under "Daily Digest".

## Memory System

All analyses are saved to the `memory/` folder:

- `memory/2026-02-09.md` - All analyses from that day
- `memory/index.json` - Searchable index of every link

This is your persistent, searchable archive. It survives app restarts.

## Prompt Editor

The **Prompt Editor** tab lets you customize what Claude focuses on during analysis:

- Change it to focus on JavaScript/React instead of Python
- Modify it to evaluate tools for video editing workflows
- Add specific criteria relevant to your current project

The prompt updates immediately - no bot restart needed.

## Appearance

### Appearance Mode

Choose between **Dark**, **Light**, or **System** mode in **File > Settings** under "Appearance & Other".

### Color Themes

Link Lens ships with 20+ color themes. Change the theme in **File > Settings** under "Color Theme". The UI rebuilds immediately with the new colors.

## Tips

- DMs always work, even without server channels configured
- Multiple links in one message are each analyzed separately
- YouTube links auto-extract transcripts for better analysis
- Leave a channel name blank in Settings to disable that channel
- All settings update the live bot instantly - no restart needed

## Troubleshooting

### "Invalid Discord token"
Regenerate the token in Developer Portal > Bot tab.

### "Invalid API key"
Full key starts with `sk-ant-`. Check console.anthropic.com.

### "Bot not responding to DMs"
- Enable **MESSAGE CONTENT INTENT** in Developer Portal
- Share at least one server with the bot

### "Channel NOT FOUND in status bar"
- Channel name in Settings must match exactly (no `#` prefix)
- Bot needs permission to read/write in that channel

### "Transcript unavailable for YouTube"
Some videos don't have transcripts. The bot still analyzes available metadata.
