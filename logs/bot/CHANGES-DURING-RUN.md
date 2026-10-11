> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md)

# Bot side: changes during the run (Sun 11 Oct 2026)

Changes made after the GO lock. Each one is also in `events.csv` (pushed after END) as a `rate-change` or `deviation`.

| CEST | Change | Why |
|---|---|---|
| 11:28 | stp asked **both sides to increase effort**. Build is increasing as well (see [Build's logs](../build/README.md)). | stp, 11:28 CEST |
| 11:29 | Bot target **1,011 -> 1,300 tx/s** (`rate-change`). Before this, the automatic rate rule had lowered 1,223 -> 1,112 -> 1,011 because of node-dead/stall events on the public nodes, not rejects (rejects were 0). | stp 11:28: increase effort |
| 11:29 | New rate rule for the rest of the run: **floor 1,100**; +10% after every clean 15 minutes, up to 2,400; a not-clean window lowers by **5%** only on real overload (accepted < 95% of submitted, or rejects >= 2%), otherwise the rate holds. Node-dead/stall noise no longer lowers the rate. | stp 11:28: increase effort |
| 11:30-11:34 | Senders **15 -> 18**, launched one at a time, each on 4 of the 5 public nodes. Extra senders launch only while box RAM is at least 2.5 GB, never under 1.5 GB. `deviation`: GO-BOT said at most 15 senders (box RAM). | stp 11:28: increase effort |
| 11:49 | stp: **bot fee +40% at the next rate climb**: 400/600 -> 560/840 sompi/gram, cap 840 for this run (`deviation`: above the GO cap 600). The node-quote-skip threshold stays 400. Armed 11:50. **Fired at 12:31:10 CEST** with the rate climb 1,300 -> 1,430 tx/s; all 18 senders on 560/840 from then (`fee-change`, `deviation`). | stp, 11:49 CEST |
| 11:50 | stp: **Build asked to climb like the bot**: +10% per clean 15 min, -5% only on real overload, floor = its 11:50 rate; and raise its fees +40% at its next climb (public share 200/300 -> 280/420; desk pair x1.4). Build's side, see [Build's logs](../build/README.md). | stp, 11:50 CEST |
| 11:50-11:54 | Senders restarted one at a time onto a sender build that takes the fee cap from the control file (needed for 840; fees stayed 400/600 until the climb). | fee change prep |
| 12:31 | **Fix: the 15-minute rate check undercounted submitted tx.** A non-integer file read offset made it skip most sender files at random (the 11:15, 11:44, 12:14 and 12:29 checks showed 0-209 tx/s while the bot actually sent ~1,060-1,300). Fixed at 12:31; the 12:14-12:29 window was re-checked with full data: 1,291.9 submitted / 1,291.5 accepted tx/s, 99.97%, 0 rejects -> clean -> rate 1,300 -> 1,430 (`fix`, `rate-change`). | rate rule bug |
| 11:56-12:00 | Box paused for about 4 minutes (no rows written); all senders were restarted automatically by the stall detector on resume, and once more at 12:04. Logged, no manual fix. | box pause |

Label: no-signature hop, anyone-can-spend, not realistic payments.
