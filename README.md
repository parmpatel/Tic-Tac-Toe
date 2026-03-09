# 🎮 Tic Tac Toe — Material You Edition

A beautifully crafted, fully-featured Tic Tac Toe game built with pure **HTML, CSS & JavaScript** — no frameworks, no dependencies. Inspired by Google's **Material You (Material Design 3)** design language with smooth animations, persistent scores, and an unbeatable AI.

---

## ✨ Features

### 🎨 Design & UI
- **Material You (MD3)** color system with dynamic theming tokens
- **Light & Dark mode** with one-click toggle — preference saved across sessions
- Animated gradient **background blobs** that float continuously
- **DM Sans** font for a clean, modern, highly readable look
- Fully **responsive layout** — works beautifully on mobile, tablet, and desktop

### 🕹️ Gameplay Modes
| Mode | Description |
|------|-------------|
| 👥 2 Players | Local multiplayer — take turns on the same device |
| 🤖 Easy AI | Random moves with occasional smart plays (30% minimax) |
| 🧠 Hard AI | Unbeatable AI using the **Minimax algorithm** |

### 🔢 AI Logic
- Implements the classic **Minimax algorithm** for perfect play in Hard mode
- Easy mode blends random moves with occasional optimal moves for a fun challenge
- AI correctly handles both X and O marks depending on player selection

### 🎭 Animations
- ✏️ **SVG draw-on animation** for X lines and O circles
- 🏆 **Win line** drawn across the board in the winner's color
- 🎊 **Confetti burst** with circles, rectangles, stars & triangles on every win
- ⭐ **Floating emoji stars** (✨⭐🌟💫🎊) pop from each winning cell
- 🎉 **Animated winner pill** drops from the top of the screen and bounces
- 💧 **Ripple effect** on cell tap/click
- 🔀 **Shake animation** when clicking an already-taken cell
- 🃏 Win cells **wobble and rotate** for a joyful pop effect
- 👻 **Ghost preview** of your mark on cell hover

### 🧩 iOS-Style Segmented Control
- The mode selector uses a **fluid sliding pill** that glides between buttons
- Smooth physics-based cubic-bezier easing — exactly like native iOS controls
- Pill repositions correctly on window resize

### 👤 X or O Picker (Single Player)
- Choose to play as **X (go first)** or **O (go second)** before each match
- Appears only in single-player modes (Easy AI / Hard AI)
- AI automatically adjusts its mark based on your selection
- If you pick O, the AI makes the first move automatically

### 📊 Scoreboard
- Tracks wins for **X**, **O**, and **Ties** across multiple rounds
- Active player's score card **lifts and highlights**
- Score numbers animate with a **pop/bounce** when updated

### 💾 Persistent Storage
All preferences and scores are saved to `localStorage` and restored on next visit:

| Data | Saved When |
|------|------------|
| X / O / Tie scores | After every game |
| Game mode | When you switch modes |
| Your mark (X or O) | When you pick in single player |
| Theme (Light / Dark) | When you toggle |

Scores survive browser close, refresh, and reopen. Reset button clears both the display and stored scores.

---

## 🚀 Getting Started

### No installation required!

Just open the file in any modern browser:

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/tictactoe-material-you.git

# Open in browser
open tictactoe.html
# or double-click the file in your file explorer
```

> ✅ Works 100% offline — no server, no build step, no `npm install`.  
> 🌐 Font (DM Sans) loads from Google Fonts — requires internet for first load, cached after that.

---

## 📁 Project Structure

```
tictactoe-material-you/
│
├── tictactoe.html      # Everything — HTML + CSS + JS in one file
└── README.md           # This file
```

The entire game is self-contained in a **single HTML file** (~860 lines), making it trivially easy to share, fork, or embed.

---

## 🧠 How the AI Works

### Hard Mode — Minimax Algorithm
The Hard AI uses the [Minimax algorithm](https://en.wikipedia.org/wiki/Minimax), a classic recursive decision-making algorithm used in two-player zero-sum games.

- It simulates **every possible future move** from the current board state
- Assigns a score: `+10` for AI win, `-10` for human win, `0` for draw
- Chooses the move that **maximizes its own score** while **minimizing the human's**
- Result: the AI **never loses** — the best a human can do is a draw

### Easy Mode
- 65% of the time: picks a **random empty cell**
- 35% of the time: uses **Minimax** for the optimal move
- This makes it beatable but still occasionally challenging

---

## ⌨️ Controls

| Action | How |
|--------|-----|
| Place mark | Click / tap any empty cell |
| Switch mode | Click a segment in the mode toggle |
| Pick X or O | Click in the picker (single player only) |
| New game | Click **New Game** button |
| Reset scores | Click **Reset Scores** button |
| Toggle theme | Click the 🌙 / ☀️ button |

---

## 🛠️ Tech Stack

| Technology | Usage |
|------------|-------|
| HTML5 | Structure & Canvas (confetti) |
| CSS3 | Animations, transitions, CSS variables, Grid |
| Vanilla JavaScript (ES6+) | Game logic, AI, DOM manipulation |
| SVG | Animated X and O marks, win line |
| localStorage | Score & preference persistence |
| Google Fonts (DM Sans) | Typography |

**Zero dependencies. Zero frameworks. Zero build tools.**

---

## 🎨 Design Tokens

The game uses CSS custom properties for full theming:

```css
:root {
  --primary:       #5446C8;   /* Purple — X color */
  --o-color:       #D93460;   /* Pink-red — O color */
  --surface:       #EEECF8;   /* Background */
  --surface-2:     #E0DCEF;   /* Card background */
  --on-surface:    #18143A;   /* Text */
  --tie-color:     #1FA89F;   /* Teal — Tie color */
}
```

Dark mode swaps all tokens automatically via `[data-theme="dark"]`.

---

## 🐛 Bug Fixes & Technical Notes

### Stale AI Timeout Fix
A `gameGen` counter is incremented on every `newGame()` call. Each scheduled AI move checks if its generation still matches before executing — preventing stale `setTimeout` callbacks from firing on a freshly reset board.

### AI Turn Guard
`aiMove()` verifies `current === aiMark` before placing — a safety net against any race conditions.

### No Tap Highlight
`-webkit-tap-highlight-color: transparent` is applied globally, along with `outline: none` on all buttons, ensuring zero browser-default blue flashes on mobile.

---

## 📸 Screenshots

| Light Mode | Dark Mode |
|-----------|-----------|
| <details><summary>Light Mode</summary><br><img src="https://github.com/user-attachments/assets/042aacee-f9e9-466e-8324-12178b0ac817" width="250"></details> | <details><summary>Dark Mode</summary><br><img src="https://github.com/user-attachments/assets/9a78c4d1-869c-4ab0-83c6-53b1c4605cdd" width="250"></details> |

---

## 🙌 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repo
2. Create your branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👨‍💻 Author

Made with ❤️ and lots of ✨ animations.

> If you found this useful or fun, give it a ⭐ on GitHub!
