> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md)

# logs/bot

Pushed by **TN10 ops** after END (raw logs: same files and columns as [tn10-storm-1010 logs/bot](https://github.com/STP-KAS/tn10-storm-1010/tree/main/logs/bot), plus an xlsx). tn ops2 keeps `SUMMARY.md` live every 15 minutes during the run and writes the count. Submits: the five public TN10 nodes. Reads and miner: n2.

| File | Every | What |
|---|---|---|
| `sec.csv` | second | What the senders did and how the node looked |
| `minute.csv` | minute | Per minute, incl. network unique accepted; line up with Kaspa Pulse |
| `public-nodes.csv` | minute, per public node | Which public node took, refused or failed |
| `rejects.csv` | second with a reject | Why submits failed |
| `miner.csv` | 10 s | The one miner |
| `host.csv` | 10 s | The machine: CPU, RAM, disk |
| `node.csv` | 10 s | The side's own node |
| [`CHANGES-DURING-RUN.md`](CHANGES-DURING-RUN.md) | each change | Changes after the GO lock (11:28 CEST: stp asked both sides to increase effort) |
| `events.csv` | each event | Everything in order: rate changes, fixes, restarts, deviations |
| `gates.csv` | R1, R2 | Ready reads |
| `ntp.csv` | start and end | Clock offset |
| `chain-count.csv` | per minute, after END | The count before pruning (Kaspa Pulse's fix). `headline_strict = yes` = the 171 minutes behind the peak and median |
| `confirm.csv`, `order.csv` | each hour | Submit-to-accept times and ordering. **Header only for 11 Oct:** the senders logged no per-transaction times this run. |
| `chain-recount-1m.csv` | per recount span, after END | Raw chain recount from n2 (`span_min` > 1 = lumped minutes) |
| `steps.csv` | after END | `window` plus `window-h1` … `window-h5` |
| `SUMMARY.md` | after END; live every 15 min during the run | Peak minute, 5-hour mean and median, what broke, what was done |

Columns: [go/LOGGING.md](../../go/LOGGING.md). Counts only; per-transaction logs and ids stay local.
