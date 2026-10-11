# blackjack-agent

A Blackjack environment and reinforcement learning agent that learns optimal play from
scratch. It includes a full game simulator, a Monte Carlo basic strategy solver, tabular
Q-learning, and Hi-Lo card counting with bet sizing.

This is a **learning project**: every module is implemented step by step, guided by
failing tests, with the goal of understanding *why* basic strategy falls out of the maths
and how an RL agent rediscovers it on its own.

## Features (planned)

- **Game simulator**: 6-deck shoe with configurable penetration, cut-card reshuffles,
  dealer stands/hits soft 17, double after split, late surrender, 3:2 blackjacks.
- **Monte Carlo basic strategy solver**: derives the hit/stand/double/split/surrender
  chart from scratch by comparing expected value (EV) of every action in every state.
- **Hi-Lo card counting**: running count, true count, bet ramp, and a subset of the
  "Illustrious 18" playing deviations.
- **Tabular Q-learning agent**: learns playing decisions from scratch through trial and
  error, benchmarked against the derived basic strategy.

## Roadmap

| Phase | Module | What it does |
|-------|--------|--------------|
| 1 | `blackjack_agent/cards.py` | Ranks, hand values, Hi-Lo tags, shoe with running/true count |
| 2 | `blackjack_agent/env.py` | Blackjack round environment: actions, dealer AI, payouts |
| 3 | `blackjack_agent/basic.py` | Monte Carlo EV evaluation + policy iteration → basic strategy chart |
| 4 | `blackjack_agent/counting.py` | Bet ramp and Hi-Lo playing deviations |
| 5 | `blackjack_agent/qlearning.py` | Tabular Q-learning agent (epsilon-greedy) |
| 6 | `blackjack_agent/simulate.py` | Round simulator, EV/bankroll statistics, CLI experiments |

## Getting started

Requires Python 3.10+ (standard library only).

```bash
python3 -m unittest discover -s tests -v          # run tests
python3 -m blackjack_agent derive --trials 2000     # derive basic strategy (planned)
python3 -m blackjack_agent simulate --rounds 100000 # run experiments (planned)
```

## Project layout

```
blackjack-agent/
├── blackjack_agent/     # package source
├── tests/               # unittest test suites (spec for each phase)
├── data/                # generated artefacts: strategy tables, Q tables, bankroll curves
└── README.md
```

## License

[MIT](LICENSE)
