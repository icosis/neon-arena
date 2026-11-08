# Neon Arena

A first-person wave shooter that runs in the browser. One file (`index.html`), no build step.
It loads three.js r128 from cdnjs, so it needs an internet connection the first time.

## Play it locally

Open `index.html` directly, or serve the folder (some browsers are stricter about pointer lock on `file://`):

    python -m http.server 8000
    # then open http://localhost:8000

Click to start. WASD move, Shift sprint, Space jump, mouse aim and shoot, R reload, 1 / 2 / wheel switch weapon, Esc pause.

`index.html?demo=1` skips the click-to-start and plays itself, which is what the headless screenshots use.

## Put it online

It is a static site, so any static host works. Two easy ones:

- Vercel: `npx vercel --prod` inside this folder.
- GitHub Pages: push the folder to a repo and enable Pages on the main branch.

## What is in it

- Three enemy types (grunt, runner, tank) that scale with the wave; tanks and runners appear from wave 2 and 4.
- Rifle (auto) and shotgun (8 pellets). Headshots do 2.5x.
- Cover that blocks both your shots and theirs; enemies only shoot with a clear line.
- Health packs drop from kills; clearing a wave heals 20.
- Best score is kept in `localStorage`. Sensitivity is a slider on the menu.

## Not here yet

- Multiplayer. That needs a server holding the shared game state; this is single-player against bots.
- Touch controls (mouse and keyboard only).
