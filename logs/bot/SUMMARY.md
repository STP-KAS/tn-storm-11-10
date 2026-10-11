# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **13:30:19 CEST / 11:30:19 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 1,430 tx/s; last clean level 1,300 |
| Network unique accepted, last complete minute (n2 count) | 3,423.1 tx/s (13:29 CEST) |
| Network best minute so far / mean since START | 3,583.1 (13:28 CEST) / 2,818.4 tx/s (200 valid minutes) |
| Bot submitted, last 10 min | 876.3 tx/s (525,807 tx) |
| Bot accepted on n2, last 10 min | 871.8 tx/s (523,108 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 18 (processes up: 18) |
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
| electron-10.kaspa.blue | 131,108 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 130,486 | 0 | 0 | 0 |
| neutrino-10.kaspa.stream | 131,625 | 0 | 0 | 0 |
| vector-10.kaspa.green | 132,588 | 0 | 0 | 0 |

## Kaspa Pulse method (live mirror)

**Monitoring started 10:48Z (12:48 CEST)**, runs until END 12:30Z (14:30 CEST). Kaspa Pulse's counter: transactions accepted in blocks, per UTC minute, by block time, on two independent nodes (n2 and the public node muon-10.kaspa.blue, side by side). Earlier minutes of the run (from 07:30Z) come from the post-END chain count. File: [pulse-method-minute.csv](pulse-method-minute.csv), with network blocks (blue/red) and our miner per UTC minute.

**Every network count includes TN10 base load of about 56 tx/s** (figure from Kaspa Pulse).

| UTC minute | CEST | n2 accepted tx/s | public node tx/s | diff (tx) | blue blocks | our blocks | our hashrate | note |
|---|---|---:|---:|---:|---:|---:|---|---|
| 2026-10-11T11:21Z | 13:21 | 2025.8 | 2025.8 | 0 | 490 |  |  | miner chain row missing |
| 2026-10-11T11:22Z | 13:22 | 2028.7 | 2028.7 | 0 | 474 |  |  | miner chain row missing |
| 2026-10-11T11:26Z | 13:26 | 2830.3 | 2830.3 | 0 | 460 | 172 | 5.58 Mhash/s |  |
| 2026-10-11T11:23Z | 13:23 | 2039.4 | 2039.4 | 0 | 464 |  | 5.71 Mhash/s | miner chain row missing |
| 2026-10-11T11:27Z | 13:27 | 3041.6 | 3041.6 | 0 | 515 | 207 | 5.97 Mhash/s |  |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.5 s |
| n2 virtual DAA score | 593,837,418 |
| Miner processes | 1 |
| Lane tips at last sender boots | 173,842 tKAS in 3,600 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 28 GB / 2,787 MB |

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
| 13:29 | 1,430 | 543.8 | 540.8 | 0.00 | 1.38 | 56.4 | no: 5 node-dead events; submitted 543.8 < 90% of 1430; box RAM min 1.38 GB < 1.5 | 1,430 |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 13:24:24 | sender-start | window | S15 mode=pub |
| 13:24:27 | sender-relaunch | window | S16 relaunch 6/200 |
| 13:24:27 | sender-start | window | S16 mode=pub |
| 13:24:30 | sender-relaunch | window | S17 relaunch 9/200 |
| 13:24:30 | sender-start | window | S17 mode=pub |
| 13:24:33 | sender-relaunch | window | S18 relaunch 5/200 |
| 13:24:33 | sender-start | window | S18 mode=pub |
| 13:24:39 | miner-off | window | n2 not synced for 60 s |
| 13:25:29 | node-restart | window | kaspad pid changed (n2 restarted on the same flags by its guard), uptime 1 s |
| 13:25 | node-restart | window | GO freeze: DAA stuck 593826615 since ~13:08 CEST, sink lag ~986s; restarted n2 same flags via start-n2.sh pid - (old 2857338); miner was already OFF |
| 13:26:05 | miner-on | window | n2 synced again / process relaunch |
| 13:29:53 | rate-eval | window | RAMP EVAL 13:14-13:29 CEST at 1430 tx/s: sub/acc 543.8/540.8 tx/s, acc/sub 99.43%, rejects 0% (+0 transport), RAM min 1.38 GB, CPU avg 56.4% -> NOT clean (5 nod |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
