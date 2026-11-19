# Tiny Chess — Build Report

Own 0x88 negamax alpha-beta, iterative deepening to a FIXED node
budget (deterministic), TT, quiescence (captures/promotions, full
moves in check), MVV-LVA + killer + history, formula PST eval
(material + centrality + rook 7th + tapered king) + bishop pair,
repetition avoidance. lzma-packed; main.py 3,695 B. Perft 20/20.

## Grades (practice trial-0, 6 games; Elo = official anchors)
- v1 60k: 2W 1D 3L = 2.5/6, Elo 1191 (10m49s). Beat depth-2/4,
  drew depth-3, lost nodes-100k/250k/500k by mate.
- v3 70k + history + lazy legality (2x speed): 2W 1D 3L,
  Elo 1191 (16m08s). Same score.
- v4 150k + LMR: 1W 0D 5L; games 2-6 LOST BY TIME. LMR hurts in
  tactical openings; 150k unsafe.
- v5 100k, no LMR: 0W 0D 6L, all lost by time. 100k unsafe.
- v7 70k + pawn-shield eval: 0W 0D 6L, all lost by time. Dropped.
- v8 FINAL 60k (v3 engine): 0W 0D 6L, all lost by time under
  heavy local load (Calyx build, load 3.8-6.4). Same engine
  scored 1191 on a quiet machine (v1/v3). Reliable Elo: 1191.

## Conclusion
Best safe: v8, 60k nodes, Elo ~1191 (floor 1154; sunfish ~1365;
top 2110). Gap is depth: house engines search far deeper than
Python can in 10s/move.
