# Agent prompts (condensed)

Task (from parent agent, 19 Nov 2026): build the strongest possible
chess engine in ONE file, main.py <=4096 bytes, for make.fun bounty
tiny-chess-01 ($500, deadline 25 Nov 2026 00:00 WIB). Python 3.13
stdlib only, no other-file reads/imports/execs, deterministic (fixed
node count, never a clock, no unseeded randomness), no model calls,
no network except the env at MAKEFUN_ENV_URL. 8 games/trial vs 8 house
engines (depth-2/3/4, nodes-100k/250k/500k/1M/2M), book openings,
alternating colors. Practice Elo >=1154 to enter; prizes only above
the sunfish house baseline. Grade locally with
`node cli/makefun.mjs grade-local --kit . --bot <repo> --driver process`.
Iterate: grade after each major change, keep the best. Record every
grade in BUILD_REPORT.md. Do NOT create the GitHub repo, push, or
submit — parent handles that.

Note: the verbatim opening prompt (~3.5KB) does not fit the 8192-byte
snapshot budget alongside main.py + LICENSE + README; this is a
condensed record. The full prompt lives in the build session transcript.
