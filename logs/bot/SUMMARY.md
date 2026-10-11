# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **09:30:21 CEST / 07:30:21 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 919 tx/s; last clean level – |
| Network unique accepted, last complete minute (n2 count) | – tx/s |
| Network best minute so far / mean since START | – / – tx/s (0 valid minutes) |
| Bot submitted, last 10 min | 31.0 tx/s (18,609 tx) |
| Bot accepted on n2, last 10 min | 29.4 tx/s (17,664 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 15 (processes up: 15) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 0 |
| HALT | no |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| boson-10.kaspa.red | 4,033 | 0 | 0 | 0 |
| electron-10.kaspa.blue | 3,416 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 2,771 | 0 | 0 | 0 |
| neutrino-10.kaspa.stream | 4,348 | 0 | 0 | 0 |
| vector-10.kaspa.green | 4,041 | 0 | 0 | 0 |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.4 s |
| n2 virtual DAA score | 593,693,615 |
| Miner processes | 1 |
| Lane tips at last sender boots | 147,647 tKAS in 3,000 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 21 GB / 3,869 MB |

## Rate checks (every 15 min over the full last 15 min: +10% if clean, -10% if not)

| Eval (CEST) | Level | Submitted tx/s | Accepted tx/s | Rejects % | RAM min GB | CPU avg % | Clean | Next |
|---|---:|---:|---:|---:|---:|---:|---|---:|
| (first eval 15 min after START 09:30 CEST / 07:30 UTC) | – | – | – | – | – | – | – | – |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 09:19:27 | sender-start | - | S10 mode=pub |
| 09:19:30 | sender-start | - | S11 mode=pub |
| 09:19:33 | sender-start | - | S12 mode=pub |
| 09:19:36 | sender-start | - | S13 mode=pub |
| 09:19:39 | sender-start | - | S14 mode=pub |
| 09:19:42 | sender-start | - | S15 mode=pub |
| 09:20:00 | gate | - | G2 fail synced true utxoindex false lag 0.5 |
| 09:20:00 | build-confirmed | - | at G2 |
| 09:20:00 | build-confirmed | - | BUILD-OK |
| 09:20:00 | miner-on | - | 07:20 UTC start, n2 synced |
| 09:30:00 | step-start | window | window bot max |
| 09:30:00 | deviation | window | Build ready file (FOR-TN10-OPS-ready-1110.txt) not passed to the bot by START 09:30 CEST; bot does not wait (GO-BOT) |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
