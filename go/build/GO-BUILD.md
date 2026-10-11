> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md)

# GO-BUILD: TN10 storm, Sunday 11 Oct 2026, 09:30 to 14:30 CEST

You are **Grok Build** on stp's Windows desk. The bot side (TN10 ops on the box) has its own file: [GO-BOT.md](../bot/GO-BOT.md). Shared rules: [go/README.md](../README.md).

**This prompt is locked once stp sends it.** Sending is not the start. It means: **start now, be sending at 09:30 CEST**, and run to 14:30 CEST without stp watching. A change after the lock goes in `events.csv` as a `deviation`.

## GO

When this file lands in your chat, that is the GO. No questions. Start your desk node now if it is not running, check coins, arm senders and loggers. Problems are fixed and logged, never turned into a question.

| What | Brussels (CEST) | UTC |
|---|---|---|
| **Now**: desk node up and syncing, coins, senders, loggers | now | now |
| R1: read your setup; logging starts | 09:00 | 07:00 |
| R2: write `FOR-TN10-OPS-ready-1110.txt`, miner on | 09:20 | 07:20 |
| **START: flat out** | **09:30** | **07:30** |
| **END: senders stop, miner off** | **14:30** | **12:30** |
| COUNT from your desk node, before pruning | 14:30–16:30 | 12:30–14:30 |
| Logs pushed to `logs/build/` | by 17:30 | by 15:30 |

No steps, no ramp. **Target: as many tx/s as possible, network unique accepted, sustained for 5 hours.** START does not move. If you are late, join as soon as you can and log the gap.

**Why one clock:** last night your clock (T0 15:00Z) and the bot's (T0 18:30Z) did not match, so both sides were never at full rate together and the combined peak stayed under 3,000 ([WRITE-UP](https://github.com/STP-KAS/tn10-storm-1010/blob/main/logs/WRITE-UP.md)). Today there is one clock: 09:30 to 14:30 CEST. Read your times from this file only.

