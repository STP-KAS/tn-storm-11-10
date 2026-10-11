> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Method sidecar: kept next to the CSV so the CSV itself stays plain (header row first) for parsers.

# Method: chain-count.csv (11 Oct 2026)

| | |
|---|---|
| **One row** | one UTC minute, 06:30Z to 12:33Z (headline window 07:30Z to the halt at 12:33:01Z) |
| **Timezone** | UTC (`minute_utc`). CEST = UTC+2. |
| **What is counted** | `network_unique_accepted`: transaction ids accepted by the virtual chain of **n2** (the bot's own pruned TN10 node), each id once, **minus one coinbase per chain block**. All senders on the network, plus TN10 base load (about 56 tx/s). `accepted_tx_per_s` = that / 60 (or / `span_min` for a lumped row). |
| **Which node** | **One node: n2.** Recounted after the halt, before pruning, from n2's selected chain (raw rows: [chain-recount-1m.csv](chain-recount-1m.csv)). Six minutes (08:26-08:29Z, 10:28-10:29Z) come from the live chain logger on n2 where the recount had a gap (`strict_source`). |
| **Bucketing** | **By n2's receive time, not block time.** At every UTC-minute boundary of n2's wall clock the logger read n2's chain tip (sink). A minute = the chain blocks between two such boundary tips. So a block lands in the minute in which n2 had it as part of its chain, typically within about 1 s of its block time. |
| **`blocks`, `our_mined_blocks`** | blocks n2 received in that minute (block-added events, by n2 receive time), and of those, blocks paying the bot's one miner |
| **Lumped rows** | if a boundary tip did not end up on the final chain, its minute merges with the next ones: `span_min` > 1, total in the first row of the span. Lumped rows count in the mean, not in the peak or median. |
| **Headline rule** | `headline_strict = yes`: single minute, at most 400 chain blocks. 171 minutes. Peak, median and mean on [COMBINED.md](../COMBINED.md). `complete_minute` is an older, looser flag. |

Why it can differ from a count by block time: a minute boundary here is n2's clock reading its tip, not block timestamps, so a few blocks near each boundary fall in the neighbouring minute. Per-minute values shift a little; totals over many minutes agree. Compare with our own block-time mirror: [pulse-method-minute.csv](pulse-method-minute.csv.METHOD.md).

Counts only: no txid, key, seed, IP, host, port or wallet address in the file. Kaspa Testnet-10 only; tKAS has no value.
