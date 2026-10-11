# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **13:23:51 CEST / 11:23:51 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 1,430 tx/s; last clean level 1,300 |
| Network unique accepted, last complete minute (n2 count) | 3,286.3 tx/s (13:07 CEST) |
| Network best minute so far / mean since START | 3,475.6 (12:41 CEST) / 2,811.5 tx/s (198 valid minutes) |
| Bot submitted, last 10 min | 1.6 tx/s (951 tx) |
| Bot accepted on n2, last 10 min | 1.0 tx/s (592 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 17 (processes up: 4) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 85 |
| HALT | no |

## Changes during the run

| CEST | Change |
|---|---|
| 11:28 | **stp asked both sides to increase effort.** Bot raised 1,011 -> 1,300 tx/s at 11:29 (rate-change). New rate rule for the rest of the run: floor 1,100; +10% after every clean 15 min up to 2,400; a not-clean window lowers by 5% only on real overload (accepted < 95% of submitted or rejects >= 2%), otherwise the rate holds. |
| 11:30-11:34 | Senders 15 -> 18 (staggered, each on 4 of the 5 public nodes; extra senders launch only while box RAM >= 2.5 GB, never under 1.5 GB). Deviation from GO-BOT (max 15 senders for box RAM): 'stp 11:28 increase effort'. |
| 11:28 | Build is increasing effort as well (Build's side, see Build's logs). |
| 11:49 | **stp: bot fee +40% at the next rate climb**, 400/600 -> 560/840 sompi/gram, cap 840 for this run (above the GO cap 600: deviation). Node-quote-skip threshold stays 400. Fired at **12:31:10 CEST** with the rate climb 1,300 -> 1,430 (re-checked 12:14-12:29 window). |
| 12:31 | Fix: the 15-minute rate check undercounted submitted tx (a non-integer read offset skipped sender files; the 11:15/11:44/12:14/12:29 checks read 0-209 tx/s while the bot sent ~1,060-1,300). Re-checked 12:14-12:29 with full data: 1,291.9 / 1,291.5 tx/s, 99.97%, 0 rejects -> clean -> 1,300 -> 1,430 tx/s, fees 560/840 from 12:31:10. |
| 11:50 | stp: **Build asked to climb like the bot** (+10% per clean 15 min, -5% only on real overload, floor = its 11:50 rate) and to raise its fees +40% at its next climb (public share 200/300 -> 280/420; desk pair x1.4). Build's side, see Build's logs. |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| boson-10.kaspa.red | 0 | 0 | 0 | 0 |
| electron-10.kaspa.blue | 236 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 243 | 0 | 0 | 0 |
| neutrino-10.kaspa.stream | 237 | 0 | 0 | 0 |
| vector-10.kaspa.green | 235 | 0 | 0 | 0 |

## Kaspa Pulse method (live mirror)

**Monitoring started 10:48Z (12:48 CEST)**, runs until END 12:30Z (14:30 CEST). Kaspa Pulse's counter: transactions accepted in blocks, per UTC minute, by block time, on two independent nodes (n2 and the public node muon-10.kaspa.blue, side by side). Earlier minutes of the run (from 07:30Z) come from the post-END chain count. File: [pulse-method-minute.csv](pulse-method-minute.csv), with network blocks (blue/red) and our miner per UTC minute.

**Every network count includes TN10 base load of about 56 tx/s** (figure from Kaspa Pulse).

| UTC minute | CEST | n2 accepted tx/s | public node tx/s | diff (tx) | blue blocks | our blocks | our hashrate | note |
|---|---|---:|---:|---:|---:|---:|---|---|
| 2026-10-11T11:01Z | 13:01 | 3416.0 | 3416.0 | 0 | 647 | 217 | 6.10 Mhash/s |  |
| 2026-10-11T11:02Z | 13:02 | 3259.2 | 3259.2 | 0 | 574 | 180 | 6.02 Mhash/s |  |
| 2026-10-11T11:03Z | 13:03 | 3357.0 | 3357.0 | 0 | 631 | 186 | 6.12 Mhash/s |  |
| 2026-10-11T11:04Z | 13:04 | 3332.6 | 3332.6 | 0 | 614 | 185 | 6.12 Mhash/s |  |
| 2026-10-11T11:05Z | 13:05 | 3289.3 | 3289.3 | 0 | 592 | 196 | 6.13 Mhash/s |  |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | False / False |
| n2 sink age (lag) | 899.3 s |
| n2 virtual DAA score | 593,826,615 |
| Miner processes | 1 |
| Lane tips at last sender boots | 174,307 tKAS in 3,600 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 29 GB / 5,484 MB |

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
| 12:14 | 1,300 | 168.9 | 168.1 | 0.00 | 2.21 | 42.2 | no: 3 node-dead events; submitted 168.9 < 90% of 1300 | 1,300 |
| 12:29 | 1,300 | 209.0 | 209.0 | 0.00 | 1.78 | 42.6 | no: submitted 209 < 90% of 1300 | 1,300 |
| 12:29 | 1,300 | 1,291.9 | 1,291.5 | 0.00 | 1.78 | 42.6 | yes | 1,430 |
| 12:44 | 1,430 | 1,389.1 | 1,388.4 | 0.00 | 1.10 | 48.0 | no: box RAM min 1.1 GB < 1.5 | 1,430 |
| 12:59 | 1,430 | 1,346.8 | 1,348.8 | 0.00 | 1.01 | 54.8 | no: box RAM min 1.01 GB < 1.5 | 1,430 |
| 13:23 | 1,430 | 21.3 | 21.1 | 0.00 | 1.35 | 45.9 | no: submitted 21.3 < 90% of 1430; box RAM min 1.35 GB < 1.5 | 1,430 |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 13:23:40 | sender-stall | window | S16 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh |
| 13:23:40 | sender-stall | window | S17 stalled: 0 ok submits in 45 s (0 sec rows), 0 accepts in 60 s, erroring nodes [], main - -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 | node-dead | window | electron-10.kaspa.blue: 3 strikes in 10 min (S18 main: no accepts in 60 s); new picks avoid it |
| 13:23:40 | sender-stall | window | S18 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fres |
| 13:23:41 | sender-relaunch | window | S1 relaunch 7/200 |
| 13:23:41 | sender-start | window | S1 mode=pub |
| 13:23:44 | sender-relaunch | window | S2 relaunch 7/200 |
| 13:23:44 | sender-start | window | S2 mode=pub |
| 13:23:47 | sender-relaunch | window | S3 relaunch 8/200 |
| 13:23:47 | sender-start | window | S3 mode=pub |
| 13:23:51 | sender-relaunch | window | S4 relaunch 7/200 |
| 13:23:51 | sender-start | window | S4 mode=pub |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
