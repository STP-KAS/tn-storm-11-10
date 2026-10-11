| 08:43:33 CEST | 06:43:33 UTC | watchdog: scheduler not running -> (re)start |
| 08:43:33 CEST | 06:43:33 UTC | scheduler armed pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 08:43:33 CEST | 06:43:33 UTC | PLAN (STP-KAS/tn10-storm-2026-10-11 go/bot/GO-BOT.md (locked, pasted by stp 08:39 CEST)): flat-out bot window 07:30-12:30 UTC (09:30-14:30 CEST). Submit ONLY to the 5 public TN10 nodes (4 of 5 per sender, strike-aware picks); n2 = 1 miner + reads. Rate: start 919 tx/s, checked every 15 min over the full last 15 min (full 15 min: >=99% of submitted seen accepted, p90 submit RTT <=10 s, no node-dead event, consensus rejects <2%, box RAM >=1.5 GB, CPU avg <95%; raise +10% if clean, lower -10% if not); max 2400. Fees 400/600, floor 100, cap 600; per-node skip if quote > 400. 15 senders x 200 lanes, staggered, stall detector 45 s -> SIGKILL + relaunch (cap 200, backoff), no launch at RAM < 1.5 GB. No BUILD-OK gate. Miner 1 thread 07:20-12:30 UTC. [no-signature hop, anyone-can-spend, not realistic payments] |
| 08:43:33 CEST | 06:43:33 UTC | n2 first read: synced true, utxoindex false, sink lag 0.4 s, DAA 593665258 |
| 08:43:33 CEST | 06:43:33 UTC | n2 unhealthy under pubMode (utxoindex off): senders KEEP submitting on public nodes (stp 16:19) |
| 08:43:33 CEST | 06:43:33 UTC | prep: n2 synced true, utxoindex false, lag 0.4 s; no sends, miner off until 07:20 UTC |
| 08:44:00 CEST | 06:44:00 UTC | live summary: loop started (pid -): write every 10 min, push every 15 min from G1 to END+15 min |
| 08:58:34 CEST | 06:58:34 UTC | prep: n2 synced true, utxoindex false, lag 0.5 s; no sends, miner off until 07:20 UTC |
| 09:00:00 CEST | 07:00:00 UTC | GATE 1 07:00 UTC (logging start; never holds public-node senders) (own n2 sink): synced true, utxoindex false, sink lag 0.4 s, mempool 294, quote 100 -> FAIL |
| 09:00:00 CEST | 07:00:00 UTC | BOT BLOCK: session down, runners 0, disk 34 GB, n2 synced true utxoindex false lag 0.4 s mempool 294, bot sub/acc 0/0 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 54.6 tx/s (10/10 valid), miner 0, mining share 0%, dup share 0.4171 |
| 09:00:11 CEST | 07:00:11 UTC | live summary: pushed logs/bot/SUMMARY.md (2f80114) |
| 09:10:00 CEST | 07:10:00 UTC | BOT BLOCK: session down, runners 0, disk 33.9 GB, n2 synced true utxoindex false lag 0.5 s mempool 294, bot sub/acc 0/0 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 54.6 tx/s (10/10 valid), miner 0, mining share 0%, dup share 0.3292 |
| 09:15:18 CEST | 07:15:18 UTC | live summary: pushed logs/bot/SUMMARY.md (ac56248) |
| 09:20:00 CEST | 07:20:00 UTC | GATE 2 07:20 UTC (ready check) (own n2 sink): synced true, utxoindex false, sink lag 0.5 s, mempool 294, quote 100 -> FAIL |
| 09:20:00 CEST | 07:20:00 UTC | READY CHECK: Build started? CONFIRMED (no BUILD-OK gate on 11 Oct (bot does not wait for Build)); n2 gate fail (logged; does not hold public-node senders) |
| 09:20:00 CEST | 07:20:00 UTC | BUILD CONFIRMED: no BUILD-OK gate on 11 Oct (bot does not wait for Build) -> bot sends from the open step |
| 09:20:00 CEST | 07:20:00 UTC | miner ON (1 box CPU kaspa-miner, 1 thread, n2 gRPC): 07:20 UTC start, n2 synced |
| 09:20:00 CEST | 07:20:00 UTC | BOT BLOCK: session up, runners 15, disk 33.9 GB, n2 synced true utxoindex false lag 0.5 s mempool 294, bot sub/acc 0/0 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 55.3 tx/s (9/9 valid), miner 1, mining share 0%, dup share 0.3602 |
| 09:30:00 CEST | 07:30:00 UTC | ROW window window begins (07:30-12:30 UTC; plan bot: max; Build: max; miner on) |
| 09:30:00 CEST | 07:30:00 UTC | window target: 919 tx/s (ramp start 919, raise +10% after a full clean 15 min, lower if not) |
| 09:30:00 CEST | 07:30:00 UTC | fee quote at step start: 100 (pair 400/600, cap 600, floor 100, sit out above 400) |
| 09:30:00 CEST | 07:30:00 UTC | DEVIATION: Build ready file (FOR-TN10-OPS-ready-1110.txt) not passed to the bot by START 09:30 CEST; bot does not wait (GO-BOT) |
| 09:30:00 CEST | 07:30:00 UTC | rate: window senders 919 tx/s total (15 up x 61.267), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:30:00 CEST | 07:30:00 UTC | BOT BLOCK: session up, runners 15, disk 21.2 GB, n2 synced true utxoindex false lag 0.2 s mempool 1, bot sub/acc 0/0 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 54.3 tx/s (9/9 valid), miner 1, mining share 28.35%, dup share 0.4736 |
| 09:30:27 CEST | 07:30:27 UTC | live summary: pushed logs/bot/SUMMARY.md (3379cec) |
| 09:31:42 CEST | 07:31:42 UTC | DEVIATION: box disk 18.8 GB free (< 20): senders pause at 8 GB; n2 disk guard STOP at 5 GB, halt at 3 GB; pub submit fallback below 10 GB |
| 09:43:10 CEST | 07:43:10 UTC | B0: B = 2588.4 tx/s (median of 8 valid n2 minutes 07:30-07:40 UTC) -> reported only; combined targets are fixed (250/1,000/1,500/2,000/2,500/3,500/3,200); bot rates stay the bot column |
| 09:43:11 CEST | 07:43:11 UTC | S1 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S2 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S3 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S4 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S5 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | public node vector-10.kaspa.green: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 09:43:11 CEST | 07:43:11 UTC | S6 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S7 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S8 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S9 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S10 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S11 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S12 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S13 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | S14 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | public node electron-10.kaspa.blue: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 09:43:11 CEST | 07:43:11 UTC | S15 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 09:43:11 CEST | 07:43:11 UTC | BOT BLOCK: session up, runners 15, disk 15.5 GB, n2 synced true utxoindex false lag 298.3 s mempool 7160, bot sub/acc 459.2/458.8 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2541.4 tx/s (5/6 valid), miner 1, mining share 34.18%, dup share 0.4439 |
| 09:43:12 CEST | 07:43:12 UTC | S1 not running -> relaunch 1/200 |
| 09:43:12 CEST | 07:43:12 UTC | rate: window senders 919 tx/s total (9 up x 102.111), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:43:15 CEST | 07:43:15 UTC | S2 not running -> relaunch 1/200 |
| 09:43:18 CEST | 07:43:18 UTC | S3 not running -> relaunch 1/200 |
| 09:43:21 CEST | 07:43:21 UTC | S4 not running -> relaunch 1/200 |
| 09:43:24 CEST | 07:43:24 UTC | S5 not running -> relaunch 1/200 |
| 09:43:27 CEST | 07:43:27 UTC | S6 not running -> relaunch 1/200 |
| 09:43:30 CEST | 07:43:30 UTC | S7 not running -> relaunch 1/200 |
| 09:43:33 CEST | 07:43:33 UTC | S8 not running -> relaunch 1/200 |
| 09:43:36 CEST | 07:43:36 UTC | S9 not running -> relaunch 1/200 |
| 09:43:39 CEST | 07:43:39 UTC | S10 not running -> relaunch 1/200 |
| 09:43:39 CEST | 07:43:39 UTC | rate: window senders 919 tx/s total (10 up x 91.9), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:43:42 CEST | 07:43:42 UTC | S11 not running -> relaunch 1/200 |
| 09:43:42 CEST | 07:43:42 UTC | rate: window senders 919 tx/s total (11 up x 83.545), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:43:45 CEST | 07:43:45 UTC | S12 not running -> relaunch 1/200 |
| 09:43:45 CEST | 07:43:45 UTC | rate: window senders 919 tx/s total (12 up x 76.583), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:43:48 CEST | 07:43:48 UTC | S13 not running -> relaunch 1/200 |
| 09:43:48 CEST | 07:43:48 UTC | rate: window senders 919 tx/s total (13 up x 70.692), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:43:51 CEST | 07:43:51 UTC | S14 not running -> relaunch 1/200 |
| 09:43:51 CEST | 07:43:51 UTC | rate: window senders 919 tx/s total (14 up x 65.643), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:43:54 CEST | 07:43:54 UTC | S15 not running -> relaunch 1/200 |
| 09:43:54 CEST | 07:43:54 UTC | rate: window senders 919 tx/s total (15 up x 61.267), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:45:04 CEST | 07:45:04 UTC | RAMP EVAL 09:30-09:45 CEST at 919 tx/s: sub/acc 587.9/587.1 tx/s, acc/sub 99.86%, rejects 0% (+0 transport), RAM min 2.98 GB, CPU avg 48% -> NOT clean (2 node-dead events; submitted 587.9 < 90% of 919); rate 919 -> 835 |
| 09:45:04 CEST | 07:45:04 UTC | rate: window senders 835 tx/s total (15 up x 55.667), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 09:45:23 CEST | 07:45:23 UTC | live summary: pushed logs/bot/SUMMARY.md (4f8ca95) |
| 09:47:11 CEST | 07:47:11 UTC | box disk back to 32.9 GB free |
| 09:50:00 CEST | 07:50:00 UTC | BOT BLOCK: session up, runners 15, disk 32.8 GB, n2 synced true utxoindex false lag 0.4 s mempool 783, bot sub/acc 554.3/552.8 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2214.9 tx/s (3/6 valid), miner 1, mining share 22.36%, dup share 0.4606 |
| 10:00:00 CEST | 08:00:00 UTC | RAMP EVAL 09:45-10:00 CEST at 835 tx/s: sub/acc 833.5/834.1 tx/s, acc/sub 100%, rejects 0% (+0 transport), RAM min 2.48 GB, CPU avg 48.5% -> clean; rate 835 -> 919 |
| 10:00:00 CEST | 08:00:00 UTC | rate: window senders 919 tx/s total (15 up x 61.267), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:00:00 CEST | 08:00:00 UTC | BOT BLOCK: session up, runners 15, disk 33.7 GB, n2 synced true utxoindex false lag 0 s mempool 457, bot sub/acc 833.6/834.1 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2320.3 tx/s (9/9 valid), miner 1, mining share 34.45%, dup share 0.4265 |
| 10:00:13 CEST | 08:00:13 UTC | live summary: pushed logs/bot/SUMMARY.md (6147e12) |
| 10:10:00 CEST | 08:10:00 UTC | BOT BLOCK: session up, runners 15, disk 33.9 GB, n2 synced true utxoindex false lag 0.4 s mempool 4987, bot sub/acc 891/890.4 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2364.2 tx/s (9/9 valid), miner 1, mining share 32.28%, dup share 0.4391 |
| 10:15:00 CEST | 08:15:00 UTC | RAMP EVAL 10:00-10:15 CEST at 919 tx/s: sub/acc 900/898.8 tx/s, acc/sub 99.87%, rejects 0% (+0 transport), RAM min 2.56 GB, CPU avg 37.2% -> clean; rate 919 -> 1011 |
| 10:15:00 CEST | 08:15:00 UTC | rate: window senders 1011 tx/s total (15 up x 67.4), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:15:21 CEST | 08:15:21 UTC | live summary: pushed logs/bot/SUMMARY.md (3af1674) |
| 10:20:00 CEST | 08:20:00 UTC | BOT BLOCK: session up, runners 15, disk 33.9 GB, n2 synced true utxoindex false lag 0.2 s mempool 12231, bot sub/acc 962.8/962.1 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3171.7 tx/s (10/10 valid), miner 1, mining share 32.57%, dup share 0.2757 |
| 10:30:01 CEST | 08:30:01 UTC | RAMP EVAL 10:15-10:30 CEST at 1011 tx/s: sub/acc 1009.5/1009.6 tx/s, acc/sub 100%, rejects 0% (+2 transport), RAM min 2.46 GB, CPU avg 39.8% -> clean; rate 1011 -> 1112 |
| 10:30:01 CEST | 08:30:01 UTC | rate: window senders 1112 tx/s total (15 up x 74.133), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:30:01 CEST | 08:30:01 UTC | BOT BLOCK: session up, runners 15, disk 33.9 GB, n2 synced true utxoindex false lag 0.1 s mempool 9781, bot sub/acc 1008.7/1008.3 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3112.6 tx/s (10/10 valid), miner 1, mining share 29.79%, dup share 0.3026 |
| 10:30:11 CEST | 08:30:11 UTC | live summary: pushed logs/bot/SUMMARY.md (4ff423d) |
| 10:40:00 CEST | 08:40:00 UTC | BOT BLOCK: session up, runners 15, disk 34.4 GB, n2 synced true utxoindex false lag 0.6 s mempool 6222, bot sub/acc 1109.9/1109.8 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2933.3 tx/s (9/9 valid), miner 1, mining share 31.06%, dup share 0.2923 |
| 10:45:01 CEST | 08:45:01 UTC | RAMP EVAL 10:30-10:45 CEST at 1112 tx/s: sub/acc 1100.8/1100.6 tx/s, acc/sub 99.98%, rejects 0% (+4 transport), RAM min 2.32 GB, CPU avg 40% -> clean; rate 1112 -> 1223 |
| 10:45:01 CEST | 08:45:01 UTC | rate: window senders 1223 tx/s total (15 up x 81.533), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:45:19 CEST | 08:45:19 UTC | live summary: pushed logs/bot/SUMMARY.md (b2365a6) |
| 10:49:33 CEST | 08:49:33 UTC | S1 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S2 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S3 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S4 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S5 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S6 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S7 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S8 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | public node neutrino-10.kaspa.stream: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 10:49:33 CEST | 08:49:33 UTC | S9 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | public node muon-10.kaspa.blue: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 10:49:33 CEST | 08:49:33 UTC | S10 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | public node boson-10.kaspa.red: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 10:49:33 CEST | 08:49:33 UTC | S11 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | public node electron-10.kaspa.blue: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 10:49:33 CEST | 08:49:33 UTC | S12 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S13 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S14 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:33 CEST | 08:49:33 UTC | S15 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 10:49:34 CEST | 08:49:34 UTC | S1 not running -> relaunch 2/200 |
| 10:49:34 CEST | 08:49:34 UTC | rate: window senders 1223 tx/s total (9 up x 135.889), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:49:37 CEST | 08:49:37 UTC | S2 not running -> relaunch 2/200 |
| 10:49:40 CEST | 08:49:40 UTC | S3 not running -> relaunch 2/200 |
| 10:49:43 CEST | 08:49:43 UTC | S4 not running -> relaunch 2/200 |
| 10:49:46 CEST | 08:49:46 UTC | S5 not running -> relaunch 2/200 |
| 10:49:49 CEST | 08:49:49 UTC | S6 not running -> relaunch 2/200 |
| 10:49:52 CEST | 08:49:52 UTC | S7 not running -> relaunch 2/200 |
| 10:49:55 CEST | 08:49:55 UTC | S8 not running -> relaunch 2/200 |
| 10:49:58 CEST | 08:49:58 UTC | S9 not running -> relaunch 2/200 |
| 10:50:00 CEST | 08:50:00 UTC | BOT BLOCK: session up, runners 9, disk 34.5 GB, n2 synced true utxoindex false lag 0.4 s mempool 11, bot sub/acc 649.9/646 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3296.6 tx/s (5/5 valid), miner 1, mining share 27.31%, dup share 0.3148 |
| 10:50:01 CEST | 08:50:01 UTC | S10 not running -> relaunch 2/200 |
| 10:50:01 CEST | 08:50:01 UTC | rate: window senders 1223 tx/s total (10 up x 122.3), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:50:04 CEST | 08:50:04 UTC | S11 not running -> relaunch 2/200 |
| 10:50:04 CEST | 08:50:04 UTC | rate: window senders 1223 tx/s total (11 up x 111.182), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:50:07 CEST | 08:50:07 UTC | S12 not running -> relaunch 2/200 |
| 10:50:07 CEST | 08:50:07 UTC | rate: window senders 1223 tx/s total (12 up x 101.917), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:50:10 CEST | 08:50:10 UTC | S13 not running -> relaunch 2/200 |
| 10:50:10 CEST | 08:50:10 UTC | rate: window senders 1223 tx/s total (13 up x 94.077), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:50:13 CEST | 08:50:13 UTC | S14 not running -> relaunch 2/200 |
| 10:50:13 CEST | 08:50:13 UTC | rate: window senders 1223 tx/s total (14 up x 87.357), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:50:16 CEST | 08:50:16 UTC | S15 not running -> relaunch 2/200 |
| 10:50:16 CEST | 08:50:16 UTC | rate: window senders 1223 tx/s total (15 up x 81.533), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 10:51:45 CEST | 08:51:45 UTC | deviation: day-watch: mass stall all 15 senders at 10:49:33 CEST; scheduler auto SIGKILL+relaunch 2/200 with fresh picks + public-node stall-strike avoid (muon/boson/electron); all 15 up by 10:50:16; live ~1200/1223; no manual fix |
| 11:00:00 CEST | 09:00:00 UTC | BOT BLOCK: session up, runners 15, disk 34.4 GB, n2 synced true utxoindex false lag 0.3 s mempool 6641, bot sub/acc 1214.1/1213.4 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2738.2 tx/s (7/9 valid), miner 1, mining share 24.77%, dup share 0.3847 |
| 11:00:01 CEST | 09:00:01 UTC | RAMP EVAL 10:45-11:00 CEST at 1223 tx/s: sub/acc 884.1/882.1 tx/s, acc/sub 99.77%, rejects 0% (+2 transport), RAM min 2.21 GB, CPU avg 40.4% -> NOT clean (4 node-dead events; submitted 884.1 < 90% of 1223); rate 1223 -> 1112 |
| 11:00:01 CEST | 09:00:01 UTC | rate: window senders 1112 tx/s total (15 up x 74.133), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:00:27 CEST | 09:00:27 UTC | live summary: pushed logs/bot/SUMMARY.md (5fd5e55) |
| 11:05:55 CEST | 09:05:55 UTC | day-watch: OK at 1112; 15 senders; miner 1; disk 35G; RAM ~3.6G; no manual fix |
| 11:10:00 CEST | 09:10:00 UTC | BOT BLOCK: session up, runners 15, disk 34.3 GB, n2 synced true utxoindex false lag 0.8 s mempool 3023, bot sub/acc 1110.5/1109.6 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3060.6 tx/s (9/9 valid), miner 1, mining share 32.4%, dup share 0.2775 |
| 11:15:01 CEST | 09:15:01 UTC | RAMP EVAL 11:00-11:15 CEST at 1112 tx/s: sub/acc 0/0 tx/s, acc/sub -%, rejects 0% (+0 transport), RAM min 3.05 GB, CPU avg 42.3% -> NOT clean (accepted -% of submitted < 99%; p90 - s > 10; submitted 0 < 90% of 1112); rate 1112 -> 1011 |
| 11:15:01 CEST | 09:15:01 UTC | rate: window senders 1011 tx/s total (15 up x 67.4), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:15:15 CEST | 09:15:15 UTC | live summary: pushed logs/bot/SUMMARY.md (d750d08) |
| 11:20:00 CEST | 09:20:00 UTC | BOT BLOCK: session up, runners 15, disk 33.8 GB, n2 synced true utxoindex false lag 0.4 s mempool 127, bot sub/acc 1060.1/1061.6 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2983.3 tx/s (9/9 valid), miner 1, mining share 31.98%, dup share 0.3052 |
| 11:28:25 CEST | 09:28:25 UTC | day-watch: OK hold 1011; 15 senders; miner 1; disk 34G; RAM ~3.3G; no manual fix |
| 11:29:52 CEST | 09:29:52 UTC | watchdog: scheduler not running -> (re)start |
| 11:29:52 CEST | 09:29:52 UTC | stp 11:28 CEST: increase effort: rate 1011 -> 1300 tx/s; new rule: floor 1,100, +10% per clean 15 min up to 2400, -5% only on real overload (acc < 95% of sub or rejects >= 2%), else hold; next eval in 15 min |
| 11:29:52 CEST | 09:29:52 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 11:29:52 CEST | 09:29:52 UTC | n2 first read: synced true, utxoindex false, sink lag 0.7 s, DAA 593767635 |
| 11:30:17 CEST | 09:30:17 UTC | watchdog: scheduler not running -> (re)start |
| 11:30:17 CEST | 09:30:17 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 11:30:17 CEST | 09:30:17 UTC | n2 first read: synced true, utxoindex false, sink lag 0.4 s, DAA 593767906 |
| 11:30:17 CEST | 09:30:17 UTC | DEVIATION: stp 11:28 increase effort: senders 15 -> 16 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:30:24 CEST | 09:30:24 UTC | live summary: pushed logs/bot/SUMMARY.md (bc507bd) |
| 11:30:42 CEST | 09:30:42 UTC | watchdog: scheduler not running -> (re)start |
| 11:30:42 CEST | 09:30:42 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 11:30:42 CEST | 09:30:42 UTC | n2 first read: synced true, utxoindex false, sink lag 0 s, DAA 593768139 |
| 11:30:42 CEST | 09:30:42 UTC | DEVIATION: stp 11:28 increase effort: senders 15 -> 16 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:31:07 CEST | 09:31:07 UTC | watchdog: scheduler not running -> (re)start |
| 11:31:07 CEST | 09:31:07 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 11:31:07 CEST | 09:31:07 UTC | n2 first read: synced true, utxoindex false, sink lag 0.3 s, DAA 593768389 |
| 11:31:07 CEST | 09:31:07 UTC | DEVIATION: stp 11:28 increase effort: senders 15 -> 16 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:31:07 CEST | 09:31:07 UTC | rate: window senders 1300 tx/s total (16 up x 81.25), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:31:58 CEST | 09:31:58 UTC | DEVIATION: stp 11:28 increase effort: senders 16 -> 17 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:31:58 CEST | 09:31:58 UTC | rate: window senders 1300 tx/s total (17 up x 76.471), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:33:38 CEST | 09:33:38 UTC | DEVIATION: stp 11:28 increase effort: senders 17 -> 18 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:33:38 CEST | 09:33:38 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:40:01 CEST | 09:40:01 UTC | BOT BLOCK: session up, runners 18, disk 33.4 GB, n2 synced true utxoindex false lag 0.3 s mempool 8003, bot sub/acc 1296.6/1295.3 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3111.6 tx/s (10/10 valid), miner 1, mining share 32.57%, dup share 0.2763 |
| 11:44:52 CEST | 09:44:52 UTC | RAMP EVAL 11:29-11:44 CEST at 1300 tx/s: sub/acc 187.3/186.9 tx/s, acc/sub 99.81%, rejects 0% (+0 transport), RAM min 2.44 GB, CPU avg 40.2% -> NOT clean (submitted 187.3 < 90% of 1300); rate stays 1300 (not clean but no overload (node-dead/stall noise): hold) |
| 11:44:52 CEST | 09:44:52 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:45:13 CEST | 09:45:13 UTC | live summary: pushed logs/bot/SUMMARY.md (83d62d1) |
| 11:48:24 CEST | 09:48:24 UTC | S9 stalled: 0 ok submits in 45 s (44 sec rows), 2 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 11:48:24 CEST | 09:48:24 UTC | rate: window senders 1300 tx/s total (17 up x 76.471), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:48:25 CEST | 09:48:25 UTC | S9 not running -> relaunch 3/200 |
| 11:48:25 CEST | 09:48:25 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:50:00 CEST | 09:50:00 UTC | BOT BLOCK: session up, runners 18, disk 33.4 GB, n2 synced true utxoindex false lag 0.1 s mempool 9091, bot sub/acc 1290.5/1288 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3243.1 tx/s (10/10 valid), miner 1, mining share 32.29%, dup share 0.2802 |
| 11:50:52 CEST | 09:50:52 UTC | watchdog: scheduler not running -> (re)start |
| 11:50:52 CEST | 09:50:52 UTC | stp 11:49 CEST: fee +40% (400/600 -> 560/840, cap 840, node-quote-skip stays 400) ARMED: fires with the next rate increase only |
| 11:50:52 CEST | 09:50:52 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 11:50:52 CEST | 09:50:52 UTC | n2 first read: synced true, utxoindex false, sink lag 0.3 s, DAA 593780060 |
| 11:50:52 CEST | 09:50:52 UTC | DEVIATION: stp 11:28 increase effort: senders 15 -> 18 (GO-BOT said max 15 for box RAM; extra senders launch only while MemAvailable >= 2.5 GB, never under 1.5 GB) |
| 11:50:52 CEST | 09:50:52 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 11:51:09 CEST | 09:51:09 UTC | rolling restart of senders S1-S18 onto sender code with control-file fee cap (stp 11:49 fee +40% hook); one at a time, SIGKILL, scheduler relaunches |
| 11:51:10 CEST | 09:51:10 UTC | S1 not running -> relaunch 3/200 |
| 11:51:19 CEST | 09:51:19 UTC | S2 not running -> relaunch 3/200 |
| 11:51:26 CEST | 09:51:26 UTC | S3 not running -> relaunch 3/200 |
| 11:51:33 CEST | 09:51:33 UTC | S4 not running -> relaunch 3/200 |
| 11:51:42 CEST | 09:51:42 UTC | S5 not running -> relaunch 3/200 |
| 11:51:51 CEST | 09:51:51 UTC | S6 not running -> relaunch 3/200 |
| 11:52:00 CEST | 09:52:00 UTC | S7 not running -> relaunch 3/200 |
| 11:52:09 CEST | 09:52:09 UTC | S8 not running -> relaunch 3/200 |
| 11:52:18 CEST | 09:52:18 UTC | S9 not running -> relaunch 4/200 |
| 11:52:27 CEST | 09:52:27 UTC | S10 not running -> relaunch 3/200 |
| 11:52:36 CEST | 09:52:36 UTC | S11 not running -> relaunch 3/200 |
| 11:52:45 CEST | 09:52:45 UTC | S12 not running -> relaunch 3/200 |
| 11:52:54 CEST | 09:52:54 UTC | S13 not running -> relaunch 3/200 |
| 11:53:03 CEST | 09:53:03 UTC | S14 not running -> relaunch 3/200 |
| 11:53:12 CEST | 09:53:12 UTC | S15 not running -> relaunch 3/200 |
| 11:53:20 CEST | 09:53:20 UTC | S16 not running -> relaunch 1/200 |
| 11:53:27 CEST | 09:53:27 UTC | S17 not running -> relaunch 1/200 |
| 11:53:34 CEST | 09:53:34 UTC | S18 not running -> relaunch 1/200 |
| 11:53:41 CEST | 09:53:41 UTC | rolling restart done: 18 senders on new sender code (fees still 400/600 until the next rate climb) |
| 12:00:39 CEST | 10:00:39 UTC | RAMP EVAL 11:45-12:00 CEST at 1300 tx/s: sub/acc 915/911.6 tx/s, acc/sub 99.63%, rejects 0% (+3 transport), RAM min 2.34 GB, CPU avg 41.2% -> NOT clean (submitted 915 < 90% of 1300); rate stays 1300 (not clean but no overload (node-dead/stall noise): hold) |
| 12:00:39 CEST | 10:00:39 UTC | S1 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S2 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S3 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S4 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S5 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S6 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | public node vector-10.kaspa.green: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 12:00:39 CEST | 10:00:39 UTC | S7 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S8 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S9 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S10 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S11 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S12 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | public node neutrino-10.kaspa.stream: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 12:00:39 CEST | 10:00:39 UTC | S13 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S14 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S15 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | public node electron-10.kaspa.blue: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 12:00:39 CEST | 10:00:39 UTC | S16 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S17 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | S18 stalled: 0 ok submits in 45 s (3 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:00:39 CEST | 10:00:39 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:00:40 CEST | 10:00:40 UTC | BOT BLOCK: session up, runners 18, disk 33.2 GB, n2 synced true utxoindex false lag 258.3 s mempool 6098, bot sub/acc 723.3/720.3 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3187.1 tx/s (6/6 valid), miner 1, mining share 31.96%, dup share 0.2594 |
| 12:00:41 CEST | 10:00:41 UTC | S1 not running -> relaunch 4/200 |
| 12:00:41 CEST | 10:00:41 UTC | rate: window senders 1300 tx/s total (11 up x 118.182), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:00:44 CEST | 10:00:44 UTC | S2 not running -> relaunch 4/200 |
| 12:00:47 CEST | 10:00:47 UTC | S3 not running -> relaunch 4/200 |
| 12:00:50 CEST | 10:00:50 UTC | S4 not running -> relaunch 4/200 |
| 12:00:52 CEST | 10:00:52 UTC | live summary: pushed logs/bot/SUMMARY.md (3924643) |
| 12:00:53 CEST | 10:00:53 UTC | S5 not running -> relaunch 4/200 |
| 12:00:56 CEST | 10:00:56 UTC | S6 not running -> relaunch 4/200 |
| 12:00:59 CEST | 10:00:59 UTC | S7 not running -> relaunch 4/200 |
| 12:01:02 CEST | 10:01:02 UTC | S8 not running -> relaunch 4/200 |
| 12:01:05 CEST | 10:01:05 UTC | S9 not running -> relaunch 5/200 |
| 12:01:08 CEST | 10:01:08 UTC | S10 not running -> relaunch 4/200 |
| 12:01:11 CEST | 10:01:11 UTC | S11 not running -> relaunch 4/200 |
| 12:01:14 CEST | 10:01:14 UTC | S12 not running -> relaunch 4/200 |
| 12:01:14 CEST | 10:01:14 UTC | rate: window senders 1300 tx/s total (12 up x 108.333), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:01:17 CEST | 10:01:17 UTC | S13 not running -> relaunch 4/200 |
| 12:01:17 CEST | 10:01:17 UTC | rate: window senders 1300 tx/s total (13 up x 100), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:01:20 CEST | 10:01:20 UTC | S14 not running -> relaunch 4/200 |
| 12:01:20 CEST | 10:01:20 UTC | rate: window senders 1300 tx/s total (14 up x 92.857), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:01:23 CEST | 10:01:23 UTC | S15 not running -> relaunch 4/200 |
| 12:01:23 CEST | 10:01:23 UTC | rate: window senders 1300 tx/s total (15 up x 86.667), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:01:26 CEST | 10:01:26 UTC | S16 not running -> relaunch 2/200 |
| 12:01:26 CEST | 10:01:26 UTC | rate: window senders 1300 tx/s total (16 up x 81.25), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:01:29 CEST | 10:01:29 UTC | S17 not running -> relaunch 2/200 |
| 12:01:29 CEST | 10:01:29 UTC | rate: window senders 1300 tx/s total (17 up x 76.471), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:01:32 CEST | 10:01:32 UTC | S18 not running -> relaunch 2/200 |
| 12:01:32 CEST | 10:01:32 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:04:23 CEST | 10:04:23 UTC | S1 stalled: 0 ok submits in 45 s (44 sec rows), 1135 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S2 stalled: 0 ok submits in 45 s (44 sec rows), 1110 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S3 stalled: 0 ok submits in 45 s (44 sec rows), 1157 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S4 stalled: 0 ok submits in 45 s (44 sec rows), 1141 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S5 stalled: 0 ok submits in 45 s (44 sec rows), 1148 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S6 stalled: 0 ok submits in 45 s (44 sec rows), 1118 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S7 stalled: 0 ok submits in 45 s (44 sec rows), 1154 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S8 stalled: 0 ok submits in 45 s (44 sec rows), 1153 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S9 stalled: 0 ok submits in 45 s (44 sec rows), 1154 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S10 stalled: 0 ok submits in 45 s (44 sec rows), 1100 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S11 stalled: 0 ok submits in 45 s (44 sec rows), 1147 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S12 stalled: 0 ok submits in 45 s (44 sec rows), 1141 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S13 stalled: 0 ok submits in 45 s (44 sec rows), 1154 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S14 stalled: 0 ok submits in 45 s (44 sec rows), 1099 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S15 stalled: 0 ok submits in 45 s (44 sec rows), 1159 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S16 stalled: 0 ok submits in 45 s (44 sec rows), 1153 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S17 stalled: 0 ok submits in 45 s (44 sec rows), 1146 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:23 CEST | 10:04:23 UTC | S18 stalled: 0 ok submits in 45 s (44 sec rows), 1104 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 12:04:24 CEST | 10:04:24 UTC | S1 not running -> relaunch 5/200 |
| 12:04:24 CEST | 10:04:24 UTC | rate: window senders 1300 tx/s total (11 up x 118.182), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:04:27 CEST | 10:04:27 UTC | S2 not running -> relaunch 5/200 |
| 12:04:30 CEST | 10:04:30 UTC | S3 not running -> relaunch 5/200 |
| 12:04:33 CEST | 10:04:33 UTC | S4 not running -> relaunch 5/200 |
| 12:04:36 CEST | 10:04:36 UTC | S5 not running -> relaunch 5/200 |
| 12:04:39 CEST | 10:04:39 UTC | S6 not running -> relaunch 5/200 |
| 12:04:42 CEST | 10:04:42 UTC | S7 not running -> relaunch 5/200 |
| 12:04:45 CEST | 10:04:45 UTC | S8 not running -> relaunch 5/200 |
| 12:04:48 CEST | 10:04:48 UTC | S9 not running -> relaunch 6/200 |
| 12:04:51 CEST | 10:04:51 UTC | S10 not running -> relaunch 5/200 |
| 12:04:54 CEST | 10:04:54 UTC | S11 not running -> relaunch 5/200 |
| 12:04:57 CEST | 10:04:57 UTC | S12 not running -> relaunch 5/200 |
| 12:04:57 CEST | 10:04:57 UTC | rate: window senders 1300 tx/s total (12 up x 108.333), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:05:00 CEST | 10:05:00 UTC | S13 not running -> relaunch 5/200 |
| 12:05:00 CEST | 10:05:00 UTC | rate: window senders 1300 tx/s total (13 up x 100), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:05:03 CEST | 10:05:03 UTC | S14 not running -> relaunch 5/200 |
| 12:05:03 CEST | 10:05:03 UTC | rate: window senders 1300 tx/s total (14 up x 92.857), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:05:07 CEST | 10:05:07 UTC | S15 not running -> relaunch 5/200 |
| 12:05:07 CEST | 10:05:07 UTC | rate: window senders 1300 tx/s total (15 up x 86.667), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:05:10 CEST | 10:05:10 UTC | S16 not running -> relaunch 3/200 |
| 12:05:10 CEST | 10:05:10 UTC | rate: window senders 1300 tx/s total (16 up x 81.25), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:05:13 CEST | 10:05:13 UTC | S17 not running -> relaunch 3/200 |
| 12:05:13 CEST | 10:05:13 UTC | rate: window senders 1300 tx/s total (17 up x 76.471), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:05:16 CEST | 10:05:16 UTC | S18 not running -> relaunch 3/200 |
| 12:05:16 CEST | 10:05:16 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:10:00 CEST | 10:10:00 UTC | BOT BLOCK: session up, runners 18, disk 32.9 GB, n2 synced true utxoindex false lag 0.2 s mempool 7993, bot sub/acc 1023.9/1014.8 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 101.7 tx/s (7/9 valid), miner 1, mining share 23.76%, dup share 0.2578 |
| 12:14:52 CEST | 10:14:52 UTC | RAMP EVAL 11:59-12:14 CEST at 1300 tx/s: sub/acc 168.9/168.1 tx/s, acc/sub 99.48%, rejects 0% (+0 transport), RAM min 2.21 GB, CPU avg 42.2% -> NOT clean (3 node-dead events; submitted 168.9 < 90% of 1300); rate stays 1300 (not clean but no overload (node-dead/stall noise): hold) |
| 12:14:52 CEST | 10:14:52 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:15:20 CEST | 10:15:20 UTC | live summary: pushed logs/bot/SUMMARY.md (e31a148) |
| 12:16:24 CEST | 10:16:24 UTC | watchdog: scheduler not running -> (re)start |
| 12:16:24 CEST | 10:16:24 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 12:16:24 CEST | 10:16:24 UTC | n2 first read: synced true, utxoindex false, sink lag 0.2 s, DAA 593794922 |
| 12:16:24 CEST | 10:16:24 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:20:00 CEST | 10:20:00 UTC | BOT BLOCK: session up, runners 18, disk 32.3 GB, n2 synced true utxoindex false lag 0.2 s mempool 13383, bot sub/acc 1296.4/1294.8 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3130.6 tx/s (9/9 valid), miner 1, mining share 32.35%, dup share 0.2425 |
| 12:29:54 CEST | 10:29:54 UTC | tailLines read error (eval input): RangeError [ERR_OUT_OF_RANGE]: The value of "position" is out of range. It must be an integer. Received 3526892.5 |
| 12:29:54 CEST | 10:29:54 UTC | RAMP EVAL 12:14-12:29 CEST at 1300 tx/s: sub/acc 209/209 tx/s, acc/sub 100%, rejects 0% (+0 transport), RAM min 1.78 GB, CPU avg 42.6% -> NOT clean (submitted 209 < 90% of 1300); rate stays 1300 (not clean but no overload (node-dead/stall noise): hold) |
| 12:29:54 CEST | 10:29:54 UTC | rate: window senders 1300 tx/s total (18 up x 72.222), fees 400/600 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:30:01 CEST | 10:30:01 UTC | BOT BLOCK: session up, runners 18, disk 31.7 GB, n2 synced true utxoindex false lag 0.6 s mempool 10869, bot sub/acc 1286.9/1286.7 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3221.9 tx/s (9/9 valid), miner 1, mining share 32.02%, dup share 0.2198 |
| 12:30:09 CEST | 10:30:09 UTC | S17 not running -> relaunch 4/200 |
| 12:30:10 CEST | 10:30:10 UTC | live summary: pushed logs/bot/SUMMARY.md (a559cd8) |
| 12:31:09 CEST | 10:31:09 UTC | watchdog: scheduler not running -> (re)start |
| 12:31:09 CEST | 10:31:09 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 12:31:09 CEST | 10:31:09 UTC | n2 first read: synced true, utxoindex false, sink lag 0.3 s, DAA 593803766 |
| 12:31:09 CEST | 10:31:09 UTC | re-eval of the 12:14-12:29 CEST window: the 12:29 eval read only part of the sender files (non-integer read offset in tailLines, fixed 12:33 CEST; the 11:15/11:44/12:14/12:29 evals undercounted submitted) |
| 12:31:09 CEST | 10:31:09 UTC | day-watch: S17 degraded (high RSS/latency, ~50 sub/s) -> SIGKILL+relaunch with fresh pub picks; MemAvailable recovered ~1.8->2.7 GB; rate hold 1300 |
| 12:31:10 CEST | 10:31:10 UTC | RAMP EVAL 12:14-12:29 CEST at 1300 tx/s: sub/acc 1291.9/1291.5 tx/s, acc/sub 99.97%, rejects 0% (+0 transport), RAM min 1.78 GB, CPU avg 42.6% -> clean; rate 1300 -> 1430 |
| 12:31:10 CEST | 10:31:10 UTC | DEVIATION: fee-change 400/600 -> 560/840 (stp 11:49 CEST: +40% at next climb; above GO cap 600, deviation); cap 840, node-quote-skip stays 400 |
| 12:31:10 CEST | 10:31:10 UTC | fee-change 400/600 -> 560/840 (stp 11:49 CEST: +40% at next climb; above GO cap 600, deviation); cap 840, node-quote-skip stays 400 |
| 12:31:10 CEST | 10:31:10 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:38:32 CEST | 10:38:32 UTC | S4 not running -> relaunch 6/200 |
| 12:38:32 CEST | 10:38:32 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:38:35 CEST | 10:38:35 UTC | S12 not running -> relaunch 6/200 |
| 12:38:35 CEST | 10:38:35 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:40:00 CEST | 10:40:00 UTC | BOT BLOCK: session up, runners 18, disk 31.2 GB, n2 synced true utxoindex false lag 0.2 s mempool 10558, bot sub/acc 1394.4/1396.5 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3287.7 tx/s (10/10 valid), miner 1, mining share 32.47%, dup share 0.2691 |
| 12:44:18 CEST | 10:44:18 UTC | S17 not running -> relaunch 5/200 |
| 12:44:18 CEST | 10:44:17 UTC | day-watch: S17 degraded again (avg ~54 sub/s vs 79.4 target, zeros in last 60s, RSS spikes to ~775 MB, lat_max ~2.2 s) -> SIGKILL+relaunch with fresh pub picks; MemAvailable was ~1.2-1.6 GB (near/under 1.5 floor); rate hold 1430 |
| 12:44:56 CEST | 10:44:56 UTC | RAMP EVAL 12:29-12:44 CEST at 1430 tx/s: sub/acc 1389.1/1388.4 tx/s, acc/sub 99.95%, rejects 0% (+436 transport), RAM min 1.1 GB, CPU avg 48% -> NOT clean (box RAM min 1.1 GB < 1.5); rate stays 1430 (not clean but no overload (node-dead/stall noise): hold) |
| 12:44:56 CEST | 10:44:56 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:45:19 CEST | 10:45:19 UTC | live summary: pushed logs/bot/SUMMARY.md (f9be819) |
| 12:46:00 CEST | 10:46:40 UTC | day-watch 12:46: S17 post-relaunch still soft-degraded (~54 sub/s, RSS~690); agg ~1390-1400 near 1430; MemAvailable ~1.5-1.7G; rate hold 1430; no second kill; no stop |
| 12:47:47 CEST | 10:47:47 UTC | launch held: MemAvailable 1474 MB < 1500 (no sender launch while RAM is low) |
| 12:47:47 CEST | 10:47:47 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:47:48 CEST | 10:47:48 UTC | S6 not running -> relaunch 6/200 |
| 12:47:48 CEST | 10:47:48 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:47:51 CEST | 10:47:51 UTC | S9 not running -> relaunch 7/200 |
| 12:47:51 CEST | 10:47:51 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:49:09 CEST | 10:49:09 UTC | S3 not running -> relaunch 6/200 |
| 12:49:09 CEST | 10:49:09 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:49:12 CEST | 10:49:12 UTC | S8 not running -> relaunch 6/200 |
| 12:49:12 CEST | 10:49:12 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:49:15 CEST | 10:49:15 UTC | S17 not running -> relaunch 6/200 |
| 12:49:15 CEST | 10:49:15 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:00 CEST | 10:50:00 UTC | BOT BLOCK: session up, runners 18, disk 30.5 GB, n2 synced true utxoindex false lag 0.2 s mempool 13344, bot sub/acc 1369.8/1370.3 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3371.7 tx/s (9/9 valid), miner 1, mining share 31.65%, dup share 0.2531 |
| 12:50:14 CEST | 10:50:14 UTC | S5 not running -> relaunch 6/200 |
| 12:50:15 CEST | 10:50:15 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:17 CEST | 10:50:17 UTC | S2 not running -> relaunch 6/200 |
| 12:50:17 CEST | 10:50:17 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:27 CEST | 10:50:27 UTC | S6 not running -> relaunch 7/200 |
| 12:50:27 CEST | 10:50:27 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:29 CEST | 10:50:29 UTC | rate: window senders 1430 tx/s total (14 up x 102.143), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:30 CEST | 10:50:30 UTC | S10 not running -> relaunch 6/200 |
| 12:50:30 CEST | 10:50:30 UTC | rate: window senders 1430 tx/s total (15 up x 95.333), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:33 CEST | 10:50:33 UTC | S13 not running -> relaunch 6/200 |
| 12:50:33 CEST | 10:50:33 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:36 CEST | 10:50:36 UTC | S14 not running -> relaunch 6/200 |
| 12:50:36 CEST | 10:50:36 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:39 CEST | 10:50:39 UTC | S17 not running -> relaunch 7/200 |
| 12:50:39 CEST | 10:50:39 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:50:59 CEST | 10:50:59 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:51:00 CEST | 10:51:00 UTC | S12 not running -> relaunch 7/200 |
| 12:51:00 CEST | 10:51:00 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:53:05 CEST | 10:53:05 UTC | S8 not running -> relaunch 7/200 |
| 12:53:05 CEST | 10:53:05 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:53:08 CEST | 10:53:08 UTC | launch held: MemAvailable 1424 MB < 1500 (no sender launch while RAM is low) |
| 12:53:08 CEST | 10:53:08 UTC | rate: window senders 1430 tx/s total (15 up x 95.333), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:53:10 CEST | 10:53:10 UTC | S12 not running -> relaunch 8/200 |
| 12:53:10 CEST | 10:53:10 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:53:15 CEST | 10:53:15 UTC | S14 not running -> relaunch 7/200 |
| 12:53:15 CEST | 10:53:15 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:53:21 CEST | 10:53:21 UTC | S15 not running -> relaunch 6/200 |
| 12:53:21 CEST | 10:53:21 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:54:49 CEST | 10:54:49 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:54:50 CEST | 10:54:50 UTC | S8 not running -> relaunch 8/200 |
| 12:54:50 CEST | 10:54:50 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:54:59 CEST | 10:54:59 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:01 CEST | 10:55:01 UTC | S15 not running -> relaunch 7/200 |
| 12:55:01 CEST | 10:55:01 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:03 CEST | 10:55:03 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:04 CEST | 10:55:04 UTC | S11 not running -> relaunch 6/200 |
| 12:55:04 CEST | 10:55:04 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:11 CEST | 10:55:11 UTC | S16 not running -> relaunch 4/200 |
| 12:55:11 CEST | 10:55:11 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:19 CEST | 10:55:19 UTC | S5 not running -> relaunch 7/200 |
| 12:55:19 CEST | 10:55:19 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:22 CEST | 10:55:22 UTC | S10 not running -> relaunch 7/200 |
| 12:55:22 CEST | 10:55:22 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:23 CEST | 10:55:23 UTC | rate: window senders 1430 tx/s total (13 up x 110), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:25 CEST | 10:55:25 UTC | S1 not running -> relaunch 6/200 |
| 12:55:26 CEST | 10:55:26 UTC | rate: window senders 1430 tx/s total (14 up x 102.143), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:29 CEST | 10:55:29 UTC | S3 not running -> relaunch 7/200 |
| 12:55:29 CEST | 10:55:29 UTC | rate: window senders 1430 tx/s total (15 up x 95.333), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:32 CEST | 10:55:32 UTC | S12 not running -> relaunch 9/200 |
| 12:55:32 CEST | 10:55:32 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:55:35 CEST | 10:55:35 UTC | S14 not running -> relaunch 8/200 |
| 12:55:35 CEST | 10:55:35 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:56:05 CEST | 10:56:05 UTC | S11 not running -> relaunch 7/200 |
| 12:56:05 CEST | 10:56:05 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:57:11 CEST | 10:57:11 UTC | S7 not running -> relaunch 6/200 |
| 12:57:23 CEST | 10:57:23 UTC | S5 not running -> relaunch 8/200 |
| 12:57:23 CEST | 10:57:23 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:57:25 CEST | 10:57:25 UTC | rate: window senders 1430 tx/s total (14 up x 102.143), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:57:26 CEST | 10:57:26 UTC | S15 not running -> relaunch 8/200 |
| 12:57:26 CEST | 10:57:26 UTC | rate: window senders 1430 tx/s total (15 up x 95.333), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:57:29 CEST | 10:57:29 UTC | S16 not running -> relaunch 5/200 |
| 12:57:29 CEST | 10:57:29 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:57:32 CEST | 10:57:32 UTC | S18 not running -> relaunch 4/200 |
| 12:57:32 CEST | 10:57:32 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:58:12 CEST | 10:58:12 UTC | S7 not running -> relaunch 7/200 |
| 12:58:12 CEST | 10:58:12 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 12:59:53 CEST | 10:59:53 UTC | RAMP EVAL 12:44-12:59 CEST at 1430 tx/s: sub/acc 1346.8/1348.8 tx/s, acc/sub 100%, rejects 0% (+209 transport), RAM min 1.01 GB, CPU avg 54.8% -> NOT clean (box RAM min 1.01 GB < 1.5); rate stays 1430 (not clean but no overload (node-dead/stall noise): hold) |
| 12:59:53 CEST | 10:59:53 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:00:00 CEST | 11:00:00 UTC | BOT BLOCK: session up, runners 18, disk 29.8 GB, n2 synced true utxoindex false lag 0.4 s mempool 14215, bot sub/acc 1338.2/1339.5 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3225.3 tx/s (9/9 valid), miner 1, mining share 32.16%, dup share 0.2609 |
| 13:00:10 CEST | 11:00:10 UTC | live summary: pushed logs/bot/SUMMARY.md (06490d0) |
| 13:07:34 CEST | 11:07:34 UTC | S17 not running -> relaunch 8/200 |
| 13:07:33 CEST | 11:07:33 UTC | day-watch: S17 degraded again (avg ~41 sub/s vs 79.4 target, zeros in last ~60s, RSS spikes to ~771 MB, lat_max ~3.2 s, lanes_nocoin 8) -> SIGKILL pid - + storm relaunch with fresh pub picks; MemAvailable 1540->2268 MB; rate hold 1430 |
| 13:23:39 CEST | 11:23:39 UTC | n2 unhealthy under pubMode (not synced, utxoindex off, sink lag 886.6 s > 60): senders KEEP submitting on public nodes (stp 16:19) |
| 13:23:40 CEST | 11:23:40 UTC | RAMP EVAL 13:08-13:23 CEST at 1430 tx/s: sub/acc 21.3/21.1 tx/s, acc/sub 99.43%, rejects 0% (+0 transport), RAM min 1.35 GB, CPU avg 45.9% -> NOT clean (submitted 21.3 < 90% of 1430; box RAM min 1.35 GB < 1.5); rate stays 1430 (not clean but no overload (node-dead/stall noise): hold) |
| 13:23:40 CEST | 11:23:40 UTC | S1 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S2 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S3 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S4 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | public node boson-10.kaspa.red: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 13:23:40 CEST | 11:23:40 UTC | S5 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S6 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S7 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main boson-10.kaspa.red -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S8 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S9 stalled: 0 ok submits in 45 s (2 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S10 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S11 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S12 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S13 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | public node muon-10.kaspa.blue: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 13:23:40 CEST | 11:23:40 UTC | S14 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main muon-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | public node neutrino-10.kaspa.stream: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 13:23:40 CEST | 11:23:40 UTC | S15 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | public node vector-10.kaspa.green: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 13:23:40 CEST | 11:23:40 UTC | S16 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main vector-10.kaspa.green -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | S17 stalled: 0 ok submits in 45 s (0 sec rows), 0 accepts in 60 s, erroring nodes [], main - -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | public node electron-10.kaspa.blue: 3 stall strikes in 10 min -> relaunch picks avoid it |
| 13:23:40 CEST | 11:23:40 UTC | S18 stalled: 0 ok submits in 45 s (1 sec rows), 0 accepts in 60 s, erroring nodes [], main electron-10.kaspa.blue -> SIGKILL pid -, relaunch now with fresh picks |
| 13:23:40 CEST | 11:23:40 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:23:40 CEST | 11:23:40 UTC | BOT BLOCK: session up, runners 18, disk 29.1 GB, n2 synced false utxoindex false lag 886.6 s mempool 14283, bot sub/acc 0/0 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted not measured tx/s (0/0 valid), miner 1, mining share -%, dup share - |
| 13:23:41 CEST | 11:23:41 UTC | S1 not running -> relaunch 7/200 |
| 13:23:41 CEST | 11:23:41 UTC | rate: window senders 1430 tx/s total (11 up x 130), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:23:44 CEST | 11:23:44 UTC | S2 not running -> relaunch 7/200 |
| 13:23:47 CEST | 11:23:47 UTC | S3 not running -> relaunch 8/200 |
| 13:23:51 CEST | 11:23:51 UTC | S4 not running -> relaunch 7/200 |
| 13:23:54 CEST | 11:23:54 UTC | S5 not running -> relaunch 9/200 |
| 13:23:57 CEST | 11:23:57 UTC | S6 not running -> relaunch 8/200 |
| 13:23:57 CEST | 11:23:57 UTC | live summary: pushed logs/bot/SUMMARY.md (d4db361) |
| 13:24:00 CEST | 11:24:00 UTC | S7 not running -> relaunch 8/200 |
| 13:24:03 CEST | 11:24:03 UTC | S8 not running -> relaunch 9/200 |
| 13:24:06 CEST | 11:24:06 UTC | S9 not running -> relaunch 8/200 |
| 13:24:09 CEST | 11:24:09 UTC | FREEZE start: n2 virtual DAA not moving for 30 s (>= 30 s) (lag 916.7 s) |
| 13:24:09 CEST | 11:24:09 UTC | S10 not running -> relaunch 8/200 |
| 13:24:12 CEST | 11:24:12 UTC | S11 not running -> relaunch 8/200 |
| 13:24:15 CEST | 11:24:15 UTC | S12 not running -> relaunch 10/200 |
| 13:24:15 CEST | 11:24:15 UTC | rate: window senders 1430 tx/s total (12 up x 119.167), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:24:18 CEST | 11:24:18 UTC | S13 not running -> relaunch 7/200 |
| 13:24:18 CEST | 11:24:18 UTC | rate: window senders 1430 tx/s total (13 up x 110), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:24:21 CEST | 11:24:21 UTC | S14 not running -> relaunch 9/200 |
| 13:24:21 CEST | 11:24:21 UTC | rate: window senders 1430 tx/s total (14 up x 102.143), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:24:24 CEST | 11:24:24 UTC | S15 not running -> relaunch 9/200 |
| 13:24:24 CEST | 11:24:24 UTC | rate: window senders 1430 tx/s total (15 up x 95.333), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:24:27 CEST | 11:24:27 UTC | S16 not running -> relaunch 6/200 |
| 13:24:27 CEST | 11:24:27 UTC | rate: window senders 1430 tx/s total (16 up x 89.375), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:24:30 CEST | 11:24:30 UTC | S17 not running -> relaunch 9/200 |
| 13:24:30 CEST | 11:24:30 UTC | rate: window senders 1430 tx/s total (17 up x 84.118), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:24:33 CEST | 11:24:33 UTC | S18 not running -> relaunch 5/200 |
| 13:24:33 CEST | 11:24:33 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:24:39 CEST | 11:24:39 UTC | miner OFF: n2 not synced for 60 s |
| 13:25:29 CEST | 11:25:29 UTC | n2 kaspad restarted (new process, uptime 1 s) |
| 13:25:42 CEST | 11:25:42 UTC | FREEZE end: length 124 s, n2 lag 1010.2 s |
| 13:25:51 CEST | 11:25:51 UTC | node-restart: n2 DAA frozen ~16m lag~986s -> start-n2.sh pid - (GO freeze rule) |
| 13:26:05 CEST | 11:26:05 UTC | miner ON (1 box CPU kaspa-miner, 1 thread, n2 gRPC): n2 synced again / process relaunch |
| 13:29:53 CEST | 11:29:53 UTC | RAMP EVAL 13:14-13:29 CEST at 1430 tx/s: sub/acc 543.8/540.8 tx/s, acc/sub 99.43%, rejects 0% (+0 transport), RAM min 1.38 GB, CPU avg 56.4% -> NOT clean (5 node-dead events; submitted 543.8 < 90% of 1430; box RAM min 1.38 GB < 1.5); rate stays 1430 (not clean but no overload (node-dead/stall noise): hold) |
| 13:29:53 CEST | 11:29:53 UTC | rate: window senders 1430 tx/s total (18 up x 79.444), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:30:00 CEST | 11:30:00 UTC | BOT BLOCK: session up, runners 18, disk 28.2 GB, n2 synced true utxoindex false lag 0.3 s mempool 13442, bot sub/acc 832.3/827.1 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3583.1 tx/s (1/3 valid), miner 1, mining share 8.74%, dup share 0.2703 |
| 13:30:25 CEST | 11:30:25 UTC | live summary: pushed logs/bot/SUMMARY.md (5369453) |
| 13:33:34 CEST | 11:33:34 UTC | S14 stalled: 0 ok submits in 45 s (44 sec rows), 1 accepts in 60 s, erroring nodes [], main neutrino-10.kaspa.stream -> SIGKILL pid -, relaunch now with fresh picks |
| 13:33:35 CEST | 11:33:35 UTC | S14 not running -> relaunch 10/200 |
| 13:40:00 CEST | 11:40:00 UTC | BOT BLOCK: session up, runners 18, disk 27.5 GB, n2 synced true utxoindex false lag 0.3 s mempool 12611, bot sub/acc 1360.1/1359.1 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3432.6 tx/s (10/10 valid), miner 1, mining share 31.65%, dup share 0.2814 |
| 13:44:55 CEST | 11:44:55 UTC | RAMP EVAL 13:29-13:44 CEST at 1430 tx/s: sub/acc 1361.7/1361.2 tx/s, acc/sub 99.96%, rejects 0% (+0 transport), RAM min 1.83 GB, CPU avg 56.6% -> clean; rate 1430 -> 1573 |
| 13:44:55 CEST | 11:44:55 UTC | rate: window senders 1573 tx/s total (18 up x 87.389), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 13:45:14 CEST | 11:45:14 UTC | live summary: pushed logs/bot/SUMMARY.md (e967164) |
| 13:50:00 CEST | 11:50:00 UTC | BOT BLOCK: session up, runners 18, disk 26.6 GB, n2 synced true utxoindex false lag 0.4 s mempool 13574, bot sub/acc 1422.3/1421.1 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3454.8 tx/s (9/9 valid), miner 1, mining share 34.12%, dup share 0.2889 |
| 13:59:52 CEST | 11:59:52 UTC | RAMP EVAL 13:44-13:59 CEST at 1573 tx/s: sub/acc 1459.7/1459.2 tx/s, acc/sub 99.97%, rejects 0% (+0 transport), RAM min 1.39 GB, CPU avg 61.6% -> NOT clean (box RAM min 1.39 GB < 1.5); rate stays 1573 (not clean but no overload (node-dead/stall noise): hold) |
| 13:59:52 CEST | 11:59:52 UTC | rate: window senders 1573 tx/s total (18 up x 87.389), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 14:00:00 CEST | 12:00:00 UTC | BOT BLOCK: session up, runners 18, disk 26 GB, n2 synced true utxoindex false lag 0.7 s mempool 17088, bot sub/acc 1448.1/1446.3 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3431.9 tx/s (9/9 valid), miner 1, mining share 33.17%, dup share 0.3018 |
| 14:00:25 CEST | 12:00:25 UTC | live summary: pushed logs/bot/SUMMARY.md (b425637) |
| 14:02:27 CEST | 12:02:27 UTC | S8 not running -> relaunch 10/200 |
| 14:04:05 CEST | 12:04:05 UTC | S9 not running -> relaunch 9/200 |
| 14:06:26 CEST | 12:06:26 UTC | S1 not running -> relaunch 8/200 |
| 14:06:32 CEST | 12:06:32 UTC | S2 not running -> relaunch 8/200 |
| 14:06:38 CEST | 12:06:38 UTC | S3 not running -> relaunch 9/200 |
| 14:06:44 CEST | 12:06:44 UTC | S4 not running -> relaunch 8/200 |
| 14:06:50 CEST | 12:06:50 UTC | S5 not running -> relaunch 10/200 |
| 14:06:56 CEST | 12:06:56 UTC | S6 not running -> relaunch 9/200 |
| 14:07:02 CEST | 12:07:02 UTC | S7 not running -> relaunch 9/200 |
| 14:07:07 CEST | 12:07:07 UTC | S8 not running -> relaunch 11/200 |
| 14:07:10 CEST | 12:07:10 UTC | S17 not running -> relaunch 10/200 |
| 14:07:13 CEST | 12:07:13 UTC | S9 not running -> relaunch 10/200 |
| 14:07:19 CEST | 12:07:19 UTC | S10 not running -> relaunch 9/200 |
| 14:07:26 CEST | 12:07:26 UTC | S11 not running -> relaunch 9/200 |
| 14:07:32 CEST | 12:07:32 UTC | S12 not running -> relaunch 11/200 |
| 14:07:32 CEST | 12:07:32 UTC | day-watch: S17 soft-degrade SIGKILL pid - (rss~776MB, ~37 sub/s, nocoin 9) -> storm relaunch 10/200 pid -; MemAvail ~1.2->2.4 GB; rate hold 1573 |
| 14:07:38 CEST | 12:07:38 UTC | S13 not running -> relaunch 8/200 |
| 14:07:44 CEST | 12:07:44 UTC | S14 not running -> relaunch 11/200 |
| 14:07:50 CEST | 12:07:50 UTC | S15 not running -> relaunch 10/200 |
| 14:07:56 CEST | 12:07:56 UTC | S16 not running -> relaunch 7/200 |
| 14:08:02 CEST | 12:08:02 UTC | rate: window senders 1573 tx/s total (17 up x 92.529), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 14:08:08 CEST | 12:08:08 UTC | S18 not running -> relaunch 6/200 |
| 14:08:11 CEST | 12:08:11 UTC | S17 not running -> relaunch 11/200 |
| 14:08:11 CEST | 12:08:11 UTC | rate: window senders 1573 tx/s total (18 up x 87.389), fees 560/840 [no-signature hop, anyone-can-spend, not realistic payments] |
| 14:08:39 CEST | 12:08:39 UTC | watchdog: scheduler not running -> (re)start |
| 14:08:40 CEST | 12:08:40 UTC | DEVIATION: fee x2 to 1120/1680 by stp 12:05Z (deviation: above GO cap 600); cap 1680, node-quote-skip 400 -> 1680 so our own fee does not make senders sit out; fired 2026-10-11T12:08:40.013Z |
| 14:08:40 CEST | 12:08:40 UTC | fee x2 to 1120/1680 by stp 12:05Z (deviation: above GO cap 600); cap 1680, node-quote-skip 400 -> 1680 so our own fee does not make senders sit out; fired 2026-10-11T12:08:40.013Z |
| 14:08:40 CEST | 12:08:40 UTC | DEVIATION: rate held high to END by stp 12:06Z; Build same (deviation: no -5% on unclean/overload windows; only coins running out may lower; floor = current level 1573) |
| 14:08:40 CEST | 12:08:40 UTC | rate held high to END by stp 12:06Z; Build same (deviation: no -5% on unclean/overload windows; only coins running out may lower; floor = current level 1573) |
| 14:08:40 CEST | 12:08:40 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 12:30 UTC; node n2 (own private node, loopback) |
| 14:08:40 CEST | 12:08:40 UTC | n2 first read: synced true, utxoindex false, sink lag 0.2 s, DAA 593862236 |
| 14:08:40 CEST | 12:08:40 UTC | rate: window senders 1573 tx/s total (18 up x 87.389), fees 1120/1680 [no-signature hop, anyone-can-spend, not realistic payments] |
| 14:10:00 CEST | 12:10:00 UTC | BOT BLOCK: session up, runners 18, disk 25.1 GB, n2 synced true utxoindex false lag 0.3 s mempool 11381, bot sub/acc 1458.3/1454.7 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 3222.7 tx/s (9/9 valid), miner 1, mining share 33.34%, dup share 0.2869 |
| 14:14:23 CEST | 12:14:23 UTC | watchdog: scheduler not running -> (re)start |
| 14:14:23 CEST | 12:14:23 UTC | DEVIATION: END extended +1h to 13:30Z by stp 12:13Z, same fees and pace (1120/1680, rate held high, no cuts); miner off, loggers and chain count shift +1 h (count 13:30-15:30Z covers 06:30-13:30Z) |
| 14:14:23 CEST | 12:14:23 UTC | scheduler restarted (resume by clock) pid -; T0 07:30 UTC, gates 07:00/07:20 UTC, end 13:30 UTC; node n2 (own private node, loopback) |
| 14:14:23 CEST | 12:14:23 UTC | n2 first read: synced true, utxoindex false, sink lag 0.6 s, DAA 593865777 |
| 14:14:23 CEST | 12:14:23 UTC | rate: window senders 1573 tx/s total (18 up x 87.389), fees 1120/1680 [no-signature hop, anyone-can-spend, not realistic payments] |
| 14:14:53 CEST | 12:14:53 UTC | RAMP EVAL 13:59-14:14 CEST at 1573 tx/s: sub/acc 1425.1/1422 tx/s, acc/sub 99.79%, rejects 0% (+3 transport), RAM min 1.24 GB, CPU avg 62.1% -> NOT clean (box RAM min 1.24 GB < 1.5); rate stays 1573 (not clean but no overload (node-dead/stall noise): hold) |
| 14:14:53 CEST | 12:14:53 UTC | rate: window senders 1573 tx/s total (18 up x 87.389), fees 1120/1680 [no-signature hop, anyone-can-spend, not realistic payments] |
| 14:15:33 CEST | 12:15:33 UTC | live summary: loop started (pid -): write every 10 min, push every 15 min from G1 to END+15 min |
| 14:15:41 CEST | 12:15:41 UTC | live summary: pushed logs/bot/SUMMARY.md (10963a1) |
| 14:20:00 CEST | 12:20:00 UTC | BOT BLOCK: session up, runners 18, disk 24.4 GB, n2 synced true utxoindex false lag 0.2 s mempool 549, bot sub/acc 1423.5/1424.4 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2780.9 tx/s (9/9 valid), miner 1, mining share 30.61%, dup share 0.4042 |
| 14:29:56 CEST | 12:29:56 UTC | RAMP EVAL 14:14-14:29 CEST at 1573 tx/s: sub/acc 1438.8/1438.4 tx/s, acc/sub 99.97%, rejects 0% (+2 transport), RAM min 1.51 GB, CPU avg 59.1% -> clean; rate 1573 -> 1730 |
| 14:29:56 CEST | 12:29:56 UTC | rate: window senders 1730 tx/s total (18 up x 96.111), fees 1120/1680 [no-signature hop, anyone-can-spend, not realistic payments] |
| 14:30:00 CEST | 12:30:00 UTC | BOT BLOCK: session up, runners 18, disk 23.6 GB, n2 synced true utxoindex false lag 0.3 s mempool 2285, bot sub/acc 1410.8/1410.4 tx/s (no-signature hop, anyone-can-spend, not realistic payments), n2 unique accepted 2717.6 tx/s (9/9 valid), miner 1, mining share 32.15%, dup share 0.4079 |
| 14:30:12 CEST | 12:30:12 UTC | live summary: pushed logs/bot/SUMMARY.md (b713240) |
| 14:33:14 CEST | 12:33:14 UTC | live summary: loop ended |
| 14:33:14 CEST | 12:33:14 UTC | HALT (stop.sh): watchdog, scheduler, senders (SIGKILL), miner stopped; n2 and loggers untouched |
| 14:36:03 CEST | 12:36:03 UTC | live loggers (n2mon, chain) stopped after the halt minute 12:33Z |
| 14:36:30 CEST | 12:36:30 UTC | COUNT: chain recount on n2 starting (window 2026-10-11T06:30:00Z - 2026-10-11T12:34:00Z, before pruning) |
| 14:37:17 CEST | 12:37:17 UTC | COUNT failed or timed out (see out/recount.log); live chain-1m stays the count |
| 14:37:27 CEST | 12:37:27 UTC | end clock read (HTTP Date method) |
| 14:37:33 CEST | 12:37:33 UTC | repo log files written to out/logs-bot |
| 14:37:36 CEST | 12:37:36 UTC | xlsx written (run-2026-10-11.xlsx) |
| 14:41:12 CEST | 12:41:12 UTC | COUNT retry 2 (try 1 lost n2: kaspad OOM-killed during the walk, guard relaunched it; n2 synced again) |
