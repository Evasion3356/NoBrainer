# NoBrainer offline checks

Run from the repository root with LuaJIT (`luajit tests/<suite>.lua`).

The solvers are BetterBrainer's, in the `BetterBrainer` submodule; their suites are in `BetterBrainer/tests/` (see its `tests/README.md`). NoBrainer's suites cover only what NoBrainer adds.

| Command | What it checks | Last result |
|---|---|---|
| `nobrainer_spec.lua` | Import of BetterBrainer's core, data and localization through a DMF stub; option and string placement; Smart Seed Reroll with a host seed, a predicted board after a reroll, a client seed rebuilt from the level seed, and BetterBrainer's own reroll when it is off | 2026-10-24: 136/136 |
| `servo_skull_spec.lua` | Servo skull ordering through `ctx.settings` and `update(dt, t)` | 2026-10-24: 4/4 |

`nobrainer_spec.lua` replaces the engine's `math.next_random` with a stand-in generator, so its board costs are not the game's. These are offline results, not in-game results.
