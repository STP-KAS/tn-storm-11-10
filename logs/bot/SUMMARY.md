# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **10:15:15 CEST / 08:15:15 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 1,011 tx/s; last clean level 919 |
| Network unique accepted, last complete minute (n2 count) | 3,108.1 tx/s (10:14 CEST) |
| Network best minute so far / mean since START | 3,156.0 (10:12 CEST) / 2,434.4 tx/s (37 valid minutes) |
| Bot submitted, last 10 min | 892.7 tx/s (535,632 tx) |
| Bot accepted on n2, last 10 min | 892.5 tx/s (535,479 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 15 (processes up: 15) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 15 |
| HALT | no |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| boson-10.kaspa.red | 133,825 | 0 | 0 | 0 |
| electron-10.kaspa.blue | 133,951 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 133,938 | 0 | 0 | 0 |
| neutrino-10.kaspa.stream | 133,918 | 0 | 0 | 0 |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.1 s |
| n2 virtual DAA score | 593,721,384 |
| Miner processes | 1 |
| Lane tips at last sender boots | 147,437 tKAS in 3,000 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 34 GB / 2,711 MB |

## Rate checks (every 15 min over the full last 15 min: +10% if clean, -10% if not)

| Eval (CEST) | Level | Submitted tx/s | Accepted tx/s | Rejects % | RAM min GB | CPU avg % | Clean | Next |
|---|---:|---:|---:|---:|---:|---:|---|---:|
| 09:45 | 919 | 587.9 | 587.1 | 0.00 | 2.98 | 48.0 | no: 2 node-dead events; submitted 587.9 < 90% of 919 | 835 |
| 10:00 | 835 | 833.5 | 834.1 | 0.00 | 2.48 | 48.5 | yes | 919 |
| 10:15 | 919 | 900.0 | 898.8 | 0.00 | 2.56 | 37.2 | yes | 1,011 |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 09:43:42 | sender-start | window | S11 mode=pub |
| 09:43:45 | sender-relaunch | window | S12 relaunch 1/200 |
| 09:43:45 | sender-start | window | S12 mode=pub |
| 09:43:48 | sender-relaunch | window | S13 relaunch 1/200 |
| 09:43:48 | sender-start | window | S13 mode=pub |
| 09:43:51 | sender-relaunch | window | S14 relaunch 1/200 |
| 09:43:51 | sender-start | window | S14 mode=pub |
| 09:43:54 | sender-relaunch | window | S15 relaunch 1/200 |
| 09:43:54 | sender-start | window | S15 mode=pub |
| 09:45:04 | rate-change | window | RAMP EVAL 09:30-09:45 CEST at 919 tx/s: sub/acc 587.9/587.1 tx/s, acc/sub 99.86%, rejects 0% (+0 transport), RAM min 2.98 GB, CPU avg 48% -> NOT clean (2 node-d |
| 10:00:00 | rate-change | window | RAMP EVAL 09:45-10:00 CEST at 835 tx/s: sub/acc 833.5/834.1 tx/s, acc/sub 100%, rejects 0% (+0 transport), RAM min 2.48 GB, CPU avg 48.5% -> clean; rate 835 ->  |
| 10:15:00 | rate-change | window | RAMP EVAL 10:00-10:15 CEST at 919 tx/s: sub/acc 900/898.8 tx/s, acc/sub 99.87%, rejects 0% (+0 transport), RAM min 2.56 GB, CPU avg 37.2% -> clean; rate 919 ->  |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
