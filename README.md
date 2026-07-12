# Gem Rumble

A top-down mobile arena brawler in the spirit of Brawl Stars — one self-contained
`index.html`, no build step, no external assets. Built from the spec in
[`PROMPT.md`](PROMPT.md).

## How to run

Open `index.html` in any modern browser. On a phone, serve the folder
(`python3 -m http.server`) and visit it, or open the file directly. Works
offline; best in landscape.

## How to play

Hold **10 gems** (team total) from the center mine for **15 seconds** to win a
3-minute match. Dying drops your gems.

- **Touch:** left half = floating movement joystick. Right half: **tap** to
  quick-fire with auto-aim, **drag & release** to aim (drag back to center to
  cancel). The glowing **SUPER** button appears when charged.
- **Desktop:** WASD to move, mouse to aim, click to fire, **Space** for Super.

Hide in bushes, break crates with Supers, and watch out for water.

## Tuning

All key constants live at the top of the `<script>` in `index.html`:
match length (`MATCH_TIME`), gems to win (`GEMS_TO_WIN`, `HOLD_TIME`),
bot difficulty (`BOT.aimErr` / `BOT.reaction` — raise to make bots easier),
respawn/shield timers, and per-character stats in the `CHARS` array
(hp, speed, reload, damage, range, Super definitions).
