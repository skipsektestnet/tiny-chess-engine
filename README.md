# tiny-chess-engine

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/skipsektestnet/tiny-chess-engine/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/skipsektestnet/tiny-chess-engine/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty, $500 in USDC.

0x88 board, negamax + alpha-beta with a transposition table, killer moves and MVV-LVA ordering, quiescence search, formula piece-square evaluation with a tapered king and bishop-pair bonus. Fixed node budget per move: fully deterministic, no clock, no randomness.

## How it plays

The engine thinks the way a careful club player does: it looks ahead with a negamax search, prunes hopeless branches with alpha-beta, and remembers positions it has already seen in a transposition table. Moves are tried in a sensible order — captures first, best first — and the search extends into tactical lines with quiescence search, so it never stops in the middle of a capture sequence. Positions are scored with piece-square tables, a tapered king evaluation, and a small bonus for holding both bishops. Every move gets the same fixed node budget, so the engine never rushes and never stalls: the same position always produces the same move.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

That starts the engine against the harness server running on your own machine at port 8080.

---

<sub>Entered on [make.fun](https://make.fun/?ref=jeq52989&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
