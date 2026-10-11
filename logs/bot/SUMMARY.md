# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **10:45:13 CEST / 08:45:13 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 1,223 tx/s; last clean level 1,112 |
| Network unique accepted, last complete minute (n2 count) | 3,421.3 tx/s (10:44 CEST) |
| Network best minute so far / mean since START | 3,421.3 (10:44 CEST) / 2,733.6 tx/s (67 valid minutes) |
| Bot submitted, last 10 min | 1,095.8 tx/s (657,491 tx) |
| Bot accepted on n2, last 10 min | 1,095.2 tx/s (657,104 tx) |
| Rejects, last 10 min | 4 consensus/mempool; 4 public-node transport errors |
| Senders writing rows | 15 (processes up: 15) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 15 |
| HALT | no |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| boson-10.kaspa.red | 164,031 | 4 | 4 | 0 |
| electron-10.kaspa.blue | 164,227 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 165,073 | 0 | 0 | 0 |
| neutrino-10.kaspa.stream | 164,160 | 0 | 0 | 0 |

Rejects by class: already_in_mempool 4, rpc 4

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.7 s |
| n2 virtual DAA score | 593,741,103 |
| Miner processes | 1 |
| Lane tips at last sender boots | 147,437 tKAS in 3,000 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 35 GB / 2,613 MB |

## Rate checks (every 15 min over the full last 15 min: +10% if clean, -10% if not)

| Eval (CEST) | Level | Submitted tx/s | Accepted tx/s | Rejects % | RAM min GB | CPU avg % | Clean | Next |
|---|---:|---:|---:|---:|---:|---:|---|---:|
| 09:45 | 919 | 587.9 | 587.1 | 0.00 | 2.98 | 48.0 | no: 2 node-dead events; submitted 587.9 < 90% of 919 | 835 |
| 10:00 | 835 | 833.5 | 834.1 | 0.00 | 2.48 | 48.5 | yes | 919 |
| 10:15 | 919 | 900.0 | 898.8 | 0.00 | 2.56 | 37.2 | yes | 1,011 |
| 10:30 | 1,011 | 1,009.5 | 1,009.6 | 0.00 | 2.46 | 39.8 | yes | 1,112 |
| 10:45 | 1,112 | 1,100.8 | 1,100.6 | 0.00 | 2.32 | 40.0 | yes | 1,223 |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 09:43:48 | sender-relaunch | window | S13 relaunch 1/200 |
| 09:43:48 | sender-start | window | S13 mode=pub |
| 09:43:51 | sender-relaunch | window | S14 relaunch 1/200 |
| 09:43:51 | sender-start | window | S14 mode=pub |
| 09:43:54 | sender-relaunch | window | S15 relaunch 1/200 |
| 09:43:54 | sender-start | window | S15 mode=pub |
| 09:45:04 | rate-change | window | RAMP EVAL 09:30-09:45 CEST at 919 tx/s: sub/acc 587.9/587.1 tx/s, acc/sub 99.86%, rejects 0% (+0 transport), RAM min 2.98 GB, CPU avg 48% -> NOT clean (2 node-d |
| 10:00:00 | rate-change | window | RAMP EVAL 09:45-10:00 CEST at 835 tx/s: sub/acc 833.5/834.1 tx/s, acc/sub 100%, rejects 0% (+0 transport), RAM min 2.48 GB, CPU avg 48.5% -> clean; rate 835 ->  |
| 10:15:00 | rate-change | window | RAMP EVAL 10:00-10:15 CEST at 919 tx/s: sub/acc 900/898.8 tx/s, acc/sub 99.87%, rejects 0% (+0 transport), RAM min 2.56 GB, CPU avg 37.2% -> clean; rate 919 ->  |
| 10:28:55 | day-watch | window | 10:28 CEST check: healthy; target 1011; live sub/acc ~1010/1005; 15 senders; miner 1; disk 34G; MemAvail ~2.5G; no fix |
| 10:30:01 | rate-change | window | RAMP EVAL 10:15-10:30 CEST at 1011 tx/s: sub/acc 1009.5/1009.6 tx/s, acc/sub 100%, rejects 0% (+2 transport), RAM min 2.46 GB, CPU avg 39.8% -> clean; rate 1011 |
| 10:45:01 | rate-change | window | RAMP EVAL 10:30-10:45 CEST at 1112 tx/s: sub/acc 1100.8/1100.6 tx/s, acc/sub 99.98%, rejects 0% (+4 transport), RAM min 2.32 GB, CPU avg 40% -> clean; rate 1112 |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
