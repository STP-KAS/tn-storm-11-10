# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **11:15:09 CEST / 09:15:09 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 1,011 tx/s; last clean level 1,112 |
| Network unique accepted, last complete minute (n2 count) | 3,037.4 tx/s (11:14 CEST) |
| Network best minute so far / mean since START | 3,421.3 (10:44 CEST) / 2,735.3 tx/s (91 valid minutes) |
| Bot submitted, last 10 min | 1,109.1 tx/s (665,452 tx) |
| Bot accepted on n2, last 10 min | 1,110.5 tx/s (666,318 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 15 (processes up: 15) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 30 |
| HALT | no |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| boson-10.kaspa.red | 166,802 | 0 | 0 | 0 |
| electron-10.kaspa.blue | 166,830 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 165,033 | 0 | 0 | 0 |
| vector-10.kaspa.green | 166,787 | 0 | 0 | 0 |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.4 s |
| n2 virtual DAA score | 593,758,366 |
| Miner processes | 1 |
| Lane tips at last sender boots | 147,230 tKAS in 3,000 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 34 GB / 3,386 MB |

## Rate checks (every 15 min over the full last 15 min: +10% if clean, -10% if not)

| Eval (CEST) | Level | Submitted tx/s | Accepted tx/s | Rejects % | RAM min GB | CPU avg % | Clean | Next |
|---|---:|---:|---:|---:|---:|---:|---|---:|
| 09:45 | 919 | 587.9 | 587.1 | 0.00 | 2.98 | 48.0 | no: 2 node-dead events; submitted 587.9 < 90% of 919 | 835 |
| 10:00 | 835 | 833.5 | 834.1 | 0.00 | 2.48 | 48.5 | yes | 919 |
| 10:15 | 919 | 900.0 | 898.8 | 0.00 | 2.56 | 37.2 | yes | 1,011 |
| 10:30 | 1,011 | 1,009.5 | 1,009.6 | 0.00 | 2.46 | 39.8 | yes | 1,112 |
| 10:45 | 1,112 | 1,100.8 | 1,100.6 | 0.00 | 2.32 | 40.0 | yes | 1,223 |
| 11:00 | 1,223 | 884.1 | 882.1 | 0.00 | 2.21 | 40.4 | no: 4 node-dead events; submitted 884.1 < 90% of 1223 | 1,112 |
| 11:15 | 1,112 | 0.0 | 0.0 | 0.00 | 3.05 | 42.3 | no: accepted -% of submitted < 99%; p90 - s > 10; submitted 0 < 90% of 1112 | 1,011 |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 10:50:04 | sender-start | window | S11 mode=pub |
| 10:50:07 | sender-relaunch | window | S12 relaunch 2/200 |
| 10:50:07 | sender-start | window | S12 mode=pub |
| 10:50:10 | sender-relaunch | window | S13 relaunch 2/200 |
| 10:50:10 | sender-start | window | S13 mode=pub |
| 10:50:13 | sender-relaunch | window | S14 relaunch 2/200 |
| 10:50:13 | sender-start | window | S14 mode=pub |
| 10:50:16 | sender-relaunch | window | S15 relaunch 2/200 |
| 10:50:16 | sender-start | window | S15 mode=pub |
| 10:51 | deviation | window | day-watch: mass stall all 15 senders at 10:49:33 CEST; scheduler auto SIGKILL+relaunch 2/200 with fresh picks + public-node stall-strike avoid (muon/boson/elect |
| 11:00:01 | rate-change | window | RAMP EVAL 10:45-11:00 CEST at 1223 tx/s: sub/acc 884.1/882.1 tx/s, acc/sub 99.77%, rejects 0% (+2 transport), RAM min 2.21 GB, CPU avg 40.4% -> NOT clean (4 nod |
| 11:15:01 | rate-change | window | RAMP EVAL 11:00-11:15 CEST at 1112 tx/s: sub/acc 0/0 tx/s, acc/sub -%, rejects 0% (+0 transport), RAM min 3.05 GB, CPU avg 42.3% -> NOT clean (accepted -% of su |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
