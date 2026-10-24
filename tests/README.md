# NoBrainer offline checks

Run from the repository root with LuaJIT (`luajit tests/<suite>.lua`).

The solvers are BetterBrainer's, in the `BetterBrainer` submodule; their suites are in `BetterBrainer/tests/` (see its `tests/README.md`). NoBrainer's suites cover only what NoBrainer adds.

| Command | What it checks | Last result |
|---|---|---|
| `nobrainer_spec.lua` | Import of BetterBrainer's core, data and localization through a DMF stub; option and string placement; Smart Seed Reroll with a host seed, a predicted board after a reroll, a client seed rebuilt from the level seed, and BetterBrainer's own reroll when it is off | 2026-10-24: 136/136 |
| `servo_skull_spec.lua` | Servo skull ordering through `ctx.settings` and `update(dt, t)` | 2026-10-24: 4/4 |

## Darktide source

The mod never needs the game source; only the tests do. `darktide_source.lua` fetches the files a suite asks for from [Aussiemon/Darktide-Source-Code](https://github.com/Aussiemon/Darktide-Source-Code), at a pinned commit (1.13.4), into `tests/.darktide-source/` (git-ignored). The fetch is sparse and partial: only those files are downloaded, about 2 MB on the first run. It needs `git` and network access once; later runs reuse the checkout.

To use an existing checkout instead, set `DARKTIDE_SOURCE` to its root, for example `$env:DARKTIDE_SOURCE = "D:\Darktide-Source-Code"`. It is read as is, at whatever version it is.

`nobrainer_spec.lua` builds its boards with the game's `MinigameDecodeSymbols.setup_game`, `table.shuffle` and minigame settings. `math.next_random` is native to the engine, so a stand-in generator replaces it, and board costs are not the game's. These are offline results, not in-game results.
