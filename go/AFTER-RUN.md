> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# go: after the run (amended by stp 10:51Z; END extended +1 h by stp 12:13Z; HALT by stp 12:32Z) — actual times

GO-BOT is locked, so each amendment is a `deviation` row in [logs/bot/events.csv](../logs/bot/events.csv): "after-run plan amended by stp 10:51Z", "END extended +1h to 13:30Z by stp 12:13Z, same fees and pace", and **"HALT by stp 12:32Z, run ended early vs extended END 13:30Z"**. All times UTC first, Brussels (CEST, UTC+2) second.

| UTC | CEST | What (actual) |
|---|---|---|
| **12:33:01** | 14:33:01 | **HALT = effective END** (the extended END 13:30Z was not reached). GO-BOT HALT order: halt flag, watchdog, scheduler, senders to 0, +10 s hard-kill of every sender and the miner. Nothing restarted. |
| 12:36 | 14:36 | Live loggers stopped after the halt minute 12:33Z; the Kaspa Pulse method mirror stopped and pushed. n2 stayed up. |
| 12:36–12:46 | 14:36–14:46 | **Chain count from n2, before pruning:** 06:30Z to the halt minute (12:34Z exclusive), per UTC minute, in segments. Saved before any node restart. |
| 12:47 | 14:47 | Raw logs + xlsx + SUMMARY.md (with the headline) pushed to [logs/bot/](../logs/bot/SUMMARY.md); leak-scanned. tn ops2 adds `logs/COMBINED.md` and `logs/WRITE-UP.md`. |
| after the count | – | Box nodes restarted with `--uacomment=Grok`, only after the count was saved. |
| – | – | Build's results: pending. |
| later | later | Repo renames, pattern `tn10-storm-<date>` (not `tn10-run-<date>`), after the logs have landed. |

## Headline

**Network unique accepted tx/s, 07:30Z to the halt (12:33Z), counted once** (never summed across sides); see [logs/bot/SUMMARY.md](../logs/bot/SUMMARY.md):

- the **peak complete minute**, and
- the **mean and median** over the window.

## Kaspa Pulse's counter

- Live mirror of Kaspa Pulse's method on the bot side from **10:48Z (12:48 CEST)** to the halt minute 12:33Z: [logs/bot/pulse-method-minute.csv](../logs/bot/pulse-method-minute.csv) (accepted in blocks, two independent nodes, per UTC minute, by block time). Earlier minutes come from the chain count after END.
- **tn-master** (built after today's run) **`METRICS.md`** gets Kaspa Pulse's counter and the note that every network count includes TN10 base load of about 56 tx/s. **Lines quoting Kaspa Pulse are held until he has read them.**

## After-run mining

No numbers, no monitoring, nothing in git.

## Rules (unchanged)

Normal commits only: no force-push, no tags, no releases. Leak-scan before every push. Counts only: no key, seed, txid, IP, host, port, tunnel URL, wallet address or local path.
