---
title: "P1: The First Playable Flow"
date: "2026-05-09"
excerpt: "SingleplayerRoguelite has reached its first milestone: the player can move through the menu, choose a character, start a run, and enter the first version of the outpost."
---

SingleplayerRoguelite has reached its first real milestone. It is still very early, but the game now has the beginning of a playable flow.

The main focus for this milestone is simple: the player should be able to open the game, use the menu, choose a character, start a run, and arrive at the first hub area.

That might not sound as exciting as combat or boss fights, but it is an important step. Before the game can grow, the basic starting point has to make sense.

## What The Game Is

SingleplayerRoguelite is a single-player roguelite about going on repeated runs, getting stronger, making choices, and eventually defeating bosses.

The bigger goal is to collect three lost gems. Each gem comes from defeating a different boss, and each run should push the player closer to that goal.

The planned loop is:

- start a run
- choose a path
- fight enemies
- find upgrades
- reach a boss
- earn rewards
- repeat with more progress

Right now, the game is not at the full loop yet. This milestone is about making the first part work properly.

## The Menu Works

The first version of the menu flow is now in place.

The player can go from the start menu into the run overview. From there, the game can decide if the player should continue an existing run or start a new one.

This is important because roguelites need a clear start. The game needs to know if the player already has a run, if they are starting fresh, and where they should go next.

There is also a rule being added around new runs: the player should not be able to endlessly restart just to get the perfect first choice. The game should push the player to actually play the run instead of rerolling the menu.

## Character Select Is The Main Focus

The biggest part of this milestone is the character selection screen.

When starting a new run, the player chooses a character. That character has a name, skills, and starting information that becomes part of the run.

This makes character select more than just a menu. It is where the run begins to get its identity.

The next important improvement is making this screen easier to understand. A new player should quickly understand what the skills mean, why the character choice matters, and what they are about to start.

## The First Hub Is In

After choosing a character, the player enters the outpost.

The outpost is the game's between-run hub. This is where the player will later prepare, visit buildings, check items, take contracts, and make choices before moving forward.

The first version already supports:

- fixed buildings, like an inn and contract building
- random building slots for future shops or services
- popups and screens for things like inventory, settings, character info, and codex
- building screens with text, images, and action buttons

Some of it is still placeholder content, but the important part is that the structure exists. The outpost can now become the place where many future systems connect.

## Made For Phones First

This game is being designed for phones in landscape mode.

That means the UI has to be easy to press and easy to read. Buttons need to be large enough. Text needs to be clear. Menus cannot be designed only for mouse and keyboard.

This is why the menu and character setup matter so much right now. If these screens are confusing on a phone, the rest of the game will feel bad no matter how good the later combat becomes.

## What Needs Work Next

The next step is making the first experience clearer.

The main things I want to improve next are:

- first-run tips on character selection
- better explanations for skills and stats
- clearer feedback when equipping items
- a setting to turn first-run tips on or off
- better gold and item count display in shop/building screens

These sound like small details, but they matter a lot. The first version should not just work. It should also make sense to someone who has not followed development.

## Current State

SingleplayerRoguelite is still early, and a lot of the content is temporary. But the first playable flow is now taking shape.

The player can move from the menu, into character selection, and then into the first hub. That gives the project a real foundation to build on.

Next, I want to make this flow easier to understand before pushing further into contracts, combat, items, bosses, and the full three-gem progression loop.
