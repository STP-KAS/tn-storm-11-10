> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md)
>
> **Part of [tn-master](https://github.com/STP-KAS/tn-master)**, the map of every TN10 storm. Renamed on 11 Oct 2026 from `tn-storm-11-10`; old links redirect here.
>
> ← previous storm: [tn10-storm-2026-10-10-public-nodes](https://github.com/STP-KAS/tn10-storm-2026-10-10-public-nodes) | latest storm →

# tn10-storm-2026-10-11 · Sun 11 Oct, 07:30-12:33 UTC (09:30-14:33 CEST): one target, one window

**History of every storm: [MASTER.md](https://github.com/STP-KAS/tn-master/blob/main/history/MASTER.md)** (in tn-master).

**Thank you first to Kaspa Pulse ([@gokugalax](https://x.com/gokugalax), [kaspapulse.com](https://kaspapulse.com)).** He counted our chain from outside on his own nodes and shaped these runs with his questions, method and fixes: the node-dead rule and the chain count right after END. All his inputs: [tn10-storm-2026-10-10 credits/KASPA-PULSE.md](https://github.com/STP-KAS/tn10-storm-2026-10-10/blob/main/credits/KASPA-PULSE.md).

## Start, end, target

| | Brussels (CEST) | UTC |
|---|---|---|
| **START** | **Sun 11 Oct 2026, 09:30** | 07:30 |
| **END** | **14:30** (extended to 15:30; **halted by stp at 14:33:01**) | 12:30 (13:30; halt 12:33:01) |
| **TARGET** | As many tx/s as possible, sustained for 5 hours | |

Headline: **network unique accepted tx/s**, counted once from chain data: the peak complete minute plus the 5-hour mean and median. Kaspa Testnet-10 only; tKAS has no value.

## What and why

**What.** The same two sides as [tn10-storm-2026-10-10](https://github.com/STP-KAS/tn10-storm-2026-10-10), with no step timeline: both go flat out at START and stop at END.
- **Bot** (TN10 ops with tn ops2, on the box): **steady** at its max sustainable rate, submitting to the five public TN10 nodes; its private node n2 does reads and its one miner.
- **Build** (Grok Build on stp's desk): its own private, non-archival node (75% of senders) plus about 25% on the public TN10 nodes, and one miner; **monitors the network constantly**, raises or lowers, fixes problems **without stopping**.

**Why.** Last night the two sides ran on different clocks, so they were never at full rate together and the best step median stayed at about 2,642 tx/s (corrected 11 Oct), under 3,000 ([WRITE-UP](https://github.com/STP-KAS/tn10-storm-2026-10-10/blob/main/logs/WRITE-UP.md), [COMBINED](https://github.com/STP-KAS/tn10-storm-2026-10-10/blob/main/logs/COMBINED.md)). Today: one clock, one window, one target.

## GO

Once stp sends a GO it is locked; sending means **be ready at 09:30 CEST**. Bot: [GO-BOT.md](go/bot/GO-BOT.md). Build: [GO-BUILD.md](go/build/GO-BUILD.md). After END: [go/AFTER-RUN.md](go/AFTER-RUN.md) (amended by stp 10:51Z / 12:51 CEST).

## Map

| Folder or file | What is in it |
|---|---|
| [DISCLAIMER.md](DISCLAIMER.md) | Experimental; what this repo is and is not |
| [go/](go/README.md) | Target, start and end (CEST and UTC), rules, lock rule, stp's to-do |
| [go/bot/GO-BOT.md](go/bot/GO-BOT.md) | The bot's prompt |
| [go/build/GO-BUILD.md](go/build/GO-BUILD.md) | Build's prompt |
| [go/LOGGING.md](go/LOGGING.md) | Every log file and column; one `window`, per second and per minute |
| [go/AFTER-RUN.md](go/AFTER-RUN.md) | After END (UTC first): chain count, node restart, headline, pushes, Kaspa Pulse's counter (amended by stp 10:51Z) |
| [logs/](logs/README.md) | Results after END: [bot/](logs/bot/README.md), [build/](logs/build/README.md) |
| [history/](history/README.md) | Links to MASTER and earlier runs |
| [tn10-storm-2026-10-10](https://github.com/STP-KAS/tn10-storm-2026-10-10) | Last night's run, the template for this one |
| [tn10-storm-2026-10-11-draft](https://github.com/STP-KAS/tn10-storm-2026-10-11-draft) | Superseded draft (12:00 plan) |

## Results

**Halted by stp at 14:33:01 CEST (12:33:01Z)**, before the extended END of 15:30 CEST. Stopped early by stp: taking a break, other things on the agenda. (bot and Build) Combined: [`logs/COMBINED.md`](logs/COMBINED.md) · write-up: [`logs/WRITE-UP.md`](logs/WRITE-UP.md) · bot: [`logs/bot/SUMMARY.md`](logs/bot/SUMMARY.md), workbook [`logs/bot/run-2026-10-11.xlsx`](logs/bot/run-2026-10-11.xlsx) · changes during the run: [`logs/bot/CHANGES-DURING-RUN.md`](logs/bot/CHANGES-DURING-RUN.md).

Window **07:30Z to the halt (303 minutes)**. Network counts are counted once from chain data and include about **56 tx/s of TN10 base load**.

| Key number | Value | Detail |
|---|---|---|
| Network unique accepted, peak complete minute (tx/s) | **3,583.1** (11:28Z / 13:28 CEST) | [logs/COMBINED.md](logs/COMBINED.md) |
| Network unique accepted, median / mean (tx/s) | **3,107.1** (171 complete minutes) / **2,833.1** | [logs/COMBINED.md](logs/COMBINED.md) |
| Bot mean submit-OK / accepted on n2 (tx/s, all 303 minutes) | 1,101.5 / 1,100.6 (steps.csv logged-second mean 1,212.97 / 1,211.87) | [logs/COMBINED.md](logs/COMBINED.md#bot-vs-build) |
| Build mean submitted / accepted (tx/s) | pending | [logs/build/](logs/build/README.md) |
| Kaspa Pulse's outside count (accepted in blocks, two independent nodes, per UTC minute, by block time; every minute confirmed by both nodes) | 07:30-12:30Z, 300 full minutes: mean **2,844**, median **3,055**, best minute **3,646** (11:28Z); **51.2 million** tx accepted; 163 minutes above 3,000 tx/s. Includes ~56 tx/s base load. | [credits/kaspa-pulse/2026-10-11/](credits/kaspa-pulse/2026-10-11/README.md) |

**Dips have two shapes:** a big miner dropping out (block rate and throughput fall together) vs senders slowing (block rate holds, tx per block falls). Our evidence: [logs/COMBINED.md, Dips](logs/COMBINED.md#dips-two-shapes-from-our-logs). How each per-minute CSV was counted: [logs/README.md, Method per file](logs/README.md#method-per-file).

Submit-OK (taken into a node's mempool) is not the same as accepted on chain. Kaspa Testnet-10 only; tKAS has no value.

Counts only: no txid, key, seed, IP, host, port or wallet address in this repo.

---

Intentions are good; thought process is questionable. STP remains delusional. Si vis pacem, para bellum.
