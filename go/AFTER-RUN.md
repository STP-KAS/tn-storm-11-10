> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# go: after the run (amended by stp 10:51Z, 12:51 CEST)

GO-BOT is locked, so this amendment is logged as a `deviation` row in [logs/bot/events.csv](../logs/bot/README.md) ("after-run plan amended by stp 10:51Z"). All times UTC first, Brussels (CEST, UTC+2) second.

| UTC | CEST | What |
|---|---|---|
| **12:30** | 14:30 | **END.** Senders stop, the bot's one miner off, loggers stop. |
| 12:30–14:30 | 14:30–16:30 | **Chain count from n2, before pruning:** 06:30–12:30Z, per UTC minute. |
| after the count | – | The box nodes are restarted (with `--uacomment=Grok`) **only after the count is done and saved**. |
| ~14:00 | ~16:00 | **Build's result file wanted**, so the 15:30Z push is not held up. |
| **by 15:30** | by 17:30 | Raw logs + xlsx pushed to [logs/bot/](../logs/bot/README.md); tn ops2 adds `logs/COMBINED.md` and `logs/WRITE-UP.md`. |
| after 15:30 | after 17:30 | Repo renames, pattern `tn10-storm-<date>` (not `tn10-run-<date>`). |

## Headline

**Network unique accepted tx/s for 07:30–12:30Z, counted once** (never summed across sides):

- the **peak full minute**, and
- the **5-hour mean and median**.

## Kaspa Pulse's counter

- Live mirror of Kaspa Pulse's method on the bot side since **10:48Z (12:48 CEST)**: [logs/bot/pulse-method-minute.csv](../logs/bot/pulse-method-minute.csv) (accepted in blocks, two independent nodes, per UTC minute, by block time). Earlier minutes come from the chain count after END.
- **tn-master** (built after today's run) **`METRICS.md`** gets Kaspa Pulse's counter and the note that every network count includes TN10 base load of about 56 tx/s. **Lines quoting Kaspa Pulse are held until he has read them.**

## After-run mining

No numbers, no monitoring, nothing in git.

## Rules (unchanged)

Normal commits only: no force-push, no tags, no releases. Leak-scan before every push. Counts only: no key, seed, txid, IP, host, port, tunnel URL, wallet address or local path.
