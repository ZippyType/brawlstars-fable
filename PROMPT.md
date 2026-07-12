# AI Prompt: Build a Brawl Stars–Style Mobile Arena Brawler with Touch Controls

Copy everything below the line into your AI coding assistant.

---

You are an expert game developer. Build a complete, playable top-down multiplayer-style arena brawler in the spirit of Brawl Stars, designed for mobile with touch controls. Use only original names, art, and characters — do not copy any Supercell assets, names, or trademarks.

## Tech Stack

- Build it as a single HTML5 game using **HTML, CSS, and JavaScript with the Canvas API** (or Phaser 3 if a framework is preferred), so it runs in any mobile browser with no install.
- Everything must work offline in one page. Render all art with code (shapes, gradients, particles) — no external images, fonts, or network requests.
- Target 60 FPS on mid-range phones: use `requestAnimationFrame`, object pooling for bullets/particles, and avoid per-frame allocations.
- Set the proper viewport meta tag, disable page scrolling/zooming/text selection, handle `touchstart`/`touchmove`/`touchend` with `preventDefault()`, and support both portrait and landscape by scaling the canvas to the screen with `devicePixelRatio` awareness.

## Core Gameplay

A 3-minute match on a tile-based arena (roughly 30×20 tiles) viewed top-down with a camera that follows the player:

- **Player character ("brawler")** with health, movement speed, a primary attack (3 ammo bars that recharge over time), and a Super ability that charges by dealing damage.
- **7 AI-controlled enemy bots** with simple but fun behavior: wander, seek gems/power-ups, chase and attack when the player is in range, retreat when low on health, and hide in bushes.
- **Game mode — "Gem Grab" style:** gems spawn from a mine in the center of the map every few seconds. First team/player to hold 10 gems starts a 15-second countdown; survive it to win. Dying drops all your gems where you fell.
- **Respawning:** defeated characters respawn at their spawn point after 3 seconds with brief invincibility.
- **Map elements:** destructible walls (broken by Supers), indestructible walls, water (blocks movement, not bullets), and bushes (characters inside are invisible to enemies unless close).

## Playable Characters

Include at least 4 selectable characters with distinct stats and attack styles (all original names/designs), for example:

1. **Brawler-type:** medium health, spread shotgun blast, dash Super.
2. **Sharpshooter-type:** low health, long-range single shot, piercing Super beam.
3. **Tank-type:** high health, short-range melee swipe, area slam Super.
4. **Thrower-type:** low health, lobbed projectile that goes over walls, Super that rains multiple projectiles.

Give each a distinct silhouette/color and show a character-select screen before the match.

## Touch Controls (the most important part — get these right)

- **Left virtual joystick (movement):** appears wherever the left half of the screen is first touched (floating joystick). Dragging moves the character in that direction with analog speed. Releasing stops movement. Draw the joystick base and thumb with transparency.
- **Right virtual joystick (aim & fire):** on the right half of the screen.
  - **Tap** = quick-fire with auto-aim at the nearest visible enemy.
  - **Drag** = show an aim indicator (cone or line matching the character's attack shape/range), and **release to fire** in that direction.
  - Dragging back to the center deadzone and releasing cancels the shot.
- **Super button:** a separate glowing button above the fire area that appears when the Super is charged; same tap-to-auto-aim / drag-to-aim-and-release behavior.
- Support **multi-touch** correctly: track touches by `identifier` so moving and aiming work simultaneously; never let one stick steal the other's touch.
- Add **mouse/keyboard fallback** (WASD + mouse aim, click to fire, space for Super) so it's also testable on desktop.

## Game Feel & Polish

- Smooth camera follow with slight look-ahead toward the aim direction.
- Juice: muzzle flashes, hit flashes, damage numbers floating up, screen shake on Supers, particles for gem pickup, death bursts, and respawn sparkles.
- HUD: health bars above characters, ammo bars under the player, gem counters for each team, match timer, countdown overlay when someone reaches 10 gems.
- Screens/states: title screen → character select → countdown (3-2-1) → match → victory/defeat screen with a play-again button.
- Simple synthesized sound effects with the Web Audio API (shots, hits, gem pickup, Super, win/lose jingle) and a mute button.

## Code Quality

- Organize the code into clear modules/classes: `Game`, `Input` (touch joysticks), `Entity`/`Character`, `Bot` AI, `Projectile`, `Map`, `Camera`, `HUD`, `Audio`.
- Use a fixed-timestep or delta-time game loop so speed is framerate-independent.
- Comment the key systems (joystick math, auto-aim targeting, bot state machine).

## Deliverable

A single self-contained `index.html` file (or a small set of files) that I can open on my phone and immediately play. After generating the code, briefly explain the file structure, how to run it, and how to tune key constants (character stats, bot difficulty, match length).
