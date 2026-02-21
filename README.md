# Link Lens Documentation

Welcome to the official documentation for Link Lens - a Discord bot with desktop GUI that analyzes links via Claude API.

## Quick Links

- [User Guide](user-guide.md) - Complete guide to using the application
- [Installation](installation.md) - How to install and set up the application
- [Configuration](configuration.md) - Configure settings, channels, and triage
- [Changelog](CHANGELOG.md) - Version history and release notes

## About

Link Lens watches your Discord channels for links, triages them with Haiku, performs deep analysis with Sonnet, saves everything to a persistent archive, and posts a daily digest every morning.

### Features

- **Two-Pass Triage** - Haiku screens links first, Sonnet analyzes if relevant (~80% cost savings)
- **Channel-Based Architecture** - Drop links, analysis output, and daily digest channels
- **Daily Digest** - Morning summary of all overnight analyses
- **Persistent Memory** - Dated markdown files + searchable JSON index
- **Desktop GUI** - CustomTkinter interface with Dashboard, History, and Prompt Editor
- **20+ Color Themes** - Fully themeable dark/light interface

## Getting Help

- **Email:** zhanji@book.io
- **Issues:** [GitHub Issues](https://github.com/Zhanjii/Link-Lens/issues)

## System Requirements

- Windows 10/11, macOS 10.15+, or Linux
- Python 3.10 or higher
- Discord bot token
- Anthropic API key

---

Developed by Zhanji | Contact: zhanji@book.io
