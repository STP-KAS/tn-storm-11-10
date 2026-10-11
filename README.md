> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md)

# tn-storm-11-10: one target, one window

**History of every storm: [MASTER.md](https://github.com/STP-KAS/tn10-storm-1010/blob/main/history/MASTER.md)** (in tn10-storm-1010).

**Thank you first to Kaspa Pulse ([@gokugalax](https://x.com/gokugalax)).** He counted our chain from outside on his own nodes and shaped these runs with his questions, method and fixes: the node-dead rule and the chain count right after END. All his inputs: [tn10-storm-1010 credits/KASPA-PULSE.md](https://github.com/STP-KAS/tn10-storm-1010/blob/main/credits/KASPA-PULSE.md).

## Start, end, target

| | Brussels (CEST) | UTC |
|---|---|---|
| **START** | **Sun 11 Oct 2026, 09:30** | 07:30 |
| **END** | **14:30** | 12:30 |
| **TARGET** | As many tx/s as possible, sustained for 5 hours | |

Headline: **network unique accepted tx/s**, counted once from chain data: the peak complete minute plus the 5-hour mean and median. Kaspa Testnet-10 only; tKAS has no value.

## What and why

**What.** The same two sides as [tn10-storm-1010](https://github.com/STP-KAS/tn10-storm-1010), with no step timeline: both go flat out at START and stop at END.
- **Bot** (TN10 ops with tn ops2, on the box): **steady** at its max sustainable rate, submitting to the five public TN10 nodes; its private node n2 does reads and its one miner.
- **Build** (Grok Build on stp's desk): its own private, non-archival node (75% of senders) plus about 25% on the public TN10 nodes, and one miner; **monitors the network constantly**, raises or lowers, fixes problems **without stopping**.

**Why.** Last night the two sides ran on different clocks, so they were never at full rate together and the best step median stayed at about 2,645 tx/s, under 3,000 ([WRITE-UP](https://github.com/STP-KAS/tn10-storm-1010/blob/main/logs/WRITE-UP.md), [COMBINED](https://github.com/STP-KAS/tn10-storm-1010/blob/main/logs/COMBINED.md)). Today: one clock, one window, one target.

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
| [tn10-storm-1010](https://github.com/STP-KAS/tn10-storm-1010) | Last night's run, the template for this one |
| [tn10-run-2026-10-11](https://github.com/STP-KAS/tn10-run-2026-10-11) | Superseded draft (12:00 plan) |

## Results

Filled after END and the chain count.

**Status during the run:** 11:28 CEST: stp asked both sides to increase effort. Bot raised 1,011 -> 1,300 tx/s (new floor 1,100, senders 15 -> 18); Build is increasing as well. Details: [logs/bot/CHANGES-DURING-RUN.md](logs/bot/CHANGES-DURING-RUN.md).

| Key number | Value |
|---|---|
| Network unique accepted, peak complete minute (tx/s) | pending |
| Network unique accepted, 5-hour mean / median (tx/s) | pending |
| Bot mean submitted / accepted (tx/s) | pending |
| Build mean submitted / accepted (tx/s) | pending |
| Kaspa Pulse's outside count | pending |

Counts only: no txid, key, seed, IP, host, port or wallet address in this repo.

---

Intentions are good; thought process is questionable. STP remains delusional. Si vis pacem, para bellum.