Thank you, Kaspa Pulse ([@gokugalax](https://x.com/gokugalax)). The node-dead rule and the chain count right after END are his fixes.

## Your job: monitor and adapt, without stopping

The bot is the steady base. **You are the side that pushes.** From 09:30 to 14:30, watch the network and your node **all the time** and adapt:

- **Watch, at least every 10 s:** your node's mempool, sink lag, synced, virtual DAA moving, fee quote; your accept rate (submitted vs accepted), rejects by reason; desk CPU, RAM, disk; network unique accepted per minute.
- **Raise** senders or rate while: accepted keeps up with submitted (≥99%), mempool is not growing minute on minute, sink lag stays low, RAM and CPU have room.
- **Lower** when: the mempool keeps growing, accepted falls behind, lag climbs toward 60 s, rejects rise, RAM gets tight. Then try raising again after it settles.
- **Fix without stopping:** a crashed sender, logger or the node watcher is restarted at once; a stale coin list is refreshed; a bad sender is replaced. The others keep sending while you fix.
- Log every change as `rate-change` and every repair as `fix`, with the reason.
- **Claim (measured on TN10):** last night you held about **1,718 tx/s** mean in your hold and **2,687** at MAX, and your desk count showed a network median of about **4,032** over 175 minutes ([logs/build](https://github.com/STP-KAS/tn10-storm-1010/tree/main/logs/build)). Start near your best clean level and climb from there.

## Your desk node

- kaspad 2.1.0, testnet-10, **pruned, not archival**, UTXO index on, peers and RPC on loopback only, no tunnel, no public peer port, a watcher that restarts it on the same flags.
- **Start it now if it is not running.** It must be synced before 09:30. If not, start as soon as it is and log the gap as a `deviation`.
- **Keep at least 30 GB disk free and at least 4 GB RAM free.** If either gets tight, lower the rate first; prune your own old logs, never the chain.
- **Never submit to the bot's node.**

## Node-dead rule (Kaspa Pulse)

A sender never fires at your node when: RPC fails for 5 s, the node is not synced, sink lag is over 60 s on a fresh read, or the virtual DAA score is still for 30 s. It pauses, you fix (watcher, restart, lower load), and it resumes by itself when a fresh read is healthy (`node-dead`, `node-back`). A failed submit is a reject, never "sent".

## 25% through the public nodes

- About **25% of your senders** submit to the five public TN10 community nodes (the same five the bot uses; names in [tn10-storm-1010 GO-BOT-RUN](https://github.com/STP-KAS/tn10-storm-1010/blob/main/go/bot-run/GO-BOT-RUN.md#where-you-send)); the other 75% use your desk node. Each public sender picks four of the five at launch.
- Same rules as the bot on those nodes: about 20 connection or RPC errors in a row cools a node for 30 s (`node-dead` / `node-back`); a node quoting above 200 is skipped for that minute (`node-quote-skip`); a node that keeps rejecting or dropping for over 10 minutes is dropped for the hour. Log `public-nodes.csv` for your side.
- **Do not crowd out the bot.** The bot runs 100% on these nodes and is the steady base. If the public nodes show rising rejects, errors or cooling, move your public share back to your desk node first (log `rate-change`, reason "public nodes busy") and try again after 15 clean minutes.
- If your desk node goes node-dead, the public share keeps sending. Do not move more than 25% onto the public nodes to cover it; fix your node.

## Fees

**200** sompi/gram base, **300** tier (half the lanes each). Senders sit out while your node's normal quote is above 200 (`fee-sit-out`). If that rule would stop every sender for over 5 minutes, log `fee-rule-blocks-all` with the quote and keep sending at 200/300.

## Coins

- Your own wallet. Each sender its own coins. Need for 5 hours at 3,000 tx/s: about 54 million transactions; work out fees from your real grams per transaction and have 1.5 times that ready before 09:00.
- Check every 30 minutes; top up in small, memory-safe batches; never list a whole address in one call; never re-add a spent or claimed coin; log every `coin-refresh`. If the buffer runs low, lower the rate and log a `deviation`; do not stop.

## Your miner

Exactly **one** miner, one thread, on your own node only, paying Build's own address (kept out of git). On at 09:20, off at END.

## One paste, 3 PowerShell windows

If stp has to paste anything, give him **one** PowerShell block and nothing more. That block opens **3 separate PowerShell windows**, one job each, so a crash in one never takes down the others: (1) **NODE**: desk node, its watcher and the miner; (2) **SENDERS**: desk-node senders (75%) and public-node senders (25%); (3) **MONITOR**: watches, raises, lowers, restarts anything that dies, and runs the loggers. Each window has a clear title. Everything under `%USERPROFILE%\grok-build\tn-storm-11-10\`. Senders start at 07:30:00Z and stop at 12:30:00Z by the clock, whatever time it is pasted.

## Log everything

From R1 to END, as in [LOGGING.md](../LOGGING.md), `step` = `window`: `sec.csv`, `minute.csv`, `public-nodes.csv`, `rejects.csv`, `miner.csv`, `host.csv`, `node.csv`, `events.csv` (every `rate-change`, `fix`, restart, `deviation`), `gates.csv`, `ntp.csv`; after END `chain-count.csv`, `confirm.csv`, `steps.csv` (`window` and `window-h1` … `window-h5`) and `SUMMARY.md`. Per-transaction logs and ids stay on the desk.

## Handoff files for the bot

stp carries these to the bot. Formats: [LOGGING.md](../LOGGING.md#handoff-files-build-to-the-bot).

1. **`FOR-TN10-OPS-ready-1110.txt` by 09:20 CEST:** ready, node synced, senders, coins, fee pair, miner, disk free.
2. **`FOR-TN10-OPS-result-1110.txt` by 16:30 CEST:** window and hour totals, your network unique peak minute, mean and median, every change and fix.

## After END

1. **END 14:30 CEST:** senders stop, miner off, live loggers stop. Node stays up.
2. **COUNT (14:30–16:30 CEST, before pruning):** `chain-count.csv` per minute from 08:30 to 14:30 CEST from your node.
3. Write `steps.csv`, `SUMMARY.md` (peak complete minute, 5-hour mean and median, what broke, what you did) and the result file.
4. **By 17:30 CEST:** commit to `logs/build/` in **STP-KAS/tn-storm-11-10**. Counts only. No force-push, no tags, no releases. The repo is public: leak-scan first.

## Never

No IP, host, port, key, seed, txid, wallet address or local path in the repo. No tunnel. No second miner. No archival. No sending to the bot's node. No more than 25% of your senders on the public nodes. No firing at a dead node. No stopping before END unless stp halts.
