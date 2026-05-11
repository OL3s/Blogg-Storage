---
title: "MobArena Gets Its Foundation And MVP Roadmap"
date: "2026-05-11"
excerpt: "MobArena now has its first Godot foundation: a town, company creation, building interactions, shared time UI, and a full GitHub roadmap for the MVP gladiator demo."
---

MobArena has moved from a game idea into a real Godot project with a playable structure beginning to take shape.

The goal is a 2D gladiator company game: build a roster, train fighters, buy equipment, take arena contracts, and survive long enough to face mandatory boss fights. This first update is not about finished combat yet. It is about putting the project on rails so every next feature has somewhere clean to live.

## The Town Is Taking Shape

The current build starts with a company creation flow. Before entering town, the player creates a company name and chooses a simple shield/logo combination. That company identity then appears in the town interface.

The town itself now has a first layout with buildings for the core management loop:

- Arena
- Roster Hall
- Training Hall
- Healer
- Blacksmith
- Gladiator Market

Most buildings currently open placeholder panels, but they are no longer just static art. They are real interactive building scenes with their own icons, labels, click/touch handling, and editor previews. Roster Hall already opens as a separate room, because roster management will need more space than a small popup.

## Time Now Belongs To The Company Flow

Town time is now shared through the runtime save node, so rooms like Town and Roster Hall can use the same clock. The bottom UI has a day timeline with sun and moon icons, open/sleeping state, speed controls, and a boss deadline bar.

The speed states are designed to be readable instead of only technical:

- Paused
- Slowed
- Normal
- Fast

Entering town from the main menu or returning from the arena resets time to paused, while moving between town rooms keeps the same shared time state.

## Building Toward A Real MVP

The GitHub repository is now set up with milestones and issues for the full MVP path. The MVP is meant to use every major part of the demo, not just show disconnected menus.

The planned demo loop is:

- create a gladiator company
- inspect the roster
- train a gladiator
- buy or equip simple weapons
- take arena contracts
- fight slimes
- earn gold or lose a gladiator
- recruit or heal through town buildings
- reach a boss deadline
- fight the required boss

That means every town building needs at least simple functionality for the MVP. Training needs gladiator levels and stats. Weapons need requirements, like strength or level, so training and equipment actually connect. The boss fight is also required, not optional.

## Why This Foundation Matters

This kind of work is easy to underestimate because it is not a flashy combat gif yet. But it matters because it defines how the game will grow.

The project now has reusable UI, shared runtime state, authored Godot scenes, interactive town buildings, documentation for future work, and a clear issue roadmap. The next big step is the data layer: company data, gladiator resources, weapons, contracts, and the roster systems that will power the actual game loop.

Once that is in place, the arena can stop being a placeholder and start becoming the place where all those decisions matter.
