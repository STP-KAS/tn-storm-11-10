> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# Combined results: TN10 storm, Sun 11 Oct 2026

Back to [logs/](README.md) · story: [WRITE-UP.md](WRITE-UP.md) · bot detail: [bot/SUMMARY.md](bot/SUMMARY.md) · changes: [bot/CHANGES-DURING-RUN.md](bot/CHANGES-DURING-RUN.md) · history: [MASTER.md](https://github.com/STP-KAS/tn10-storm-1010/blob/main/history/MASTER.md)

**Clock.** One clock for both sides. START **07:30Z** (09:30 CEST). Planned END 12:30Z (14:30 CEST), extended by stp to 13:30Z (15:30 CEST), then **halted by stp at 12:33:01Z (14:33:01 CEST)**. Stopped early by stp: taking a break, other things on the agenda. That applies to both the bot and Build. Times are UTC first, CEST (UTC+2) in brackets.

**Target.** One target: as many tx/s as possible, network unique accepted, sustained. No steps.

**Sources.** Bot: [bot/chain-count.csv](bot/chain-count.csv), [bot/minute.csv](bot/minute.csv), [bot/steps.csv](bot/steps.csv), [bot/public-nodes.csv](bot/public-nodes.csv), [bot/events.csv](bot/events.csv), [bot/pulse-method-minute.csv](bot/pulse-method-minute.csv), [bot/run-2026-10-11.xlsx](bot/run-2026-10-11.xlsx). Build: **pending**.

## Headline: network unique accepted tx/s, 07:30Z to the halt

Counted once from chain data on the bot's node n2 after the halt, before pruning. Never a sum of the two sides. **Every network count includes TN10 base load of about 56 tx/s** (n2 read 54 to 55 tx/s before START).

| Measure, 07:30-12:33Z (303 minutes) | tx/s | Label |
|---|---:|---|
| Peak complete minute (11:28Z, 13:28 CEST) | **3,583.1** | Claim (measured on TN10) |
| Median of complete minutes (n=171) | **3,107.1** | Claim (measured on TN10) |
| Mean, all accepted tx / 303 minutes (51,506,370 tx) | **2,833.1** | Claim (measured on TN10) |
| Complete minutes at or above 3,000 tx/s | 110 of 171 | Claim (measured on TN10) |

- **Complete minute** = a chain-count row that covers exactly one minute. 47 rows lump several minutes together (a boundary block missing or not on the final chain), including **n2's freeze 11:08-11:25Z** (13:08-13:25 CEST). They count in the mean, not in the peak or median. Six minutes where the count had a gap come from the live chain logger.
- The peak minute matches the live per-minute logger exactly (3,583.1).
- **Data gap:** the `complete_minute` flag in [bot/chain-count.csv](bot/chain-count.csv) uses a looser rule than the headline (it falls back to the live logger and marks 225 minutes in the window `yes`). The 171-minute set above comes from the stricter recount on the box, which is not in this repo. The peak, median and mean were re-checked from that recount for this page and match [bot/SUMMARY.md](bot/SUMMARY.md).

## Per hour (network median of complete minutes; bot means from minute.csv)

| Hour (UTC) | CEST | Network median (n) | Bot submit-OK | Bot accepted on n2 | Bot rejects |
|---|---|---:|---:|---:|---:|
| 07:30-08:30 | 09:30-10:30 | 2,649.3 (36) | 893.0 | 892.0 | 3 |
| 08:30-09:30 | 10:30-11:30 | 2,960.3 (36) | 1,082.1 | 1,081.8 | 12 |
| 09:30-10:30 | 11:30-12:30 | 3,146.8 (31) | 1,230.3 | 1,227.5 | 33 |
| 10:30-11:30 | 12:30-13:30 | 3,306.8 (22) | 1,340.1 | 1,339.2 | 701 |
| 11:30-12:30 | 13:30-14:30 | 3,222.7 (45) | 1,423.0 | 1,422.0 | 15 |
| 12:30-12:33 | 14:30-14:33 | 1,751.6 (1) | 1,625.8 | 1,626.9 | 0 |

Bot columns are means over the minutes that have rows (the last row uses the three full minutes 12:30-12:32Z). minute.csv has no rows for 07:39-07:42Z, 08:46-08:48Z, 09:57-09:59Z and 11:09-11:22Z (the last during n2's freeze).

## Bot vs Build

**Submit-OK is not accepted.** Submit-OK = a node took the transaction into its mempool. Accepted = seen accepted on the chain. The network headline above is neither side's submit count.

| | Bot | Build |
|---|---|---|
| Sent through | the 5 public TN10 nodes only; n2 for the miner and reads | about 75% own desk node, 25% public nodes (plan) |
| Window submit-OK (tx) | 20,026,133 | pending |
| Mean submit-OK, all 303 minutes | **1,101.5 tx/s** | pending |
| Mean accepted on n2, all 303 minutes | **1,100.6 tx/s** | pending |
| steps.csv `window` mean submit-OK / accepted | 1,212.97 / 1,211.87 tx/s | pending |
| Rejects (minute.csv) | 764, of which 701 in 10:30-11:30Z | pending |
| Fees (sompi/gram) | 400/600, then 560/840 from 10:31Z, then 1,120/1,680 from 12:08:40Z | pending |
| Stop | 12:33:01Z, stopped early by stp: taking a break, other things on the agenda | Stopped early by stp: taking a break, other things on the agenda. Logs pending |

- The two bot means differ because steps.csv averages the seconds that were logged, while 1,101.5 spreads the window total over every minute. **Not sure / open for debate** which one the next run should headline; this page uses the total.
- Bot share of the network total: about 20.0 of 51.5 million accepted tx (about 39%). Base load is about 1.0 million. The rest, about 30.5 million (about 1,680 tx/s), is Build plus any other TN10 traffic; Build's own share is **pending**. **Not sure / open for debate.**

### Public nodes (bot, 07:30-12:33Z)

| Node | Submit-OK share | Errors | Rejects |
|---|---:|---:|---:|
| electron-10.kaspa.blue | 23.8% | 4 | 5 |
| muon-10.kaspa.blue | 23.1% | 655 | 12 |
| boson-10.kaspa.red | 19.6% | 4 | 63 |
| neutrino-10.kaspa.stream | 18.3% | 5 | 9 |
| vector-10.kaspa.green | 15.2% | 2 | 5 |

## Our block-time counter (from 10:49Z)

A second live counter on the bot side, [bot/pulse-method-minute.csv](bot/pulse-method-minute.csv): transactions accepted in blocks, per UTC minute **by the accepting chain block's timestamp**, on two nodes (n2 and the public node muon-10.kaspa.blue), with miner columns. It started at 10:48Z (12:48 CEST); first full minute 10:49Z. Earlier minutes come only from the chain count.

| 10:49-12:32Z | tx/s | Label |
|---|---:|---|
| Highest minute (11:28Z, both nodes) | 3,645.9 | Claim (measured on TN10) |
| Median, public node (101 minutes) | 3,209.4 | Claim (measured on TN10) |
| Median, n2 (87 minutes; n2 missing during its freeze) | 3,225.3 | Claim (measured on TN10) |
| Minutes where the two nodes disagree | 0 | Claim (measured on TN10) |

Its minutes differ a little from the chain count because it buckets by block time, not by the minute of the chain-count row. It also includes the base load.

## Data gaps

- Build: **pending** (no files in [build/](build/README.md) yet).
- Bot minute.csv has no rows for 24 minutes (07:39-07:42Z, 08:46-08:48Z, 09:57-09:59Z, 11:09-11:22Z); the window totals leave those minutes at 0.
- `rejects.csv`, `confirm.csv` and `order.csv` have no rows, though minute.csv counts 764 rejects; reasons are not in the repo.
- steps.csv shows fee 400/600 for every hour; the fee changes are in events.csv and [CHANGES-DURING-RUN.md](bot/CHANGES-DURING-RUN.md).
- The bot workbook was regenerated so its events sheet carries the stop reason, like events.csv.

<details>
<summary><b>Certainty labels</b></summary>

| Label | Meaning |
|---|---|
| **Claim (measured on TN10)** | Seen on Testnet-10 by us, with a number and a source. |
| **Not sure / open for debate** | A reading that fits, but other readings fit too. |
| **Needs more testing** | One run is not enough to say. |

</details>

Counts only: no txid, key, seed, host IP, port or wallet address in this repo. The public TN10 node names are the community resolver nodes, not ours. Bot senders send no-signature hops (anyone-can-spend), not realistic payments. Kaspa Testnet-10 only; tKAS has no value.
