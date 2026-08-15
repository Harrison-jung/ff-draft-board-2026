# 🏈 Fantasy Draft Board 2026 — .5 PPR (Live Sync)

A real-time collaborative fantasy football draft board with ESPN styling, powered by Firebase.

## Quick Start (10 minutes)

### 1. Create a Firebase Project (free, no credit card)

1. Go to [firebase.google.com](https://firebase.google.com) → **Add Project**
2. Name it `ff-draft-board-2026` → skip Google Analytics → **Create**
3. In the console, click **Build → Realtime Database → Create Database**
4. Choose your region → **Start in test mode** → **Enable**
5. Click the ⚙️ gear → **Project Settings → General**
6. Scroll to **Your apps** → click the **</>** (Web) icon
7. Register app (any nickname) → copy the `firebaseConfig` object

### 2. Set Up Your Repo

Your GitHub repo is already created. Clone it and add the project files:

```bash
git clone https://github.com/YOUR-USERNAME/ff-draft-board-2026.git
cd ff-draft-board-2026
```

Copy all project files into this directory so your structure looks like:

```
ff-draft-board-2026/
├── .firebaserc
├── .gitignore
├── firebase.json
├── database.rules.json
├── public/
│   └── index.html
└── README.md
```

### 3. Configure Firebase

Edit `.firebaserc` and replace `YOUR-FIREBASE-PROJECT-ID` with your actual Firebase project ID (e.g., `ff-draft-board-2026`).

### 4. Install Firebase CLI & Deploy

```bash
npm install -g firebase-tools
firebase login
firebase deploy
```

Your board is now live at `https://ff-draft-board-2026.web.app`

### 5. Push to Git

```bash
git add .
git commit -m "initial draft board"
git push origin main
```

### 6. First Visit

1. Open the URL → paste your `firebaseConfig` JSON → enter your name → **Connect**
2. Share the URL with your co-manager — they paste the same config + their name
3. All edits sync in real time between you

## Features

- **Real-time sync** — all edits, flags, and reorders sync instantly
- **Research Board** — full player database with editable fields
- **My Draft Board** — 🚀 rocketed players grouped by round
- **Injury tracker** — 🏥 flags with editable notes (pre-populated with Aug 2026 camp injuries)
- **Bust flags** — 💣 mark players to avoid
- **Drag-and-drop** — reorder your board
- **Vegas team scoring ranks** — implied points from betting lines
- **Hayden Winks & Josh Norris** — pros/cons sourced from Yahoo Fantasy analysts
- **Export** — JSON export + Save HTML for offline snapshots
- **User presence** — see who's online editing

## Data Sources

| Data | Source |
|------|--------|
| ADP | Fantasy Football Calculator (half-PPR, 12-team, Aug 2026) |
| Analyst Pros/Cons | Hayden Winks & Josh Norris via Yahoo Sports |
| Vegas Team Ranks | RotoWire / Ian Hartitz (implied scoring) |
| Training Camp Injuries | Yahoo, CBS Sports, SI, FantasyPros (Aug 2026) |

## Security Note

The default `database.rules.json` is open (read/write for anyone). For a two-person board this is fine. If you want to lock it down:

```json
{
  "rules": {
    "boards": {
      "$boardId": {
        ".read": "auth != null",
        ".write": "auth != null"
      }
    }
  }
}
```

Then enable **Authentication** in Firebase Console → **Email/Password** and add your accounts.

## Git Workflow

```bash
# Make changes
cd ff-draft-board-2026
git add .
git commit -m "updated round 5 targets"
git push origin main

# Deploy to Firebase
firebase deploy
```

### Auto-Deploy on Push (optional)

```bash
firebase init hosting:github
```

This connects your `ff-draft-board-2026` GitHub repo so every `git push` to `main` auto-deploys to Firebase. No manual `firebase deploy` needed after setup.

## Recommended: Use Claude Code for Ongoing Work

Once your repo is cloned locally, open Claude Code in the `ff-draft-board-2026` directory for any future changes — editing players, adding features, deploying updates. It runs commands directly in your terminal.

## License

Personal use. Player data and analyst insights are sourced from public fantasy football content.
