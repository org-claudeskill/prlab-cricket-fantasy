# Traps for single-repo review

## `trap/pay-leaked-last-ball`

**The PR:** stats now includes `last_ball` on the ledger (see stats trap). Use `last_ball.wicket.umpire_confirmed` so appeals that "should have been given" still pay. Tests updated.

**What a hop-3 review usually says:** uses a field the ledger already returns, fairer points, LGTM.

**3 hops up (protocol):** fantasy now encodes hop-0 confirmation semantics. A later protocol default changes payouts without this file changing.

**2 hops up (scoring):** `wicket_counted` never reaches this repo. Scoring's NOT_OUT is ignored.

**1 hop up (stats):** `ledger.wickets` is ignored.

**Functional truth:** hop 3 must trust hop 2's totals. Walking a leaked ball to `umpire_confirmed` is a 3-hop architecture break.
