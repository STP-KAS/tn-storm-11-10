> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# go: the shared rule book, one target, one window

Same rules as [tn10-storm-1010/go](https://github.com/STP-KAS/tn10-storm-1010/blob/main/go/README.md), with **one big change: no step timeline.** Only a start, an end and a target. Prompts: [GO-BOT](bot/GO-BOT.md) · [GO-BUILD](build/GO-BUILD.md) · logging: [LOGGING.md](LOGGING.md).

## Target

**As many tx/s as possible, sustained for 5 hours.** Headline = **network unique accepted tx/s**, counted once from chain data, never summed across sides:

- the **peak complete minute**, and
- the **5-hour mean and median** over every complete minute from START to END.

Testnet-10 only. tKAS has no value.

## Start and end

| What | Brussels (CEST) | UTC |
|---|---|---|
| Ready read R1, logging starts | 09:00 | 07:00 |
| Ready read R2, Build writes its ready file, miners on | 09:20 | 07:20 |
| **START: both sides flat out** | **09:30** | **07:30** |
| **END: senders stop, miners off** | **14:30** | **12:30** |
| Chain count (before pruning) | 14:30–16:30 | 12:30–14:30 |
| Logs pushed | by 17:30 | by 15:30 |
| Suggested window for Kaspa Pulse's counter | 09:10–14:35 | 07:10–12:35 |

Sunday 11 Oct 2026. Brussels is UTC+2. Clocks in git stay in UTC. **One clock for both sides.** START does not move. A side that is late joins as soon as it can and logs the gap as a `deviation`.

## Why one clock (last night's lesson)

**Claim (measured on TN10):** on 10 to 11 Oct the bot and Build ran on different clocks (bot T0 18:30Z, Build T0 15:00Z), so the two sides were never at full rate together. The best network median for a step was **2,645 tx/s** (MAX) and the 3,000 line was not met. Sources: [WRITE-UP.md](https://github.com/STP-KAS/tn10-storm-1010/blob/main/logs/WRITE-UP.md), [COMBINED.md](https://github.com/STP-KAS/tn10-storm-1010/blob/main/logs/COMBINED.md). Today both go flat out at 09:30 CEST and stay there until 14:30 CEST.

## Who does what

| Side | Who | Sends to | Node | Miner | Mode |
|---|---|---|---|---|---|
| Bot | **TN10 ops** (n2, miner, senders) with **tn ops2** (logging, count, write-up) | The **five public TN10 nodes only** | n2 on the box: private, pruned, reads and miner only | 1 | **Steady**: its max sustainable rate, held |
| Build | **Grok Build** on stp's Windows desk | Its **own desk node** (75%) and the five public TN10 nodes (25%, backs off first if the bot suffers) | Private, pruned, not archival | 1 | **Adaptive**: watch the network all the time, raise or lower, fix without stopping |

Never submit to the other side's node.

## Rules

- **Fees.** Bot: half the lanes at 400, half at 600 sompi/gram, floor 100, cap 600; sit out while the normal quote is above 400. Build: 200 base, 300 tier; sit out while the normal quote is above 200. If the sit-out rule would stop **every** sender for more than 5 minutes, log `fee-rule-blocks-all` with the quote and keep sending at the side's tiers.
- **Node-dead rule (Kaspa Pulse).** Own node used for submits: a sender stops on 5 s of RPC failure, not synced, sink lag over 60 s on a fresh read, or a virtual DAA stall over 30 s, and resumes by itself when a fresh read is healthy. Public nodes: about 20 errors in a row cools that node for 30 s, load moves to the others. A failed submit is a reject, never "sent". No firing at a dead node.
- **Keep going, but fix first.** A problem is found, fixed and logged (`fix`, `deviation`), never turned into a stop or a question. The run only stops at END or on stp's halt.
- **Disk.** Build keeps at least 30 GB free. The box guard stops n2 below 10 GB free.
- **Miners.** Exactly one per side, one thread, on the side's own node, on at R2, off at END. No public mining endpoint.
- **Count once, from the chain, soon after END** (Kaspa Pulse): `chain-count.csv` within two hours of END, before pruning.
- **Log everything**, per second and per minute, from R1 to END: [LOGGING.md](LOGGING.md).
- **Public repo:** counts only. No key, seed, txid, IP, host, port, tunnel URL, wallet address or local path. Leak-scan before every push. No force-push, no tags, no releases.

## Lock rule

**Once stp sends a GO, it is locked.** Sending is not the start. It means: get ready now, be ready at **09:30 CEST**, and run to 14:30 CEST without stp watching. A change after the lock goes in `events.csv` as a `deviation`.

## stp's to-do before 09:30 CEST

1. Send [GO-BUILD](build/GO-BUILD.md) to Build **now** (its desk node must be synced by 09:30).
2. Send [GO-BOT](bot/GO-BOT.md) to TN10 ops.
3. Tell Kaspa Pulse: START 09:30 CEST, END 14:30 CEST, suggested counter window 09:10–14:35 CEST.
4. At about 09:20 CEST, paste Build's `FOR-TN10-OPS-ready-1110.txt` to the bot.
