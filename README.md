# Neon Arena

A first-person shooter that runs in the browser, single-player against bots. One file (`index.html`), no build step.
It loads three.js r128 from cdnjs, so it needs an internet connection the first time.

## Play it locally

Open `index.html` directly, or serve the folder (some browsers are stricter about pointer lock on `file://`):

    python -m http.server 8000
    # then open http://localhost:8000

Pick a mode, map and difficulty on the menu, then click Play.

| Key | Action |
|---|---|
| WASD / Shift / Space | move / sprint / jump |
| Mouse / Left click | aim / shoot |
| Right click (hold) | aim down sights; the sniper rifle gets a scope |
| R | reload |
| 1-5 / Q / wheel | choose a weapon you own |
| G | throw a grenade |
| Esc | pause (settings, or end the run) |

## What is in it

**Weapons.** Pistol (infinite reserve), rifle, shotgun, SMG and sniper. Each has its own fire rate, spread, magazine and reserve ammo. You start with the pistol and rifle and find the rest in weapon crates. Headshots do 2.5x. Grenades (G) have a fuse, bounce off walls, and splash for damage, including to you.

**Pickups.** Health, ammo, grenades, weapon crates, and timed power-ups: speed boost, double damage and a 50-point shield. Kills drop them, clearing a survival wave drops a reward, and they also spawn around the arena and expire.

**Modes.**
- Survival: endless waves, a boss every 5th wave.
- Time Attack: 90 seconds, each kill adds 1.5 more, and the bots ramp up.
- Deathmatch: first to 15 kills wins, 5 deaths and the bots win. You respawn with a short shield.

**Maps.** Grid, Pillars and Courtyard, each with its own layout and colours. Cover blocks your shots and theirs, and enemies only shoot with a clear line.

**Enemies.** Grunt, runner and tank, plus a boss. Health scales with the wave. Difficulty (easy / normal / hard) scales their health and damage.

**Progression and UI.** XP and levels, colour skins that unlock as you level, kill feed with multi-kill streaks, local top-5 board per mode, lifetime stats, and settings for sensitivity, field of view and volume. Everything is saved in `localStorage`.

`index.html?demo=1` skips the click-to-start and plays itself, which is what the headless screenshots use (with `&mode=`, `&map=`, `&diff=`, `&all=1`, `&w=`, `&wave=` and `&end=` to set it up).

## Put it online

It is a static site, so any static host works. This repo is served with GitHub Pages: Settings, Pages, deploy from the `main` branch, root folder.

## Not here yet

- Multiplayer. That needs a server holding the shared game state; this is single-player against bots.
- Touch controls (mouse and keyboard only).
