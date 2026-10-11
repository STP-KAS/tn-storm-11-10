> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# LOGGING: log everything that can be found

Both sides log the same files, with the same columns, so the bot's minutes, Build's minutes and Kaspa Pulse's minutes line up row by row. Plan: [go/README.md](README.md). Prompts: [GO-BOT](bot/GO-BOT.md), [GO-BUILD](build/GO-BUILD.md). Copied from [tn10-storm-1010 LOGGING](https://github.com/STP-KAS/tn10-storm-1010/blob/main/go/LOGGING.md), with one change: **there are no steps.** The whole run is one window, logged per second and per minute.

## Format, both sides

- CSV, UTF-8, comma, one header row, LF line ends.
- Time in UTC, ISO 8601 with `Z`. Seconds: `2026-10-11T07:30:05Z`. Minutes: `2026-10-11T07:30Z` (the same as Kaspa Pulse's CSV). Reports to stp give CEST first, UTC second.
- `side` is `bot` or `build`. `step` is kept as a column name but has only these values: `PREP` (before START), `window` (START to END, 07:30Z–12:30Z), `COUNT` (after END).
- An empty cell means **not measured**. Never write 0 for not measured.
- Log the clock offset at the start and at the end (`ntp.csv`).
- **Counts only in git.** No txid, key, seed, host IP, port or wallet address. The public node names (`muon-10.kaspa.blue` and so on) are allowed. Per-transaction logs and ids stay on the machine that made them.
- Logging runs from 30 minutes before START (07:00Z) to END, even when a side sends nothing. The COUNT file runs after.

## Files

Every file below exists on both sides with the same name and columns. An empty cell means not measured. The example rows are made up to show the shape; they are not results.

| File | Written | Answers |
|---|---|---|
| [`sec.csv`](#seccsv) | every second | One row per second per side: what the senders did and how the node looked. |
| [`minute.csv`](#minutecsv) | every minute | One row per minute per side; the file to line up with Kaspa Pulse's count. |
| [`public-nodes.csv`](#public-nodescsv) | every minute, per public node | Which public node took, refused or failed. |
| [`rejects.csv`](#rejectscsv) | every second with a reject | Why submits failed. |
| [`miner.csv`](#minercsv) | every 10 s | The side's one miner. |
| [`host.csv`](#hostcsv) | every 10 s | The machine: is it the bottleneck? |
| [`node.csv`](#nodecsv) | every 10 s | The side's own node (bot: n2, the reader; Build: its desk node). |
| [`events.csv`](#eventscsv) | each event | Everything that happened, in order (list below). |
| [`steps.csv`](#stepscsv) | after END | One `window` row for the 5 hours, plus `window-h1` … `window-h5` hour rows. |
| [`gates.csv`](#gatescsv) | each ready read | The ready reads at 09:00 and 09:20 CEST. |
| [`ntp.csv`](#ntpcsv) | start and end | Clock offset, so rows line up. |
| [`chain-count.csv`](#chain-countcsv) | COUNT, per minute, one hour before START to END | The chain count right after END, before pruning (Kaspa Pulse's fix). |
| [`confirm.csv`](#confirmcsv) | each hour of the window | How long a submit took to be accepted, by fee tier. |
| `SUMMARY.md` | bot: live every 15 min during the run, final after END; Build: once after END | Peak minute, 5-hour mean and median, what broke, what was done |

### sec.csv

Written every second. One row per second per side: what the senders did and how the node looked.

| Column | Meaning | Unit |
|---|---|---|
| `utc` | time of the second | ISO UTC |
| `side` | bot or build | text |
| `step` | `PREP`, `window` or `COUNT` | text |
| `target_tx_s` | rate the side was aiming at that second (its current max; 0 while a node-dead hold or sit-out is on) | tx/s |
| `senders_live` | senders that wrote a row this second | count |
| `sent` | submit calls | tx |
| `submit_ok` | submits a node took into its mempool | tx |
| `rejects` | failed submits (any reason, see rejects.csv) | tx |
| `node_accepted` | own transactions seen accepted on the read node's virtual chain | tx |
| `mempool_size` | read node's mempool | tx |
| `sink_lag_s` | age of the read node's sink block | s |
| `synced` | read node synced | true/false |
| `utxoindex` | UTXO index on | true/false |
| `virtual_daa_score` | read node's virtual DAA score | score |
| `sink_blue_score` | sink blue score | score |
| `feerate_quote` | node's normal fee quote | sompi/gram |
| `fee_low` | low fee tier in use | sompi/gram |
| `fee_high` | high fee tier in use | sompi/gram |
| `node_state` | ok, lag, dead or syncing (Words used) | text |

Example:

```
utc,side,step,target_tx_s,senders_live,sent,submit_ok,rejects,node_accepted,mempool_size,sink_lag_s,synced,utxoindex,virtual_daa_score,sink_blue_score,feerate_quote,fee_low,fee_high,node_state
2026-10-11T08:05:07Z,bot,window,250,15,251,251,0,248,1840,0.4,true,true,593160001,412300001,100,400,600,ok
```

### minute.csv

Written every minute. One row per minute per side; the file to line up with Kaspa Pulse's count.

| Column | Meaning | Unit |
|---|---|---|
| `minute_utc` | the minute | ISO UTC minute |
| `side` | bot or build | text |
| `step` | `PREP`, `window`, `window-hN` or `COUNT` | text |
| `target_tx_s` | rate the side was aiming at | tx/s |
| `sent` | submit calls in the minute | tx |
| `submit_ok` | submits taken | tx |
| `rejects` | failed submits | tx |
| `node_accepted` | own transactions accepted | tx |
| `network_unique_accepted` | all accepted transactions in the minute, each id once, all senders (the headline; never summed across sides) | tx |
| `blocks` | blocks on the virtual chain in the minute | blocks |
| `tx_per_block` | network_unique_accepted / blocks | tx/block |
| `our_mined_blocks` | blocks our miner found | blocks |
| `mempool_max` | largest mempool seen | tx |
| `sink_lag_max_s` | largest sink lag | s |
| `synced_all_minute` | synced every read in the minute | true/false |
| `cpu_pct_max` | highest host CPU | % |
| `ram_free_gb_min` | lowest free RAM | GB |
| `disk_free_gb_min` | lowest free disk | GB |
| `node_state` | worst node state in the minute | text |

Example:

```
minute_utc,side,step,target_tx_s,sent,submit_ok,rejects,node_accepted,network_unique_accepted,blocks,tx_per_block,our_mined_blocks,mempool_max,sink_lag_max_s,synced_all_minute,cpu_pct_max,ram_free_gb_min,disk_free_gb_min,node_state
2026-10-11T08:05Z,bot,window,250,15020,15020,0,14890,61200,612,100,3,2100,1.2,true,71,6.4,25,ok
```

### public-nodes.csv

Written every minute, per public node. Which public node took, refused or failed.

| Column | Meaning | Unit |
|---|---|---|
| `minute_utc` | the minute | ISO UTC minute |
| `side` | bot or build | text |
| `node` | public node name, e.g. muon-10.kaspa.blue | text |
| `submit_ok` | submits it took | tx |
| `rejects` | submits it refused | tx |
| `errors` | connection or RPC errors | count |
| `cooled_s` | seconds the node was cooled by the node-dead rule | s |
| `quote_skip` | seconds skipped because its fee quote was above 400 | s |

Example:

```
minute_utc,side,node,submit_ok,rejects,errors,cooled_s,quote_skip
2026-10-11T08:05Z,bot,muon-10.kaspa.blue,3010,0,0,0,0
```

### rejects.csv

Written every second with a reject. Why submits failed.

| Column | Meaning | Unit |
|---|---|---|
| `utc` | the second | ISO UTC |
| `side` | bot or build | text |
| `step` | `PREP`, `window`, `window-hN` or `COUNT` | text |
| `reason` | fee-too-low, mempool-full, orphan, double-spend, mass, rpc-timeout, rpc-closed, other | text |
| `count` | rejects for that reason that second | tx |

Example:

```
utc,side,step,reason,count
2026-10-11T08:05:09Z,bot,window,rpc-closed,4
```

### miner.csv

Written every 10 s. The side's one miner.

| Column | Meaning | Unit |
|---|---|---|
| `utc` | time | ISO UTC |
| `side` | bot or build | text |
| `miner_state` | on or off | text |
| `threads` | miner threads | count |
| `hashrate_hs` | hashrate | H/s |
| `blocks_found` | blocks found so far | blocks |
| `blocks_accepted` | of those, accepted | blocks |
| `blocks_rejected` | of those, rejected | blocks |

Example:

```
utc,side,miner_state,threads,hashrate_hs,blocks_found,blocks_accepted,blocks_rejected
2026-10-11T08:05:10Z,bot,on,1,2100000,14,14,0
```

### host.csv

Written every 10 s. The machine: is it the bottleneck?

| Column | Meaning | Unit |
|---|---|---|
| `utc` | time | ISO UTC |
| `side` | bot or build | text |
| `cpu_pct` | host CPU | % |
| `kaspad_cpu_pct` | node CPU, percent of one core | % |
| `ram_free_gb` | free RAM | GB |
| `kaspad_rss_gb` | node memory | GB |
| `disk_free_gb` | free disk | GB |
| `datadir_gb` | node data folder size | GB |
| `net_in_kbs` | network in | kB/s |
| `net_out_kbs` | network out | kB/s |
| `peers_out` | node outbound peers | count |
| `senders_up` | sender processes up | count |

Example:

```
utc,side,cpu_pct,kaspad_cpu_pct,ram_free_gb,kaspad_rss_gb,disk_free_gb,datadir_gb,net_in_kbs,net_out_kbs,peers_out,senders_up
2026-10-11T08:05:10Z,bot,64,180,6.6,2.3,25,21,900,4200,8,15
```

### node.csv

Written every 10 s. The side's own node (bot: n2, the reader; Build: its desk node).

| Column | Meaning | Unit |
|---|---|---|
| `utc` | time | ISO UTC |
| `side` | bot or build | text |
| `synced` | synced | true/false |
| `utxoindex` | UTXO index on | true/false |
| `sink_lag_s` | sink age | s |
| `virtual_daa_score` | virtual DAA score | score |
| `sink_blue_score` | sink blue score | score |
| `header_count` | headers | count |
| `block_count` | blocks | count |
| `mempool_size` | mempool | tx |
| `kaspad_uptime_s` | node uptime | s |
| `pruning_point_changed` | pruning point moved since the last row | true/false |

Example:

```
utc,side,synced,utxoindex,sink_lag_s,virtual_daa_score,sink_blue_score,header_count,block_count,mempool_size,kaspad_uptime_s,pruning_point_changed
2026-10-11T08:05:10Z,bot,true,true,0.3,593160010,412300010,1430000,1430000,1840,7200,false
```

### events.csv

Written each event. Everything that happened, in order (list below).

| Column | Meaning | Unit |
|---|---|---|
| `utc` | time | ISO UTC |
| `side` | bot or build | text |
| `step` | `PREP`, `window`, `window-hN` or `COUNT` | text |
| `event` | event name (Events table) | text |
| `detail` | what and why, plain words | text |

Example:

```
utc,side,step,event,detail
2026-10-11T08:05:30Z,bot,window,node-dead,boson-10.kaspa.red: 20 errors in a row; cooled 30 s
```

### steps.csv

Written after END: one row `window` for the 5 hours, plus one row per hour (`window-h1` … `window-h5`).

| Column | Meaning | Unit |
|---|---|---|
| `step` | `PREP`, `window`, `window-hN` or `COUNT` | text |
| `side` | bot or build | text |
| `start_utc` | window or hour start | ISO UTC |
| `end_utc` | window or hour end | ISO UTC |
| `target_tx_s` | plan rate for the side | tx/s |
| `mean_sent` | mean submit calls | tx/s |
| `mean_submit_ok` | mean submits taken | tx/s |
| `mean_node_accepted` | mean own accepted | tx/s |
| `rejects` | rejects in the window or hour | tx |
| `zero_seconds` | seconds with 0 sent while the target was above 0 | s |
| `fee_low` | low fee | sompi/gram |
| `fee_high` | high fee | sompi/gram |
| `clean` | yes if at least 99% of submitted were seen accepted, p90 submit-to-accept at most 10 s, and under 5% zero seconds | yes/no |
| `reason` | why not clean | text |

Example:

```
step,side,start_utc,end_utc,target_tx_s,mean_sent,mean_submit_ok,mean_node_accepted,rejects,zero_seconds,fee_low,fee_high,clean,reason
window,bot,2026-10-11T07:30:00Z,2026-10-11T12:30:00Z,900,880.4,880.1,878.0,120,40,400,600,yes,
```

### gates.csv

Written each ready read: R1 at 09:00 CEST (07:00Z), R2 at 09:20 CEST (07:20Z). A failed read is fixed and logged; it never moves START.

| Column | Meaning | Unit |
|---|---|---|
| `utc` | time | ISO UTC |
| `side` | bot or build | text |
| `gate` | R1 or R2 | text |
| `synced` | node synced | true/false |
| `utxoindex` | UTXO index on | true/false |
| `sink_lag_s` | sink lag | s |
| `result` | pass or fail, with what failed | text |

Example:

```
utc,side,gate,synced,utxoindex,sink_lag_s,result
2026-10-11T07:20:00Z,bot,R2,true,true,0.2,pass; node synced
```

### ntp.csv

Written start and end. Clock offset, so rows line up.

| Column | Meaning | Unit |
|---|---|---|
| `utc` | time | ISO UTC |
| `side` | bot or build | text |
| `when` | start or end | text |
| `offset_ms` | clock offset | ms |
| `source` | method | text |

Example:

```
utc,side,when,offset_ms,source
2026-10-10T18:00:02Z,bot,start,-12,HTTP Date
```

### chain-count.csv

Written COUNT, per minute, one hour before START to END. The chain count right after END, before pruning (Kaspa Pulse's fix).

| Column | Meaning | Unit |
|---|---|---|
| `minute_utc` | the minute | ISO UTC minute |
| `side` | who counted | text |
| `network_unique_accepted` | accepted transactions, each id once | tx |
| `accepted_tx_per_s` | the same per second | tx/s |
| `blocks` | chain blocks | blocks |
| `our_mined_blocks` | blocks our miner found | blocks |
| `complete_minute` | every block of the minute read | true/false |

Example:

```
minute_utc,side,network_unique_accepted,accepted_tx_per_s,blocks,our_mined_blocks,complete_minute
2026-10-11T08:05Z,bot,61200,1020.0,612,3,true
```

### confirm.csv

Written each hour of the window. How long a submit took to be accepted, by fee tier.

| Column | Meaning | Unit |
|---|---|---|
| `step` | `PREP`, `window`, `window-hN` or `COUNT` | text |
| `side` | bot or build | text |
| `fee_tier` | bot 400/600, Build 200/300 | sompi/gram |
| `n` | sampled transactions | count |
| `p50_s` | median submit-to-accept | s |
| `p90_s` | 90th percentile | s |
| `max_s` | slowest | s |

Example:

```
step,side,fee_tier,n,p50_s,p90_s,max_s
window-h1,bot,400,300,1.1,2.4,6.0
```

### SUMMARY.md

Plain tables, no columns to decode. The bot's `logs/bot/SUMMARY.md` is a **live summary** during the run: every 10 minutes on the box and pushed every 15 minutes from START to END: current rate, submitted vs accepted, network unique accepted (last complete minute, best minute so far, mean so far), rejects by public node, public-node health, n2 state, coins left, disk and RAM, last events. After END the final summary replaces it.

The bot's node columns are n2 (its reader). Build's node columns are its desk node, plus its 25% public-node share in `public-nodes.csv`.

## Events

One `events.csv` row for each:

| Event | When it is written | Example detail |
|---|---|---|
| `gate` | each ready read | 09:20 ready; node synced |
| `window-start` | START, 09:30 CEST | flat out |
| `window-end` | END, 14:30 CEST | senders stop |
| `rate-change` | a side raises or lowers its senders or rate | Build 2,600 to 3,000: mempool low, lag 1 s |
| `fix` | a problem found and fixed without stopping | sender S4 crashed; restarted |
| `fee-sit-out` | node's normal quote above the side's base fee | quote 450; senders sit out until it drops |
| `fee-rule-blocks-all` | the sit-out rule would stop every sender for over 5 minutes | quote stuck at 450; see detail |
| `sender-start` | a sender starts | S7 up |
| `sender-relaunch` | a sender restarts | S7 relaunch 2 |
| `sender-pause` | a sender pauses | S7 paused: no live node |
| `sender-stop` | a sender stops | S7 stopped at END |
| `node-dead` | node-dead rule cools a node | vector-10.kaspa.green 20 errors |
| `node-back` | a node is live again | vector-10.kaspa.green back |
| `node-quote-skip` | a public node quotes above 400; skipped 1 minute | vector-10.kaspa.green quote 500 |
| `node-fallback` | Build moves senders from its desk node to the public nodes | desk node sink lag 75 s |
| `node-lag` | read node lags (logged, not a stop for the bot) | n2 sink lag 70 s |
| `node-restart` | a node is restarted | n2 restart: DAA still 3 min |
| `miner-on` | miner starts | 1 thread |
| `miner-off` | miner stops | END |
| `coin-refresh` | coins added | added 9909 coins, unclaimed 1,034,706 tKAS |
| `disk-guard` | disk guard acts | free 5 GB: STOP |
| `halt` | stp's halt | stp 11:00 CEST |
| `deviation` | anything not as planned | desk node not synced at START |

## How to read the run in 5 minutes

| Question | Open | Look at |
|---|---|---|
| How fast is the network right now? | `logs/bot/SUMMARY.md` (live) | last complete minute, network unique accepted |
| What is the headline? | `chain-count.csv` | peak complete minute, and mean and median of `accepted_tx_per_s` over 07:30Z–12:30Z; never add the two sides |
| Was a side steady? | `steps.csv` | `window` and `window-h1` … `window-h5` rows |
| Which public node misbehaved? | `public-nodes.csv`, `events.csv` | `errors`, `cooled_s`; `node-dead`, `node-quote-skip` |
| Did Build leave its desk node? | `logs/build/events.csv` | `node-fallback`, `node-back`, `deviation` |
| Was the machine the limit? | `host.csv` | `cpu_pct`, `ram_free_gb`, `disk_free_gb` |
| Was the node healthy? | `node.csv` | `synced`, `sink_lag_s`, DAA score moving |
| Why were submits refused? | `rejects.csv` | `reason`, `count` |
| How fast did transactions confirm? | `confirm.csv` | `p50_s`, `p90_s` by fee tier |
| What happened, in order? | `events.csv` | read top to bottom |

## Words used

- **sent**: the sender called submit. **submit_ok**: the node took it. A failed submit is a reject, never sent-and-ok.
- **node_accepted**: own transactions seen accepted on the virtual chain of the node the side reads.
- **network_unique_accepted**: every accepted transaction in that minute on the virtual chain, each id once, all senders. This is the headline. It is never added across sides; the two sides' counts of the same network are a check on each other.
- **node_state**: `ok`, `lag` (sink lag over 60 s), `dead` (RPC down or not accepting), `syncing`.

## Counting rule (lesson of 10 Oct, 17:21 CEST)

Count `sent`, `submit_ok` and `node_accepted` from the senders' own per-second records. If a sender keeps no per-transaction file, the counts still come from its per-second file. An hour that shows 0 sent while the senders logged sends is a counting bug: fix it and re-count, and log the fix as a `deviation`.

## Node-dead rule (Kaspa Pulse's fix)

- **Per public node:** about 20 connection or RPC errors in a row cools that node for 30 s; the load moves to the sender's other live nodes. No live node: wait, count no attempt.
- **Own node used for submits:** stop when RPC fails for 5 s, `synced` is false, sink lag is over 60 s, or the virtual DAA score is still for 30 s.
- A reader node (the bot's n2) that lags does not stop the senders; its lag is logged.
- While a sender has no live node, its `sent` is 0. The sender starts again only after a fresh read passes, and writes `node-back`.

## Handoff files, Build to the bot

The bot cannot see Build's screen. Build writes these two plain-text files; stp pastes them to the bot. `key: value`, one per line, CEST times.

**`FOR-TN10-OPS-ready-1110.txt`** (by 09:20 CEST):

```
build_ready: yes
written_cest: 09:18
own_node_synced: yes | no
senders: <n>
coins_ready_tkas: <n>
fee_pair: 200/300
miner: on | off
disk_free_gb: <n>
notes: <anything the bot should know>
```

**`FOR-TN10-OPS-result-1110.txt`** (after END, by 16:30 CEST):

```
window: mean_sent, mean_submit_ok, mean_accepted, rejects, peak_minute_tx_s, peak_minute_cest
hours: one line per hour (h1..h5)
network_unique: peak complete minute, 5-hour mean, 5-hour median (from your chain-count.csv)
events: every rate-change, fix, restart, node-fallback, fee-sit-out, deviation (CEST)
```

## After the run

1. COUNT, within two hours of END (14:30–16:30 CEST, 12:30Z–14:30Z): `chain-count.csv` from the own node, before pruning.
2. `steps.csv` and `SUMMARY.md`.
3. Copy the files to `logs/bot/` or `logs/build/` in this repo. Keep raw per-transaction logs and ids local.
4. This repo is public from the start: counts only, leak-scan before every push.
