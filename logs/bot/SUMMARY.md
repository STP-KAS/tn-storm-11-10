# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **14:15:35 CEST / 12:15:35 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 15:30 CEST / 13:30 UTC |
| Bot target now (ramp) | 1,573 tx/s; last clean level 1,430 |
| Network unique accepted, last complete minute (n2 count) | 814.3 tx/s (14:14 CEST) |
| Network best minute so far / mean since START | 3,606.2 (13:47 CEST) / 2,895.7 tx/s (245 valid minutes) |
| Bot submitted, last 10 min | 1,406.9 tx/s (844,164 tx) |
| Bot accepted on n2, last 10 min | 1,403.6 tx/s (842,144 tx) |
| Rejects, last 10 min | 8 consensus/mempool; 3 public-node transport errors |
| Senders writing rows | 18 (processes up: 18) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 86 |
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
| boson-10.kaspa.red | 166,669 | 0 | 0 | 0 |
| electron-10.kaspa.blue | 147,396 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 177,704 | 1 | 0 | 0 |
| neutrino-10.kaspa.stream | 146,268 | 3 | 3 | 0 |
| vector-10.kaspa.green | 206,127 | 4 | 0 | 0 |

Rejects by class: already_in_mempool 8, rpc 3

## Kaspa Pulse method (live mirror)

**Monitoring started 10:48Z (12:48 CEST)**, runs until END 13:30Z (15:30 CEST; extended +1h by stp 12:13Z). Kaspa Pulse's counter: transactions accepted in blocks, per UTC minute, by block time, on two independent nodes (n2 and the public node muon-10.kaspa.blue, side by side). Earlier minutes of the run (from 07:30Z) come from the post-END chain count. File: [pulse-method-minute.csv](pulse-method-minute.csv), with network blocks (blue/red) and our miner per UTC minute.

**Every network count includes TN10 base load of about 56 tx/s** (figure from Kaspa Pulse).

| UTC minute | CEST | n2 accepted tx/s | public node tx/s | diff (tx) | blue blocks | our blocks | our hashrate | note |
|---|---|---:|---:|---:|---:|---:|---|---|
| 2026-10-11T12:07Z | 14:07 | 2907.3 | 2907.3 | 0 | 564 | 178 |  |  |
| 2026-10-11T12:08Z | 14:08 | 3146.5 | 3146.5 | 0 | 610 | 224 | 5.79 Mhash/s |  |
| 2026-10-11T12:09Z | 14:09 | 3258.8 | 3258.8 | 0 | 636 | 193 | 5.95 Mhash/s |  |
| 2026-10-11T12:10Z | 14:10 | 2880.2 | 2880.2 | 0 | 587 | 189 | 5.89 Mhash/s |  |
| 2026-10-11T12:11Z | 14:11 | 2641.5 | 2641.5 | 0 | 644 | 196 | 5.93 Mhash/s |  |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.2 s |
| n2 virtual DAA score | 593,866,502 |
| Miner processes | 1 |
| Lane tips at last sender boots | 172,891 tKAS in 3,600 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 25 GB / 2,528 MB |

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
| 13:44 | 1,430 | 1,361.7 | 1,361.2 | 0.00 | 1.83 | 56.6 | yes | 1,573 |
| 13:59 | 1,573 | 1,459.7 | 1,459.2 | 0.00 | 1.39 | 61.6 | no: box RAM min 1.39 GB < 1.5 | 1,573 |
| 14:14 | 1,573 | 1,425.1 | 1,422.0 | 0.00 | 1.24 | 62.1 | no: box RAM min 1.24 GB < 1.5 | 1,573 |

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 14:07:50 | sender-start | window | S15 mode=pub |
| 14:07:56 | sender-relaunch | window | S16 relaunch 7/200 |
| 14:07:56 | sender-start | window | S16 mode=pub |
| 14:08:08 | sender-relaunch | window | S18 relaunch 6/200 |
| 14:08:08 | sender-start | window | S18 mode=pub |
| 14:08:11 | sender-relaunch | window | S17 relaunch 11/200 |
| 14:08:11 | sender-start | window | S17 mode=pub |
| 14:08:40 | fee-change | - | fee x2 to 1120/1680 by stp 12:05Z (deviation: above GO cap 600); cap 1680, node-quote-skip 400 -> 1680 so our own fee does not make senders sit out; fired 2026- |
| 14:08:40 | deviation | - | fee x2 to 1120/1680 by stp 12:05Z (deviation: above GO cap 600); cap 1680, node-quote-skip 400 -> 1680 so our own fee does not make senders sit out; fired 2026- |
| 14:08:40 | deviation | - | rate held high to END by stp 12:06Z; Build same (deviation: no -5% on unclean/overload windows; only coins running out may lower; floor = current level 1573) |
| 14:14:23 | deviation | - | END extended +1h to 13:30Z by stp 12:13Z, same fees and pace (1120/1680, rate held high, no cuts); miner off, loggers and chain count shift +1 h (count 13:30-15 |
| 14:14:53 | rate-eval | window | RAMP EVAL 13:59-14:14 CEST at 1573 tx/s: sub/acc 1425.1/1422 tx/s, acc/sub 99.79%, rejects 0% (+3 transport), RAM min 1.24 GB, CPU avg 62.1% -> NOT clean (box R |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
