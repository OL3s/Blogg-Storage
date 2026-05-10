---
title: "Player Items And Damage Visuals"
date: "2026-05-10"
excerpt: "The Multiplayer Arena test room now has real item actions, a temporary item picker, early inventory direction, and prop visuals that change as they take damage."
---

The current Multiplayer Arena work has moved from simple movement and destruction tests into a more complete player item slice. The goal is still not to build the final shop or inventory screen first. Instead, the project is proving the gameplay pieces in the test room before turning them into polished match systems.

## Items Are Becoming Real Actions

The player item room now supports a much more practical way to test weapons and throwables. Instead of only using number keys or debug cycling, there is a temporary item grid that can be opened during the test. From there, a player can pick a modern item and use it through the same action path.

The action input is closer to how the game should actually play:

- keyboard and mouse players use left mouse button
- controller players use Xbox right trigger
- controller `B` opens the item grid
- controller `A` selects the focused item in the grid

This is still a test menu, not the final buy wheel. But it is an important step away from pure debug shortcuts and toward the player actually having an equipped item.

## Server-Authoritative Item Use

Item use is being shaped around the multiplayer model from the start. The local player requests an action, the host validates and executes it, and the result is synced back out to other peers.

That matters for weapons, grenades, and future inventory rules. A client should not be able to decide alone that it fired, had ammo, or carried an item. The host needs to validate the action so every device sees the same fight.

The current slice already sends the exact action direction when an item is used. That direction is also shown briefly on other devices by forcing the held item to point where the shot or throw actually happened. It makes remote action readable even if the normal aim display is lower rate or slightly behind.

## The Next Slice: Inventory, Ammo, And Armor

The next planned gameplay work is the player equipment model. The design is that a player should not have unlimited carrying space. What they can carry should come from their armor, inventory providers, and special slots.

The next slice is focused on:

- one equipped armor item
- one or more inventory providers
- one normal base carried item slot
- an optional backstrap item
- typed item slots
- magazine and ammo reserve buckets
- validation before item use

Ammo will be separate from carried items. A rocket launcher is an item. Extra rockets are reserve ammo, not more item slots. The same idea will apply to magazines and other reload resources.

## Prop Damage Is More Visual Now

Props also got a visual upgrade. Previously, a damaged prop was only tinted. Now the prop SVGs are three-frame horizontal atlases:

- perfect
- touched
- close to broken

The runtime picks the frame based on health, using the same kind of health-ratio thresholds as the wall damage overlays. That gives barrels, rocks, and trees a clearer sense of being damaged without changing their collision or gameplay size.

This is a small visual step, but it supports the bigger goal: the arena should be readable while it is being destroyed. Players need to understand which objects are fresh, which are damaged, and which are almost gone.

## Why This Matters

The project is starting to connect player actions, destructible objects, visuals, and networking into one testable gameplay loop. Items can execute. Props and walls can take damage. The arena changes. The next step is making the player's equipment and ammo rules real enough that the item actions have meaningful limits.

That is where the game starts moving from a test scene with weapons into an actual arena combat system.
