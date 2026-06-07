# 🎮 Dare Play

> A real-time 2-player video call game — play Rock Paper Scissors, then dare the loser.

![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)
![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

---

## ✨ Features

- 🎥 **Live video calling** — face-to-face via WebRTC (PeerJS + Twilio TURN)
- ✊ ✋ ✌️ **Rock Paper Scissors** — real-time move resolution via Socket.IO
- 🎲 **Dare mode** — winner picks a random dare from the server list, or issues a verbal dare over video
- 🔗 **Shareable room links** — send a direct join URL to your opponent
- 📱 **PWA ready** — installable on Android and iOS, works offline (cached assets)
- 🔇 **Mic toggle** — mute/unmute without leaving the game

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Server | Node.js, Express |
| Real-time | Socket.IO |
| Video / WebRTC | PeerJS, Twilio TURN |
| Client | Vanilla JS, CSS |
| PWA | Service Worker, Web App Manifest |

---

## 🎯 How to Play

1. **Open the app** and enter your name.
2. **Create a room** — a 5-character room code is generated.
3. **Share the code** (or the auto-generated link) with a friend.
4. Your friend enters the code and **joins your room** — the video call starts automatically.
5. Both players **tap Rock, Paper, or Scissors** on the ring pad.
6. The winner can issue a **dare**:
   - 🎲 **Dare mode ON** (dice button) — a random dare is picked from the list.
   - 🎤 **Dare mode OFF** — the winner makes up a dare verbally on camera.
7. The loser completes the dare, then both tap **▶ Play Again** for the next round.

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- A [Twilio](https://www.twilio.com/) account (free tier works) for TURN relay credentials

### Installation

```bash
git clone https://github.com/kamandalewis/Dare-Play.git
cd Dare-Play
npm install
```

### Environment Variables

Copy the example file and fill in your values:

```bash
cp .env.example .env
```

| Variable | Required | Description |
|---|---|---|
| `TWILIO_SID` | ✅ | Your Twilio Account SID |
| `TWILIO_TOKEN` | ✅ | Your Twilio Auth Token |
| `PORT` | ❌ | Server port (default: `3000`) |

> **Where to find your Twilio credentials:** Log in to [console.twilio.com](https://console.twilio.com) → Dashboard → Account Info.

### Running Locally

```bash
npm start
```

Then open [http://localhost:3000](http://localhost:3000) in two browser tabs (or on two devices on the same network) to test.

---

## ☁️ Deploying

Dare Play requires a **persistent server with WebSocket support**. It will **not** work on serverless platforms (Vercel, Netlify Functions, Cloudflare Workers).

Recommended platforms:

| Platform | Notes |
|---|---|
| [Render](https://render.com) | Free tier available; set env vars in dashboard |
| [Railway](https://railway.app) | Easy deploy from GitHub |
| [Fly.io](https://fly.io) | Good for low-latency global deployment |

Set `TWILIO_SID` and `TWILIO_TOKEN` as environment variables in your platform's dashboard — do **not** commit your `.env` file.

---

## 📱 Installing as a PWA

**Android (Chrome):**
1. Open the app in Chrome.
2. Tap the browser menu → **Add to Home Screen**.

**iOS (Safari):**
1. Open the app in Safari.
2. Tap the **Share** button → **Add to Home Screen**.

---

## 🤝 Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

---

## 📄 License

This project is licensed under the [GNU General Public License v3.0](LICENSE).
