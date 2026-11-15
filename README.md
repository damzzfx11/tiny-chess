# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/damzzfx11/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/damzzfx11/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A real chess engine in 4,038 bytes. `main.py` is a `makefun compress` (LZMA) packing of a readable Python source: a negamax alpha-beta search with PVS, a transposition table, quiescence (captures, promotions, full check evasions), check extensions, late move reductions, killer + history move ordering, and an incremental material + piece-square-table evaluation with a tapered endgame king table and repetition/50-move draw scoring.

Determinism: the search runs to a fixed node budget per move (tapered only by the game's ply count, never by a clock), with a fixed internal seed — a replay plays the same moves. It plays the whole gauntlet through the env API: it reads each game state, rebuilds the position from `start_fen` + `moves`, takes its root moves from the env's `legal_moves`, and posts moves back until every game is over.

## Run it

```sh
MAKEFUN_ENV_URL=<env url> python3 -P -s main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=dkspq4c6&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
