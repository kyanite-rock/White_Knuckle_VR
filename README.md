# White Knuckle VR

A full 6DOF VR conversion for **White Knuckle**, the speed climbing game from Dark Machine Games.

Features stereo rendering, roomscale movement, and 6DOF gesture-based motion controls. The philosophy of this mod is that it should be completely on-par with the physics-based gameplay of the vanilla game. All VR interactions work as inputs into the existing physics system, meaning that the player moves in exactly the same way as in vanilla. The only difference is that you are using your hands to climb and jump. This also means that buffs & debuffs should all work right out of the box.

Physical item interactions are not yet supported. This is something I'd like to add in the future, but it will likely require significant effort.

## Installation

1. Download BepInEx from https://github.com/BepInEx/BepInEx/releases/latest, copy the zip into your game folder, and extract it into your White Knuckle game folder. Take the **x64** build — the file named `BepInEx_win_x64_5.x.x.x.zip`. The x86 and IL2CPP versions won't work.
2. Download the latest White Knuckle VR release zip folder, and extract it into your White Knuckle game folder.
   `BepInEx/plugins/WhiteKnuckleVRMod.dll` will land next to BepInEx's own files.
3. Launch the game once. It will run in flatscreen mode, and create the necessary config files. Once you reach the main menu, close the game.
4. Launch the game again, with an active VR runtime. The game should now launch in VR.

