# Contributing to Dare Play

Thanks for taking the time to contribute! Here's everything you need to get set up and submit a clean pull request.

---

## Table of Contents

- [Local Setup](#local-setup)
- [Project Structure](#project-structure)
- [How to Contribute](#how-to-contribute)
- [Code Style](#code-style)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)

---

## Local Setup

1. **Fork** the repository and clone your fork:

   ```bash
   git clone https://github.com/YOUR_USERNAME/Dare-Play.git
   cd Dare-Play
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Configure environment variables:**

   ```bash
   cp .env.example .env
   ```

   Fill in `TWILIO_SID` and `TWILIO_TOKEN` with your Twilio credentials (free account works fine). See [README.md](README.md) for details.

4. **Start the dev server:**

   ```bash
   npm start
   ```

   Open [http://localhost:3000](http://localhost:3000). To test two players locally, open a second tab or use two different browsers.

---

## Project Structure

```
Dare-Play/
├── server.js          # Express + Socket.IO server, room & game logic
├── public/
│   ├── index.html     # Single HTML file — lobby screen + game screen
│   ├── app.js         # Client-side logic (Socket.IO, PeerJS, UI state)
│   ├── style.css      # All styles — dark neon theme
│   ├── sw.js          # Service Worker for PWA caching
│   └── manifest.json  # PWA web app manifest
├── .env.example       # Environment variable template
├── package.json
└── LICENSE
```

**Key things to know:**

- **Rooms are in-memory** (`rooms` object in `server.js`) — they are lost on server restart. This is intentional for now; persistence is a future improvement.
- **Video** uses PeerJS (WebRTC) with Twilio TURN for NAT traversal. The server exchanges Peer IDs via Socket.IO events (`peer-id`).
- **Game flow:** `create-room` → `join-room` → `round-start` → `choose-move` → `round-result` → `ready-next` → repeat.
- **Dare mode** is a per-player toggle. The winner's preference is used when resolving the round in `resolveRound()`.

---

## How to Contribute

1. **Create a branch** from `main` with a descriptive name:

   ```bash
   git checkout -b fix/modal-name-inconsistency
   # or
   git checkout -b feat/session-score-tracker
   ```

2. **Make your changes.** Keep commits focused — one logical change per commit.

3. **Test locally** with two browser windows before opening a PR. Check that:
   - Room creation and joining works
   - Video call establishes
   - Moves resolve correctly (win / lose / draw)
   - Dare mode toggles as expected
   - The PWA installs correctly (if you touched `manifest.json` or `sw.js`)

4. **Push your branch** and open a Pull Request against `main`.

5. In your PR description, briefly explain:
   - What the change does
   - Why it's needed
   - How you tested it

---

## Code Style

There's no linter configured yet — follow the style of the existing code:

- **2-space indentation**
- **`const` / `let`** — no `var`
- **Socket.IO event names** use `kebab-case` (e.g. `choose-move`, `round-result`)
- **DOM IDs** use `camelCase` (e.g. `roomCodeDisplay`, `diceToggleBtn`)
- Keep server logic in `server.js` and client logic in `public/app.js` — don't mix concerns

---

## Reporting Bugs

Open a [GitHub Issue](https://github.com/kamandalewis/Dare-Play/issues) and include:

- What you expected to happen
- What actually happened
- Steps to reproduce
- Browser and OS (video/WebRTC bugs are often browser-specific)

---

## Suggesting Features

Open an Issue with the label **`enhancement`** and describe:

- The problem it solves or the experience it improves
- A rough idea of how it could work

Some ideas already on the radar:

- [ ] Session score tracker (wins / losses / draws per session)
- [ ] Custom dare input (winner types their own dare)
- [ ] Reconnection handling on socket drop
- [ ] More dare categories (mild / spicy toggle)
- [ ] Room password protection
