---
layout: default
title: Installation
nav_order: 3
---

# Installation Guide

## Prerequisites

### System Requirements
- **Operating System**: Windows 10/11, macOS 10.15+, or Linux (Ubuntu 20.04+)
- **Python**: 3.10 or higher
- **Memory**: Minimum 2GB RAM
- **Storage**: At least 100MB for application and dependencies

### Required Accounts
- **Discord** - A Discord bot token ([Developer Portal](https://discord.com/developers/applications))
- **Anthropic** - An API key ([console.anthropic.com](https://console.anthropic.com/))

## Installation Steps

### 1. Clone the Repository
```bash
git clone https://github.com/Zhanjii/Link-Lens.git
cd Link-Lens
```

### 2. Create Virtual Environment (Recommended)
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -e ".[dev]"
```

### 4. Create a Discord Bot

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Click **New Application** - name it "Link Lens" (or anything)
3. Go to the **Bot** tab on the left sidebar
4. Click **Reset Token** and copy the token
5. Enable **MESSAGE CONTENT INTENT** under Privileged Gateway Intents
6. Go to **OAuth2 > URL Generator**
7. Select scopes: `bot`
8. Select permissions: `Send Messages`, `Read Message History`, `Add Reactions`, `Manage Messages`
9. Copy the generated URL, paste in browser, and add bot to a server

### 5. Create Discord Channels

Create these channels in your Discord server (names are configurable):

- `#drop-links` - You drop links here, bot watches this channel
- `#analysis-output` - Bot posts full analyses here
- `#daily-digest` - Bot posts morning summary here

### 6. Run the Application
```bash
python run.py
```

### 7. Configure Settings

1. Open **File > Settings**
2. Paste your Discord Bot Token and Anthropic API Key
3. Verify channel names match what you created
4. Click **Save Settings**
5. Click **Start Bot** on the Dashboard

## Dependencies

| Package | Purpose |
|---------|---------|
| `customtkinter` | GUI framework |
| `discord.py` | Discord bot |
| `anthropic` | Claude API client |
| `aiohttp` | Async HTTP requests |
| `beautifulsoup4` | Web content parsing |
| `youtube-transcript-api` | YouTube transcript extraction |

## Updating

```bash
git pull
pip install -e ".[dev]"
```
