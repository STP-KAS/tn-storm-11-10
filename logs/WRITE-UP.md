> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# Write-up: TN10 storm, Sun 11 Oct 2026

Companion to [COMBINED.md](COMBINED.md). Figures from the log files only. One clock this time: START 07:30Z (09:30 CEST) for both sides.

## In one paragraph

Both sides went flat out at 09:30 CEST on one target: as many tx/s as possible, network unique accepted. stp extended the run by one hour, then **halted it at 14:33:01 CEST (12:33:01Z)**. Stopped early by stp: taking a break, other things on the agenda (bot and Build). Over 07:30Z to the halt the network median was **3,107.1 tx/s** (171 complete minutes), the peak complete minute **3,583.1 tx/s** at 11:28Z, and the mean **2,833.1 tx/s**. All three include about 56 tx/s of TN10 base load. Last night's best step median was 2,642.4 (corrected 11 Oct, was 2,644.9); this time the median of the whole window is over 3,000. **Claim (measured on TN10).** Build's results: **pending**.

## What ran

- **Bot** (TN10 ops with tn ops2, on the box): sent through the **five public TN10 nodes only**; its node n2 did the reads, the chain count and its one miner. Started at 919 tx/s with 15 senders, raised by a 15-minute rate check. No-signature hop, anyone-can-spend, not realistic payments.
- **Build** (Grok Build on stp's desk): about 75% of senders on its own desk node, 25% on the public nodes, one miner. Its logs: **pending**.

## Timeline (CEST, UTC in brackets)

| CEST | What |
|---|---|
| 09:30 (07:30Z) | START. Bot at 919 tx/s, 15 senders, fees 400/600. Build ready file not passed to the bot by START; the bot does not wait. |
| 09:43 | All 15 bot senders stalled at once; the stall detector restarted them; vector and electron marked node-dead for a while. Rate check lowered 919 -> 835. |
| 10:00-10:45 | Clean checks: 835 -> 919 -> 1,011 -> 1,112 -> 1,223 tx/s. |
| 10:49 | Second mass stall (all 15); auto restart. Rate checks then lowered 1,223 -> 1,112 -> 1,011 on node-dead noise and a check bug (see 12:31), not on rejects. |
| **11:28-11:34** | stp asked both sides to increase effort. Bot 1,011 -> **1,300 tx/s**; new rule: floor 1,100, +10% per clean 15 min, cut only on real overload. Senders 15 -> **18**. |
| 11:49-11:50 | stp: bot fees +40% at the next climb (**560/840**, armed 11:50). stp asked Build to climb the same way and raise fees +40% (public share 280/420). Build's side: pending. |
| 11:56-12:00 | Box paused about 4 minutes; senders restarted on resume, and again at 12:04. |
| **12:31** | Fix: the rate check had undercounted submitted tx (a file-read bug). Re-checked clean -> **1,430 tx/s**, and the **560/840** fees fired. |
| 13:08-13:25 (11:08-11:25Z) | **n2 froze** (DAA stuck, sink lag about 16 min); miner off; n2 restarted 13:25. The chain count lumps these minutes, and the bot's minute.csv has no rows for 11:09-11:22Z. Senders restarted at 13:23. |
| **13:28 (11:28Z)** | **Peak complete minute: 3,583.1 tx/s.** |
| 13:44 | Clean check -> **1,573 tx/s**. |
| **14:05-14:08** | stp: fees x2 to **1,120/1,680**, fired 14:08:40 (12:08:40Z). Rate held high to END, no cuts; Build same. |
| 14:14 | stp: END extended +1 h to 15:30 CEST (13:30Z), same fees and pace. |
| 14:29 | Clean check -> **1,730 tx/s**. |
| **14:33:01 (12:33:01Z)** | **HALT by stp.** Stopped early by stp: taking a break, other things on the agenda. (bot and Build) |
| 14:36-14:46 | Chain count from n2 over 06:30Z to the halt minute, before pruning, saved before any node restart. |

## What went well

- **Network median over 3,000 tx/s for the whole window** (3,107.1, n=171); 110 of 171 complete minutes at or above 3,000. **Claim (measured on TN10).**
- Bot accepted almost everything it got into a mempool: 20.03 million submit-OK, 20.01 million seen accepted on n2 (99.9%). **Claim (measured on TN10).**
- Two-node block-time counter from 10:49Z: n2 and a public node agreed on every minute they both had (0 differences). **Claim (measured on TN10).**

## What broke

1. **Mass sender stalls** at 09:43, 10:49, 12:00, 12:04 and 13:23 CEST: all senders went quiet at once and were restarted automatically. They cost rate and made the 15-minute checks lower the rate.
2. **Rate check bug** (fixed 12:31): it read only part of the sender files, so four checks showed 0-209 tx/s while the bot was sending about 1,060-1,300.
3. **n2 freeze** 13:08-13:25 CEST; restarted on the same flags. 47 lumped chain-count rows, including these minutes. [minute.csv](bot/minute.csv) now marks 11:09-11:22Z as `node_state = gap` with the reason (**partly fixed**); sent/accepted for those minutes stay empty, so what the bot sent then is still not in the logs.
4. **Box memory tight** with 18 senders (down to about 1.0 GB free); several checks failed on RAM alone and sender launches were held.
5. **Public node errors:** 655 errors on muon-10.kaspa.blue; 701 of the 764 bot rejects fell in 10:30-11:30Z. Reject reasons are in [bot/rejects.csv](bot/rejects.csv): rpc-error 670, orphan 49, already-in-mempool 45.

## Fees and congestion

- Bot fees went 400/600 -> 560/840 -> 1,120/1,680 sompi/gram during the run (all above the GO cap of 600, logged as deviations). stp raised them because covenant activity was growing on Kaspa Stream (stp's observation from the dashboard, not our measurement).
- After the 2x fee the network median fell to 2,797.9 (15 complete minutes, 12:09-12:32Z) from 3,341.1 under 560/840. **Not sure / open for debate**: the window is short, and from 12:30Z the network count dropped to about 1,700 tx/s while the bot kept sending about 1,626 tx/s. Build's logs: pending.
- Fees here are paid in tKAS, which has no value. This run shows how fee raising works under load, not what an attack would cost on mainnet. **Needs more testing.**

## Lessons

- One clock worked: both sides were sending in the same window, and the whole-window median cleared 3,000.
- Count rate-check input from every sender file, every time; a partial read silently held the bot back for about an hour.
- Mass stalls are the bot's main bottleneck now, more than rejects. Four of the five came right after a gap of 3 to 14 minutes in the bot's own logs (gaps from 09:39, 10:46, 11:57 and 13:09 CEST), so a box pause may be the cause rather than the public nodes. **Not sure / open for debate.**
- 18 senders is about what the box's RAM can carry; more rate needs fewer, faster senders or more memory.
- Keep the headline rule in the repo: chain-count.csv now has `headline_strict` (the 171 minutes) next to the older, looser `complete_minute`.
- Log per-transaction submit and accept times again ([confirm.csv](bot/confirm.csv) and [order.csv](bot/order.csv) are still header-only today — **still open**).

## Pass/fail

No pass line was set; the target was "as many as possible". Network unique accepted, 07:30Z to the halt: median **3,107.1 tx/s**, peak complete minute **3,583.1 tx/s**, mean **2,833.1 tx/s**, each including about 56 tx/s base load. Build: **pending**.

Counts only: no txid, key, seed, host IP, port or wallet address in this repo. Kaspa Testnet-10 only; tKAS has no value.
