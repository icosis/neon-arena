# Scribble Arena

A hand-drawn, first-person shooter that runs in the browser, single-player against bots. One file (`index.html`), no build step.
It loads three.js r128 from cdnjs and a handwriting font from Google Fonts, so it needs an internet connection the first time.

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
| 1-5 / Q / wheel | choose a weapon |
| G | throw a grenade |
| F | show the frame rate |
| Esc | pause (settings, or end the run) |

## What is in it

**Look.** Everything is drawn on paper: a graph-paper, ruled-notebook or kraft-paper floor, pastel shapes with thick pen outlines (inverted-hull outlines, no art files), and characters with faces. Skins are pen colours that unlock as you level.

**Weapons.** All five are available from the start of every run: pistol (infinite reserve), rifle, shotgun, SMG and sniper. Each has its own fire rate, spread, magazine and reserve ammo. Headshots do 2.5x. Grenades (G) have a fuse, bounce off walls, and splash for damage, including to you.

**Pickups.** Health, ammo, grenades, ammo crates (refill every reserve), and timed power-ups: speed boost, double damage and a 50-point shield. Kills drop them, clearing a survival wave drops a reward, and they also spawn around the arena and expire.

**Modes.**
- Survival: endless waves, a boss every 5th wave.
- Time Attack: 90 seconds, each kill adds 1.5 more, and the bots ramp up.
- Deathmatch: first to 15 kills wins, 5 deaths and the bots win. You respawn with a short shield.

**Maps.** Graph, Notebook and Kraft, each with its own layout and paper. Cover blocks your shots and theirs, and enemies only shoot with a clear line.

**Enemies.** Grunt, runner and tank, plus a boss. Health scales with the wave. Difficulty (easy / normal / hard) scales their health and damage.

**Progression and UI.** XP and levels, pen-colour skins, kill feed with multi-kill streaks, local top-5 board per mode, lifetime stats, and settings for sensitivity, field of view and volume. Everything is saved in `localStorage`.

**Performance.** The renderer starts at a capped pixel ratio and steps it down on its own if frames average slower than about 40 fps. Tracers are pooled, line-of-sight checks allocate nothing, and the HUD only touches the DOM when a value changes. Press F in game to see the frame rate and current resolution scale.

`index.html?demo=1` skips the click-to-start and plays itself, which is what the headless screenshots use (with `&mode=`, `&map=`, `&diff=`, `&w=`, `&wave=`, `&fps=1` and `&end=` to set it up).

## Put it online

It is a static site, so any static host works. This repo is served with GitHub Pages: Settings, Pages, deploy from the `main` branch, root folder.

## Not here yet

- Multiplayer. That needs a server holding the shared game state; this is single-player against bots.
- Touch controls (mouse and keyboard only).
