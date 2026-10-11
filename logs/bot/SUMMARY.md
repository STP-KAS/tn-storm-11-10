# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **09:15:12 CEST / 07:15:12 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **G1 (no sends)**, until 09:20 CEST / 07:20 UTC |
| Bot target now (ramp) | 0 tx/s; last clean level – |
| Network unique accepted, last complete minute (n2 count) | – tx/s |
| Network best minute so far / mean since START | – / – tx/s (0 valid minutes) |
| Bot submitted, last 10 min | 0.0 tx/s (0 tx) |
| Bot accepted on n2, last 10 min | 0.0 tx/s (0 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 0 (processes up: 0) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 0 |
| HALT | no |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| (no sends in this window) | – | – | – | – |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.5 s |
| n2 virtual DAA score | 593,682,716 |
| Miner processes | 0 |
| Lane tips at last sender boots | 0 tKAS in 0 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 34 GB / 6,075 MB |

## Rate checks (every 15 min over the full last 15 min: +10% if clean, -10% if not)

| Eval (CEST) | Level | Submitted tx/s | Accepted tx/s | Rejects % | RAM min GB | CPU avg % | Clean | Next |
|---|---:|---:|---:|---:|---:|---:|---|---:|
| (first eval 15 min after START 09:30 CEST / 07:30 UTC) | – | – | – | – | – | – | – | – |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 08:43:33 | plan | - | STP-KAS/tn-storm-11-10 go/bot/GO-BOT.md (locked, pasted by stp 08:39 CEST) |
| 08:43:33 | deviation | - | pubMode: n2 utxoindex off; senders continue on public nodes |
| 09:00:00 | gate | - | G1 fail synced true utxoindex false lag 0.4 |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
