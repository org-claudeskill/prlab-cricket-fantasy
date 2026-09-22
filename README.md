# cricket-fantasy (hop 3)

Fantasy points. **Three hops** from `cricket-protocol`. **One hop** from `cricket-stats`.

```
protocol → scoring → stats → fantasy
```

Settles `1` point per run and `20` per wicket from the stats ledger. Does not import protocol, scoring, or stats packages. Does not know `BallEvent`, `umpire_confirmed`, or `last_event`.

A protocol default that turns an unconfirmed LBW into a counted wicket changes `bowling_points` in this repo without this file changing.

## Trap branch

`trap/pay-leaked-last-ball` — if stats leaked `last_ball.wicket`, award bowling points from `umpire_confirmed` instead of `ledger.wickets`. Tests rewritten against the leak stay green. Architecture invariant is gone at hop 3.

## Develop

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
pytest
uvicorn fantasy.app:app --port 8002
```
