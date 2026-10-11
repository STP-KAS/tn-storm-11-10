# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **12:00:46 CEST / 10:00:46 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 1,300 tx/s; last clean level 1,112 |
| Network unique accepted, last complete minute (n2 count) | 3,187.1 tx/s (11:55 CEST) |
| Network best minute so far / mean since START | 3,421.3 (10:44 CEST) / 2,694.0 tx/s (132 valid minutes) |
| Bot submitted, last 10 min | 708.2 tx/s (424,938 tx) |
| Bot accepted on n2, last 10 min | 704.7 tx/s (422,796 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 18 (processes up: 3) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 49 |
| HALT | no |

## Changes during the run

| CEST | Change |
|---|---|
| 11:28 | **stp asked both sides to increase effort.** Bot raised 1,011 -> 1,300 tx/s at 11:29 (rate-change). New rate rule for the rest of the run: floor 1,100; +10% after every clean 15 min up to 2,400; a not-clean window lowers by 5% only on real overload (accepted < 95% of submitted or rejects >= 2%), otherwise the rate holds. |
| 11:30-11:34 | Senders 15 -> 18 (staggered, each on 4 of the 5 public nodes; extra senders launch only while box RAM >= 2.5 GB, never under 1.5 GB). Deviation from GO-BOT (max 15 senders for box RAM): 'stp 11:28 increase effort'. |
| 11:28 | Build is increasing effort as well (Build's side, see Build's logs). |
| 11:49 | **stp: bot fee +40% at the next rate climb**, 400/600 -> 560/840 sompi/gram, cap 840 for this run (above the GO cap 600: deviation). Node-quote-skip threshold stays 400. Armed 11:50; fires with the next rate increase. |
| 11:50 | stp: **Build asked to climb like the bot** (+10% per clean 15 min, -5% only on real overload, floor = its 11:50 rate) and to raise its fees +40% at its next climb (public share 200/300 -> 280/420; desk pair x1.4). Build's side, see Build's logs. |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| boson-10.kaspa.red | 95,403 | 0 | 0 | 0 |
| electron-10.kaspa.blue | 84,750 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 78,612 | 0 | 0 | 0 |
| neutrino-10.kaspa.stream | 69,938 | 0 | 0 | 0 |
| vector-10.kaspa.green | 96,235 | 0 | 0 | 0 |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.7 s |
| n2 virtual DAA score | 593,783,317 |
| Miner processes | 1 |
| Lane tips at last sender boots | 175,896 tKAS in 3,600 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 33 GB / 5,693 MB |

## Rate checks (every 15 min over the full last 15 min: +10% if clean; until 11:28 CEST -10% if not; from 11:28 CEST floor 1,100 and -5% only on real overload, else hold)

| Eval (CEST) | Level | Submitted tx/s | Accepted tx/s | Rejects % | RAM min GB | CPU avg % | Clean | Next |
|---|---:|---:|---:|---:|---:|---:|---|---:|
| 09:45 | 919 | 587.9 | 587.1 | 0.00 | 2.98 | 48.0 | no: 2 node-dead events; submitted 587.9 < 90% of 919 | 835 |
| 10:00 | 835 | 833.5 | 834.1 | 0.00 | 2.48 | 48.5 | yes | 919 |
| 10:15 | 919 | 900.0 | 898.8 | 0.00 | 2.56 | 37.2 | yes | 1,011 |
| 10:30 | 1,011 | 1,009.5 | 1,009.6 | 0.00 | 2.46 | 39.8 | yes | 1,112 |
| 10:45 | 1,112 | 1,100.8 | 1,100.6 | 0.00 | 2.32 | 40.0 | yes | 1,223 |
| 11:00 | 1,223 | 884.1 | 882.1 | 0.00 | 2.21 | 40.4 | no: 4 node-dead events; submitted 884.1 < 90% of 1223 | 1,112 |
| 11:15 | 1,112 | 0.0 | 0.0 | 0.00 | 3.05 | 42.3 | no: accepted -% of submitted < 99%; p90 - s > 10; submitted 0 < 90% of 1112 | 1,011 |
| 11:44 | 1,300 | 187.3 | 186.9 | 0.00 | 2.44 | 40.2 | no: submitted 187.3 < 90% of 1300 | 1,300 |
| 12:00 | 1,300 | 915.0 | 911.6 | 0.00 | 2.34 | 41.2 | no: submitted 915 < 90% of 1300 | 1,300 |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 12:00:39 | sender-stall | window | S14 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fr |
| 12:00:39 | sender-stall | window | S15 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fres |
| 12:00:39 | node-dead | window | electron-10.kaspa.blue: 3 strikes in 10 min (S16 main: no accepts in 60 s); new picks avoid it |
| 12:00:39 | sender-stall | window | S16 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fres |
| 12:00:39 | sender-stall | window | S17 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh |
| 12:00:39 | sender-stall | window | S18 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fres |
| 12:00:41 | sender-relaunch | window | S1 relaunch 4/200 |
| 12:00:41 | sender-start | window | S1 mode=pub |
| 12:00:44 | sender-relaunch | window | S2 relaunch 4/200 |
| 12:00:44 | sender-start | window | S2 mode=pub |
| 12:00:47 | sender-relaunch | window | S3 relaunch 4/200 |
| 12:00:47 | sender-start | window | S3 mode=pub |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
