<div align="center">

# 🎧 JeahyMusisBot

**Powerful Telegram Music Bot with smooth streaming & advanced controls**

[![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Telegram](https://img.shields.io/badge/Telegram-Bot-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/NotYourAnony)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Developer](https://img.shields.io/badge/Dev-NotYourAnony--Dev-purple?style=for-the-badge)](https://github.com/NotYourAnony-Dev)

> *Hey, I'm JeahyMusisBot — your premium music assistant 🎶*

---

</div>

## ✨ Features

- 🎵 **Multi-platform streaming** — YouTube, Spotify, Resso, Apple Music, SoundCloud
- 🔊 **Crystal-clear audio** — high-quality voice chat streaming via PyTgCalls
- ⚡ **24×7 uptime** — built for reliability with automatic reconnection
- 🎛️ **Full playback controls** — pause, resume, skip, stop, mute, unmute
- 📋 **Smart queue system** — queue up to 20 tracks with auto-suggestions when the queue ends
- 👫 **Couple feature** — randomly pairs users in the group for fun
- 🛡️ **Admin commands** — kick, ban, unban, tmute and more
- 🔁 **Session persistence** — playback state saved to MongoDB across restarts
- 🚀 **One-command deploy** — Render, Railway, Koyeb, VPS, Replit ready

---

## ⚙️ Setup Guide

### Prerequisites

| Requirement | Where to get it |
|---|---|
| `API_ID` & `API_HASH` | [my.telegram.org](https://my.telegram.org) |
| `BOT_TOKEN` | [@BotFather](https://t.me/BotFather) on Telegram |
| `ASSISTANT_SESSION` | Pyrogram string session (see below) |
| `OWNER_ID` | Your Telegram user ID |
| `MongoDB_url` | [MongoDB Atlas](https://www.mongodb.com/atlas) (free tier works) |

### Generate Assistant Session String

```bash
python3 -c "
from pyrogram import Client
with Client(':memory:', api_id=YOUR_API_ID, api_hash='YOUR_API_HASH') as app:
    print(app.export_session_string())
"
```

### Local / VPS Setup

```bash
# 1. Clone the repo
git clone https://github.com/NotYourAnony-Dev/JeahyMusicBot
cd JeahyMusicBot

# 2. Install system dependencies
sudo apt-get update && sudo apt-get install -y python3-pip ffmpeg git

# 3. Install Python packages
pip3 install -U -r requirements.txt

# 4. Configure environment
cp .env.example .env
nano .env          # fill in your values

# 5. Run
python3 main.py
```

> **Tip:** Use `tmux` to keep the bot alive after closing your SSH session:
> `sudo apt install tmux -y && tmux new -s jeahy` then run the bot inside.

---

## 🚀 Deployment

### Render

1. Fork this repo on GitHub
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your forked repo
4. Set environment variables from `.env.example`
5. Deploy — Render auto-detects `render.yaml`

### Railway

1. Fork this repo
2. Go to [railway.app](https://railway.app) → **New Project → Deploy from GitHub**
3. Add your environment variables in the Railway dashboard
4. Railway picks up `railway.json` automatically

### Koyeb

1. Fork this repo
2. Go to [koyeb.com](https://koyeb.com) → **Create App → GitHub**
3. Point to your fork — `koyeb.yaml` handles the rest
4. Fill in env vars and deploy

### Replit

1. Import repo via **Import from GitHub**
2. Add your secrets in the **Secrets** tab (same keys as `.env.example`)
3. Set run command to `python main.py`
4. Hit Run

### VPS with Docker (Production recommended)

```bash
# Install Docker
curl -fsSL https://get.docker.com | sh

# Build & run
docker build -t jeahy-music-bot .
docker run -d --env-file .env --name jeahy jeahy-music-bot
```

---

## 🔑 Environment Variables

Copy `.env.example` to `.env` and fill in each value.

| Variable | Required | Description |
|---|---|---|
| `API_ID` | ✅ | Telegram API ID from my.telegram.org |
| `API_HASH` | ✅ | Telegram API Hash from my.telegram.org |
| `BOT_TOKEN` | ✅ | Bot token from @BotFather |
| `ASSISTANT_SESSION` | ✅ | Pyrogram string session for userbot |
| `OWNER_ID` | ✅ | Your Telegram user ID (integer) |
| `MongoDB_url` | ✅ | MongoDB connection URI |
| `UPDATES_CHANNEL` | ❌ | Your updates channel link |
| `SUPPORT_GROUP` | ❌ | Your support group link |
| `START_ANIMATION` | ❌ | Custom video/GIF URL for /start |

---

## 📁 Project Structure

```
JeahyMusicBot/
├── main.py                         # Entry point — all bot logic
├── JeahyMusic/                     # Core library module
│   ├── infra/
│   │   ├── chrono/                 # Time formatting utilities
│   │   ├── concurrency/            # Privilege & concurrency helpers
│   │   └── vector/                 # YouTube orchestration & backup engine
│   ├── telegram_client/
│   │   ├── startup_hooks.py        # Pre-flight channel checks
│   │   └── vector_transport.py     # Media download & transport layer
│   └── vector_text_tools.py        # Unicode bold text helper
├── requirements.txt
├── .env.example                    # Template — copy to .env
├── Procfile                        # Heroku / Railway process declaration
├── Dockerfile                      # Container image
├── render.yaml                     # Render deployment config
├── railway.json                    # Railway deployment config
├── koyeb.yaml                      # Koyeb deployment config
└── README.md
```

---

## 📞 Support

Have a question or ran into a problem? Reach out:

- **Developer:** [NotYourAnony-Dev](https://github.com/NotYourAnony-Dev)
- **Telegram Support:** [@NotYourAnony](https://t.me/NotYourAnony)

---

<div align="center">

Made with ❤️ by **NotYourAnony-Dev**

</div>
