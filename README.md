# Scribble Arena

A hand-drawn, first-person movement shooter that runs in the browser, single-player against bots. One file (`index.html`), no build step.
It loads three.js r128 from cdnjs and a handwriting font from Google Fonts, so it needs an internet connection the first time.

## Play it locally

Open `index.html` directly, or serve the folder (some browsers are stricter about pointer lock on `file://`):

    python -m http.server 8000
    # then open http://localhost:8000

Pick a mode, map and difficulty on the menu, then click Play (or press X / Options on a gamepad).

| Key | Action |
|---|---|
| WASD / Shift | move / sprint |
| Space | jump; again in the air to double jump; next to a wall to wall jump |
| C / Ctrl | slide on the ground, air dash in the air |
| Q / E | grapple: tap to hook and swing, hold to reel in, jump to launch off, tap again to let go |
| Mouse / Left click | aim / shoot (or slash with the katana) |
| Right click (hold) | aim down sights; the sniper rifle gets a scope |
| F | quick katana slash with any weapon out |
| V (or both mouse buttons with the katana) | dash-slash, once the katana gauge is full |
| 1-6 / wheel | choose a weapon (6 is the katana) |
| R / G | reload / throw a grenade |
| H / P / Esc | music / frame rate / pause |

**Gamepad (PS5, Xbox, most others):** left stick move, right stick look, R2 fire, L2 aim, X jump, O slide/dash, L1 grapple, R1 quick slash, L2+R2 dash-slash, Square reload, Triangle next weapon, R3 or d-pad up grenade, L3 sprint, Options pause.

**Settings:** sensitivity, field of view, volume, invert look, music, and a trackpad mode (Shift aims, double-tap W sprints).

## What is in it

**Movement.** Double jump, wall jump (with a slow slide down a wall you are touching), slide, air dash, and a grapple that swings on a rope or reels you in. Air momentum is kept: you steer in the air but never brake below the speed you had, so swings and wall jumps carry.

**Weapons.** All six from the start: pistol (infinite reserve), rifle, shotgun, SMG, sniper and katana. Headshots do 2.5x. Damage fills the katana gauge; when it is full, a dash-slash cuts through everything in a line. Grenades bounce and splash, including on you.

**Maps.** Three 120 x 120 arenas with real height, all generated from a fixed seed so they are the same every time:
- City: a street grid of buildings of different heights, stairs onto rooftops, fire-escape ledges, skybridges and a central plaza with a spire.
- Temple: a stepped pyramid you can climb, a ring of columns with ledges, broken walls, floating stones and four corner shrines.
- Yard: a long skybridge with stair towers, a warehouse with a walkable roof, a maze, water towers and ruined arches.

A minimap shows the layout, enemies and pickups. About a third of the pickups land on rooftops and ledges.

**Pickups.** Health, ammo, grenades, ammo crates, and timed power-ups: speed boost, double damage and a 50-point shield.

**Modes.** Survival (waves, a boss every 5th), Time Attack (90 seconds, kills add time) and Deathmatch (first to 15 kills, 5 deaths and you lose).

**Enemies.** Grunt, runner, tank and boss. They walk around walls they get stuck on, shoot over low cover and under bridges, and find a moving target harder to hit.

**Progression.** XP and levels, pen-colour skins, kill feed with multi-kill streaks, local top-5 board per mode, lifetime stats. Saved in `localStorage`.

**Performance.** Each map is merged into two meshes (fills and outlines), so it is two draw calls however many boxes it has. The renderer lowers its resolution on its own if frames run slow, tracers are pooled, and the HUD only touches the DOM when a value changes.

`index.html?demo=1` plays itself for headless screenshots (`&mode=`, `&map=`, `&diff=`, `&w=`, `&wave=`, `&fps=1`, `&end=`; `&still=1&pos=x,y,z&yaw=&pitch=` freezes the camera to look at a map).

## Put it online

This repo is served with GitHub Pages from the `main` branch, root folder.

## Not here yet

- Online multiplayer. That needs a server holding the shared game state.
- Touch controls.
