> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md)

# GO-BOT: TN10 storm, Sunday 11 Oct 2026, 09:30 to 14:30 CEST

You are the bot side: **TN10 ops** (operator: n2, the miner, the scheduler and the senders) with **tn ops2** (Grok Bot: logging, the chain count, the write-up). Build's file: [GO-BUILD.md](../build/GO-BUILD.md). Shared rules: [go/README.md](../README.md).

**This prompt is locked once stp sends it.** Sending is not the start. It means: get ready now, be sending at **09:30 CEST**, and run to 14:30 CEST without stp watching. A change after the lock goes in `events.csv` as a `deviation`.

## GO

When this file lands in your chat, that is the GO. No questions. Get ready at once; problems are fixed and logged, never turned into a question.

| What | Brussels (CEST) | UTC |
|---|---|---|
| R1: read n2, coins, disk, RAM, each public node; logging starts | 09:00 | 07:00 |
| R2: senders connected and idle, miner on | 09:20 | 07:20 |
| **START: flat out** | **09:30** | **07:30** |
| **END: senders stop, miner off** | **14:30** | **12:30** |
| COUNT from n2, before pruning | 14:30–16:30 | 12:30–14:30 |
| Logs pushed to `logs/bot/` | by 17:30 | by 15:30 |

No steps, no ramp. **Target: as many tx/s as possible, network unique accepted, sustained.** START does not move. Do not wait for Build: both sides start at 09:30 on this one clock. (Last night the two sides ran on different clocks and the combined peak never reached 3,000: [WRITE-UP](https://github.com/STP-KAS/tn10-storm-2026-10-10/blob/main/logs/WRITE-UP.md).)

Thank you, Kaspa Pulse ([@gokugalax](https://x.com/gokugalax), [kaspapulse.com](https://kaspapulse.com)). The node-dead rule and the chain count right after END are his fixes.

## Your job: steady

Run the bot's **maximum sustainable rate** and hold it flat for 5 hours. Build is the side that adapts; you are the steady base.

- **Claim (measured on TN10):** last night the bot's clean max was about **919 tx/s** (MAX) and about **880 tx/s** in the hold ([bot steps.csv](https://github.com/STP-KAS/tn10-storm-2026-10-10/blob/main/logs/bot/steps.csv)). Start there.
- Raise only if a full 15 minutes ran clean (≥99% of submitted seen accepted, p90 submit-to-accept ≤10 s, no node-dead events). Lower if not. Log every change as `rate-change` with the reason.
- **At most 15 senders** (box RAM limit), one scheduler, locked so a second copy cannot start. Launches staggered a few seconds apart; at most one relaunch per sender per minute; no launch while free box RAM is under 1.5 GB.
- Shape: the no-signature hop (anyone-can-spend P2SH lanes). Label it in every report: "no-signature hop, anyone-can-spend, not realistic payments".

## Where you send

- **Submit to the five public TN10 community nodes only**, as last night (names in [tn10-storm-2026-10-10 GO-BOT-RUN](https://github.com/STP-KAS/tn10-storm-2026-10-10/blob/main/go/bot-run/GO-BOT-RUN.md#where-you-send)). **Never submit to n2.** Random spread: each sender picks four of the five at launch.
- **Node-dead rule, per public node:** about 20 connection or RPC errors in a row cools that node for 30 s; its lanes move to the sender's other live nodes. No live node: the sender waits and counts no attempt. A failed submit is a reject, never "sent". Log `node-dead` / `node-back`.
- **Per-node fee check:** each minute; a node quoting above 400 is skipped for that minute (`node-quote-skip`).
- **Be a fair guest.** A node that keeps rejecting or dropping for more than 10 minutes is dropped for the hour and logged.

## n2: reads and the miner

- n2 on the box: kaspad 2.1.0, testnet-10, pruned (not archival), **no UTXO index** (removed 10 Oct 21:58 CEST for disk), RPC and peers on loopback only, no tunnel. At 08:35 CEST: synced, about 35 GB disk free, about 6.3 GB RAM free.
- n2 is for health reads, the fee quote, watching your own transactions get accepted, the chain count, and **the one miner**. n2 lagging does not zero the senders; it is logged.
- **Disk:** n2's disk grows in bursts under load (**Claim (measured on TN10):** up to about 16 GB in 30 minutes last night). The guard stops n2 below 10 GB free. Watch it; prune your own logs, never the chain.
- **Freeze:** n2 froze at its tip several times. If its virtual DAA score is still for over 3 minutes and its sink lag is over 3 minutes, restart it on the same flags (at most once per 20 minutes), log `node-restart`. Never switch on archival.

## Fees

Half the lanes at **400**, half at **600** sompi/gram. Floor 100, cap 600. Senders sit out while the normal quote (n2, or a public node if n2 cannot answer) is above 400 (`fee-sit-out`). If that would stop every sender for over 5 minutes, log `fee-rule-blocks-all` and keep sending at 400/600.

## Coins

- Need: about 900 tx/s × 18,000 s ≈ 16 million transactions; at about 643 grams and 400 to 600 sompi/gram, about 52,000 tKAS of fees. Hold at least 1.5 times that before 09:00 CEST.
- Through the claim ledger only. Never list a whole address in one call. n2 has no UTXO index, so the refresh must not depend on it. Check every 30 minutes. If the buffer cannot be kept, lower the rate and log a `deviation`; do not stop.
- The parked trump2028 mints and their claimed coins are not part of this run.

## Your miner

Exactly one box-CPU kaspa-miner, one thread, on n2's loopback gRPC, paying the bot's own address (kept out of git). On at R2 if n2 is synced. Off at END.

## Build

Build starts at 09:30 on the same clock. stp passes Build's `FOR-TN10-OPS-ready-1110.txt` (about 09:20). The bot does **not** wait for it; log `deviation` if it has not come by 09:30. Never change the bot's rate to cover Build.

## Log everything (tn ops2)

From R1 to END, as in [LOGGING.md](../LOGGING.md), `step` = `window`: `sec.csv`, `minute.csv` (with network unique accepted, blocks, our mined blocks), `public-nodes.csv`, `rejects.csv`, `miner.csv`, `host.csv`, `node.csv`, `events.csv`, `gates.csv`, `ntp.csv`; after END `chain-count.csv`, `confirm.csv`, `steps.csv` (`window` and `window-h1` … `window-h5`) and `SUMMARY.md`. **Live `logs/bot/SUMMARY.md` every 15 minutes** from START to END: current rate, last complete network minute, best minute so far, mean so far, last events.

## Halt

Only stp halts. Then: halt flag, **stop the watchdog first**, then the scheduler, senders to 0, wait 10 s, hard-kill every bot sender and the miner by process name, check nothing restarts. n2 and read-only loggers stay up.

## After END

1. **END 14:30 CEST:** senders stop, miner off, live loggers stop.
2. **COUNT (14:30–16:30 CEST, before pruning):** `chain-count.csv` per minute from 08:30 to 14:30 CEST, from n2.
3. Headline: **peak complete minute** and **5-hour mean and median** of network unique accepted tx/s, counted once. Read Build's result file when stp passes it.
4. **By 17:30 CEST:** TN10 ops pushes the raw logs (same files and columns as tn10-storm-2026-10-10 `logs/bot/`, plus an xlsx) to `logs/bot/` in **STP-KAS/tn10-storm-2026-10-11**, as STP-KAS. tn ops2 adds `logs/COMBINED.md` and `logs/WRITE-UP.md`. Counts only, leak-scanned. No force-push, no tags, no releases.

## Never

No IP, host, port, key, seed, txid, wallet address or local path in the repo. No tunnel. No second miner. No archival. No fee above 600 or below 100. No submits to n2 or to Build's node. No firing at a dead node. Do not ping Kaspa Pulse; stp does that.
