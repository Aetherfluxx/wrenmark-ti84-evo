# WRENMARK

A tiny, original monster-catching RPG for the **TI-84 Evo**, written in Python. ✅ Confirmed running on a real TI-84 Evo.

## What's in the game

The **whole game is playable from start to finish**:

- **Explore** the Wrenmark region: 10 towns, 8 routes, a cave, a mountain pass and the League (26 screens).
- **Wild Pokémon** in tall grass, caves and water. **Catch** them with Poké Balls; extras go to the **PC** at any Pokémon Center.
- **Battles:** fight, use items, switch, or run. Pokémon gain EXP, level up, learn moves and **evolve**.
- **Trainers** who spot you and challenge you, plus **4 Gym Leaders** who award badges. Badge 2 unlocks Surf.
- **The Elite Four and the Champion**, followed by an ending.
- **Saving:** 3 save slots. SAVE and LOAD from the start menu, CONTINUE from the title screen, and an autosave after each badge.
- **LEVEL CAP:** an item that makes strong Pokémon battle at a lower level of your choice.

## What's in this folder

| Item | What it is |
|---|---|
| `Game/WRENMARK.py` | **the game: the one you run** |
| `Game/WRCORE.py`, `Game/WRMAPS.py`, `Game/WRBTL.py`, `Game/WRTRN.py` | game parts that `WRENMARK` loads by itself. They must be on the calculator, but you never run them |
| `Game/rpgprobe.py` | optional one-time hardware test that checks how your calculator draws, reads keys and stores data |
| `Game/Dev/` | PC-only: source files, design doc, **cheat codes** (`CHEATS.md`), emulator, test tools. Never copied to the calculator |
| `GUIDE.md` | step-by-step walkthrough: where to go, what to catch, how to beat each gym |
| `README.md` | this file |
| `LICENSE.md` | the license |

## Putting it on the calculator

1. Copy **all five `WR….py` files** (`WRENMARK`, `WRCORE`, `WRMAPS`, `WRBTL`, `WRTRN`) from `Game/` to the TI-84 Evo. You can do them all in one go. Replace any older copies already on the calculator.
2. Run **`WRENMARK`**. That's it. Only ever run this one.

> **Why five files and not one?** The calculator has to translate a whole Python file in memory before running it. One big file ran out of memory (`MemoryError`), so the game is split into parts the calculator can handle one at a time. (A one-file version might be possible later. See the end of `Game/Dev/DESIGN.md`.)

**Optional, once:** copy and run `rpgprobe.py` too. It shows a results screen. Share it with Claude so the game can be tuned to your calculator.

## Controls

| Key | Walking around | Menus / dialog |
|---|---|---|
| Arrows | walk (hold to keep walking) | move cursor |
| ENTER or 2ND | talk / read / interact | confirm, next page |
| CLEAR or MODE | open start menu | back / cancel (DEL also works) |

- Red-roof door: heal.
- Blue-roof door: shop.
- Purple-roof door: gym.

A keypad diagram and the full menu reference are in `GUIDE.md`.

## Cheats

Eight secret title-screen codes for testing are documented in `Game/Dev/CHEATS.md`. They include a save editor, free roam, warp, no wild encounters, guaranteed catches and one-hit wins. None of them are active unless you type the code.

## For development (optional)

The game is written as small source files in `Game/Dev/src/` and built into the five calculator files by a build script. If you edit the sources, rebuild. Run these from `Game/Dev`.

Rebuild the calculator files and smoke-test them:

```bash
python tools/build.py
```

Validate all maps, edges, warps and badge gates:

```bash
python tools/check_maps.py
```

Check difficulty with thousands of simulated battles:

```bash
python tools/balance.py
```

Run a scripted playthrough (screenshots go to `shots/`):

```bash
python tools/sim.py
```

The full design (region, roster, type chart, battle rules, gyms, save format and risks) is in `Game/Dev/DESIGN.md`.
