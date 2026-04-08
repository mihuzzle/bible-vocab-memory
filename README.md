# FI ↔ EN Bible Vocab Match (GitHub Pages)

A single-file, mobile-friendly matching game for practicing **Biblical vocabulary translations from Finnish → English**.

Play it here: https://mihuzzle.github.io/bible-vocab-memory/

---

## How to play

1. Open the game.
2. Choose **Category** and **Content** mode (single words or all content).
3. Press **Start new session**.
4. In the game view:
   - Tap one **Finnish** card (left).
   - Tap one **English** card (right) to attempt a match.
   - Correct matches turn green, play a *ding* (if enabled), then disappear.
   - Incorrect matches flash red; optionally vibrate (if enabled).

A session uses a shuffled deck with **no repeats** until all eligible pairs are consumed.

---

## This build’s key UI rules

- ✅ **Scrolling is allowed in the matching view**.
- ✅ Each round always uses **5 pairs**.
- ✅ **Finnish is always on the left**, **English always on the right**.
- ✅ Cards **never truncate text**: phrases wrap naturally and full text is always visible.
- ✅ Default card styling uses **smaller text** and **less padding**.

---

## Difficulty and target time

- Beginner: 8.0 s/pair
- Intermediate: 3.6 s/pair
- Expert: 1.8 s/pair

Target per round:

`targetSeconds = secPerPair × numberOfPairsThisRound`

---

## Scoring

- `accuracy = matches / (matches + mistakes)`
- `base = 100 × matches/8`
- `accFactor = max(0.5, 1 − 0.05×mistakes)`
- `timeFactor = clamp(0.6, 1.4, target/max(0.2,timeUsed))`
- `roundPoints = round(base × accFactor × timeFactor)`
- `sessionPoints = sum(roundPoints)`

---

## Data

Vocabulary is embedded inside `index.html` (no external files). The uploaded `Uskonnollinen_sanasto__laaja.xls` produced:

- **1560** Finnish–English pairs
- **37** category labels

---

## Deploy / Update

1. Replace `index.html` in the repository root.
2. Commit & push.
3. GitHub Pages will publish the updated version.
