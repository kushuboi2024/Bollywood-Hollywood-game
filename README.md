# 🎬 Bollywood / Hollywood

A movie guessing game — like Hangman, but for film lovers. Guess the movie letter by letter before you run out of lives. Play solo or challenge a friend on a different device.

---

## How to Play

Vowels and spaces are revealed automatically. You guess the consonants and numbers one at a time using the on-screen keyboard (or your physical keyboard). You have **9 lives** — each wrong guess costs one.

**Single Player** — pick a movie from the preloaded list and guess it yourself.  
**2 Player** — one player sets a custom movie, the other guesses it live across any two devices.

---

## Features

### Single Player
- 56 preloaded movies across Bollywood and Hollywood
- Filter by **category** (Bollywood / Hollywood / All) and **difficulty** (Easy / Medium / Hard)
- Difficulty is colour-coded — green for easy, gold for medium, red for hard
- Streak tracker with personal best saved in the browser (survives page refresh)
- "Give up" option to reveal the answer and move on
- After each round, jump straight to the next random movie

### 2 Player (Live Multiplayer)
- Player 1 creates a room and gets a **5-letter room code**
- Player 2 joins on any device using that code
- Players **alternate roles** each round — whoever guesses becomes the setter next round
- **3 rounds** per game, 1 point awarded per correct guess
- Scores shown live on both screens throughout the game
- Category (Bollywood / Hollywood) must be selected before each round — it's shown as a hint to the guesser
- Host can restart for a rematch after the game ends

### General
- Numbers (0–9) supported — movies like *3 Idiots* and *1917* work fine
- Words never split mid-wrap — long titles always break cleanly between words
- Physical keyboard supported — just type a letter or number to guess
- Fully responsive, works on mobile and desktop

---

## Getting Started

### 1. Clone or download

```bash
git clone https://github.com/YOUR_USERNAME/bollywood-hollywood.git
```

Or simply download `index.html` — it's a single self-contained file, no build step needed.

### 2. Single Player — works immediately

Open `index.html` in any browser. No setup required.

### 3. Multiplayer — requires Firebase

Multiplayer syncs game state between devices using [Firebase Realtime Database](https://firebase.google.com/products/realtime-database) (free).

#### Set up Firebase

1. Go to [console.firebase.google.com](https://console.firebase.google.com) and create a project
2. In the left sidebar, go to **Databases & Storage → Realtime Database**
3. Click **Create Database** → choose a region → select **Start in test mode** → Enable
4. Copy the database URL — it looks like:
   ```
   https://your-project-default-rtdb.asia-southeast1.firebasedatabase.app
   ```
5. Open `index.html` in a text editor and find this line near the top of the `<script>`:
   ```js
   const FIREBASE_DB_URL = "PASTE_YOUR_DATABASE_URL_HERE";
   ```
6. Replace the placeholder with your URL:
   ```js
   const FIREBASE_DB_URL = "https://your-project-default-rtdb.asia-southeast1.firebasedatabase.app";
   ```
7. Save the file

Once configured, the 2 Player tab will show a green **"Firebase connected"** badge.

> **Note:** Firebase test mode allows open reads and writes for 30 days. After that, update your database rules in the Firebase console to keep it working.

---

## Hosting on GitHub Pages

1. Create a new **public** repository on GitHub
2. Upload `index.html` (and this `README.md`) to the repo
3. Go to **Settings → Pages**
4. Under Source, select **Deploy from a branch** → `main` → `/ (root)` → Save
5. Your game will be live at `https://YOUR_USERNAME.github.io/REPO_NAME` within a minute

---

## Project Structure

```
index.html   ← entire app (HTML + CSS + JS in one file)
README.md    ← this file
```

No dependencies, no npm, no build tools. Just one HTML file.

---

## Movie List

The game includes 56 preloaded movies:

| Category   | Count | Examples |
|------------|-------|---------|
| Bollywood  | 28    | Sholay, 3 Idiots, Dangal, Tumbbad, Gangs of Wasseypur |
| Hollywood  | 28    | The Godfather, Inception, Parasite, 1917, Memento |

Difficulties are assigned as follows — **Easy** means widely known titles, **Medium** means popular but less mainstream, **Hard** means cult classics or less recognisable titles.

---

## Tech Stack

- Vanilla HTML, CSS, JavaScript — no frameworks
- [Firebase Realtime Database](https://firebase.google.com) — multiplayer room sync (REST API, no SDK)
- [Google Fonts](https://fonts.google.com) — Playfair Display + DM Sans
- `localStorage` — streak / best score persistence

---

## Origin

This started as a Python terminal game using `getpass` to hide the movie name. It was rebuilt into a full web app with single player, multiplayer, Firebase sync, difficulty filters, streak tracking, and a proper UI — all as a single `index.html` file.

---

## License

MIT — do whatever you want with it.