The first launch writes three config files into `BepInEx/config/`. See
[The VR settings menu](#the-vr-settings-menu).

**Finding your game folder:** in Steam, right-click White Knuckle → Manage → Browse local files.

### Playing in flatscreen mode

Set `activateVR` to `false` in `BepInEx/config/VRToggle.json` and relaunch. The game will launch without the VR mod active.

## Controls

### Right controller

| Control | Action |
|---|---|
| **Grip** | Grab a handhold |
| **Trigger** | Interact with buttons and levers; pick up items; use a held item |
| **A** | Jump |
| **B** | Quick-pocket right / Cancel in menu or terminal |
| **Stick** | Turn (left/right). Smooth or snap, set in the VR settings menu. |
| **Stick click** | Crouch |
| **Menu button** | Maps to the gamepad Select button |

### Left controller

| Control | Action |
|---|---|
| **Grip** | Grab a handhold |
| **Trigger** | Interact with buttons and levers; pick up items; use a held item |
| **X** | Open / close inventory |
| **Y** | Quick-pocket left |
| **Stick** | Walk and strafe. Also climbs, unless `climbMode` is set to Gesture Only. |
| **Stick click** | Sprint |
| **Menu button** | Pause / Open Menu |

## Gestures

Gestures allow you to move and climb using physical movements, but you can achieve most of these movements with button presses as well. You can turn off or tweak each gesture's activation threshold in `ModParameters.json`.

### Climbing

While gripping handholds, your hand effectively operates as your movement joystick. Your body moves opposite your arm:

- Pull your hand down to climb up
- Move your hand left to climb right
- Pull your hand towards your chest to swing forward
- Extend your hand to move away from the handhold

There is a dead zone around a neutral, where your VR movement will be none.

Set `climbMode` in the VR settings menu to choose:

- **Either** (default) — use arm gestures to climb, but arm gestures can be overridden by using the left joystick
- **Gesture Only** — use arm gestures to climb, joystick is inactive
- **Joystick Only** — vanilla stick climbing, arm gestures are inactive

### Dyno / Wall Jump

While gripping the wall, you can flick your hand downwards and release the grip button to launch off of it. If you move your arm down in a diagonal, you will jump off the wall opposite to the direction of the diagonal. If you are holding the wall with two hands, you'll need to do this with both hands, or release one hand and dyno with the other. You can also jump off the wall by pressing A.

### Jump (on the ground)

Flick both hands upwards to jump off the ground. You can also jump off the ground by pressing A.

### Sprint

Make a mock-running motion with your hands to sprint. You can also sprint by clicking the left joystick.

### Physical crouch

Crouch in real life to crouch in-game. Because this uses the in-game crouch, it can feel a little strange. I plan to fix this later. You can also crouch by clicking the right joystick.

### Throw / drop an item

While holding grip, make a throwing motion, and then release the grip button, to throw or drop an item.

### Hand swap

While holding an item, bring your hands together and press both grips at the same time to pass it between your hands.

## Items

X opens and closes your inventory. Time slows down while it is open by default.

While holding an item, you will see a laser pointer showing where the item is pointing. Press trigger to activate the item, or hold it for charged attacks.

## The VR settings menu

Pause in-game to access the VR Settings screen. More settings are available in 3 json files in BepInEx/config/.

### `VRToggle.json`

This file allows you to turn on or off the mod, or deactivate motion controls (to use a keyboard + mouse or gamepad).

| Key | Default | Meaning |
|---|---|---|
| `activateVR` | `true` | set to `false` to disable the VR mod |
| `useMotionControls` | `true` | set to `false` to play in VR, using either keyboard + mouse or gamepad controls |

### `WhiteKnuckleVRSettings.json`

These are the exact same settings available in the VR Settings menu.

### `ModParameters.json`

Many tunable parameters are available in this file which affect the implementation of the motion & gesture controls. These aren't intended to be changed for normal play, but I'll explain the most useful parameters below.

| Key | Default | Meaning |
|---|---|---|
| `reachMultiplier` | `6` | A multiplier allowing you to reach past your physical hands. It is required for your VR reach to match your reach in the vanilla game. |
| `vrHandScale` | `1` | Size of hand sprites |
| `heldItemScale` | `1` | Size of held items relative to hand size |
| `showInteractIndicators` | `true` | Show per-hand markers on grabbable objects |
| `gestureJumpEnabled` | `true` | Enable gesture-based jump |
| `gestureSprintEnabled` | `true` | Enable gesture-based sprint |
| `handSwapGestureEnabled` | `true` | Enable item swap gesture (note: there is no equivalent button to do this) |
| `physicalCrouchEnabled` | `true` | Enable physical crouch|
| `dynoEnabled` | `true` | Enable dyno / jump-from-wall gesture |
| `throwGestureEnabled` | `true` | Enable throw gesture (note: there is no equivalent button to do this) |
| `throwAppliesReleaseVelocity` | `false` | Adds your real hand speed to a throw. Breaks vanilla gameplay. |
| `enablePositionalMovement` | `true` | Enables roomscale / 6DOF headset movement |
| `cameraFadeOnClip` | `true` | Fades camera to black when your head clips through a wall |
| `physicalCrouchDepth` | `0.25` | Physical crouch distance threshold |
| `bagDistance` / `bagShellRadius` | `0.45` / `0.65` | How far in front of your body the inventory sits, and how big it is |
| `terminalCameraPullback` | `0.2` | Camera distance when interacting with a terminal |
| `verboseLogging` | `false` | Increase mod logging level for debugging |

---

## Known limitations

- Physical item interactions are not yet implemented. I initially planned to do this, but there were a few major technical hurdles involved. So I decided to ship the mod without this to start with.
- Held items are 2D sprites. This is one of the limitations which caused me to hold off on physical items. While every item has a 3D model, those models are not animated the way the 2D sprites are.
- The VR mod renders in multi-pass rendering mode, because the game's custom shaders aren't compiled for single-pass rendering. This means that the mod can be performance intensive, which can be mitigated with the `renderScale` setting in the VR settings menu.

---

## License

White Knuckle VR Mod is free software: you can redistribute it and/or modify it under the terms of the **GNU General Public License, version 3 or (at your option) any later version**, as published by the Free Software Foundation. The full text is in `WhiteKnuckleVR/LICENSE` in the release.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

Copyright (C) 2026 Kyanite-Rock

This archive also includes the OpenXR runtime files that White Knuckle doesn't ship, from The Khronos Group and Unity Technologies. They are not part of this mod and are not covered by its GPL licence — see `WhiteKnuckleVR/THIRD-PARTY-NOTICES.md` in the release archive.

White Knuckle is the property of its developers and publisher. This mod is an unofficial, unaffiliated fan project and redistributes none of the game's files.
