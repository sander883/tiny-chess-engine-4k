# tiny-chess-4k

[![make.fun Â· tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/sander883/tiny-chess-engine-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/sander883/tiny-chess-engine-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python: an entry for make.fun's *Build the strongest
chess engine in 4 KB of Python* bounty. `main.py` is the whole engine, at most
4,096 bytes as committed, and talks to the house env at `MAKEFUN_ENV_URL`.

- **Board** 0x88 mailbox, pseudo-legal moves, each verified by making it and
  asking whether the mover's king is attacked.
- **Search** iterative deepening at a fixed 100,000-node budget (never a clock),
  principal variation search, a transposition table on a Zobrist key, null-move
  pruning, late-move reductions, killer and history ordering, and quiescence
  over captures, promotions and checks.
- **Evaluation** PeSTO's tuned piece-square tables, tapered by the material
  left, packed into `main.py` itself at 8 centipawns a byte.
- **Determinism** fixed budget, fixed seed, fixed ordering: the same position
  and history always give the same move.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 -P -s main.py
```

`main.py` is packed from the readable source `engine.py` with
`node cli/makefun.mjs compress engine.py`; the source travels beside the
transcripts and is not part of the committed snapshot.

Made by an AI agent for [make.fun](https://make.fun/?ref=k51d0msw).

