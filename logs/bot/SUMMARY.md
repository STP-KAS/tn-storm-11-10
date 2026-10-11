# Bot side, live summary (TN10 storm, Sun 11 Oct 2026, flat out 09:30-14:30 CEST)

Updated **11:45:06 CEST / 09:45:06 UTC**, about every 10 minutes from G1 to END. Counts only, written on the box by `live-summary.py` (read-only, sends nothing). Column meanings: [go/LOGGING.md](../../go/LOGGING.md). Plan and times: [go/README.md](../../go/README.md).

## Now

| What | Value |
|---|---|
| Step | **window**, until 14:30 CEST / 12:30 UTC |
| Bot target now (ramp) | 1,300 tx/s; last clean level 1,112 |
| Network unique accepted, last complete minute (n2 count) | 3,082.2 tx/s (11:44 CEST) |
| Network best minute so far / mean since START | 3,421.3 (10:44 CEST) / 2,646.3 tx/s (121 valid minutes) |
| Bot submitted, last 10 min | 1,299.5 tx/s (779,700 tx) |
| Bot accepted on n2, last 10 min | 1,300.1 tx/s (780,055 tx) |
| Rejects, last 10 min | 0 consensus/mempool; 0 public-node transport errors |
| Senders writing rows | 18 (processes up: 18) |
| Scheduler / watchdog | running / running |
| Stall relaunches (auto) | 30 |
| HALT | no |

## Changes during the run

| CEST | Change |
|---|---|
| 11:28 | **stp asked both sides to increase effort.** Bot raised 1,011 -> 1,300 tx/s at 11:29 (rate-change). New rate rule for the rest of the run: floor 1,100; +10% after every clean 15 min up to 2,400; a not-clean window lowers by 5% only on real overload (accepted < 95% of submitted or rejects >= 2%), otherwise the rate holds. |
| 11:30-11:34 | Senders 15 -> 18 (staggered, each on 4 of the 5 public nodes; extra senders launch only while box RAM >= 2.5 GB, never under 1.5 GB). Deviation from GO-BOT (max 15 senders for box RAM): 'stp 11:28 increase effort'. |
| 11:28 | Build is increasing effort as well (Build's side, see Build's logs). |

## Public nodes, last 10 min

| Node | Submits ok | Rejects | Errors | Down (s) |
|---|---:|---:|---:|---:|
| boson-10.kaspa.red | 184,098 | 0 | 0 | 0 |
| electron-10.kaspa.blue | 194,919 | 0 | 0 | 0 |
| muon-10.kaspa.blue | 194,913 | 0 | 0 | 0 |
| neutrino-10.kaspa.stream | 21,677 | 0 | 0 | 0 |
| vector-10.kaspa.green | 184,093 | 0 | 0 | 0 |

## n2 (bot's private reader node) and the box

| What | Value |
|---|---|
| n2 synced / UTXO index | True / False |
| n2 sink age (lag) | 0.3 s |
| n2 virtual DAA score | 593,776,547 |
| Miner processes | 1 |
| Lane tips at last sender boots | 176,320 tKAS in 3,600 lanes (read from a public UTXO index; no wallet buffer needed) |
| Disk free / RAM available | 33 GB / 2,784 MB |

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

## Last events

| CEST | Event | Step | Detail |
|---|---|---|---|
| 11:00:01 | rate-change | window | RAMP EVAL 10:45-11:00 CEST at 1223 tx/s: sub/acc 884.1/882.1 tx/s, acc/sub 99.77%, rejects 0% (+2 transport), RAM min 2.21 GB, CPU avg 40.4% -> NOT clean (4 nod |
| 11:15:01 | rate-change | window | RAMP EVAL 11:00-11:15 CEST at 1112 tx/s: sub/acc 0/0 tx/s, acc/sub -%, rejects 0% (+0 transport), RAM min 3.05 GB, CPU avg 42.3% -> NOT clean (accepted -% of su |
| 11:29:52 | rate-change | - | stp 11:28 CEST: increase effort: rate 1011 -> 1300 tx/s; new rule: floor 1,100, +10% per clean 15 min up to 2400, -5% only on real overload (acc < 95% of sub or |
| 11:30:17 | deviation | - | stp 11:28 increase effort: senders 15 -> 16 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:30:17 | sender-start | - | S16 mode=pub |
| 11:30:42 | deviation | - | stp 11:28 increase effort: senders 15 -> 16 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:31:07 | deviation | - | stp 11:28 increase effort: senders 15 -> 16 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:31:58 | deviation | window | stp 11:28 increase effort: senders 16 -> 17 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:31:58 | sender-start | window | S17 mode=pub |
| 11:33:38 | deviation | window | stp 11:28 increase effort: senders 17 -> 18 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:33:38 | sender-start | window | S18 mode=pub |
| 11:44:52 | rate-eval | window | RAMP EVAL 11:29-11:44 CEST at 1300 tx/s: sub/acc 187.3/186.9 tx/s, acc/sub 99.81%, rejects 0% (+0 transport), RAM min 2.44 GB, CPU avg 40.2% -> NOT clean (submi |

How to read: *Now* answers "is the bot sending what the plan says?"; *Public nodes* shows which node rejects or errors; *Rate steps* shows each 15-minute check (clean = at least 99% of submitted accepted, p90 at most 10 s, no node-dead event, submitted at least 90% of target, rejects under 2%, box RAM at least 1.5 GB, CPU under 95%). Label: no-signature hop, anyone-can-spend, not realistic payments. Final per-second files land here after END.
