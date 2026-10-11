> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Method sidecar: kept next to the CSV so the CSV itself stays plain (header row first) for parsers.

# Method: pulse-method-minute.csv (11 Oct 2026, bot side)

The CSV carries its own method in `#` comment lines at the top (written live). This sidecar repeats it for parsers that cannot skip comments: read it with `comment='#'` (pandas) or skip lines starting with `#`.

| | |
|---|---|
| **One row** | one UTC minute, 10:49Z (first full minute; monitoring started 10:48Z / 12:48 CEST) to 12:33Z (halt minute, partial); a closing `#` line at the bottom |
| **Timezone** | UTC (`utc_minute`), CEST copy in `cest_minute` |
| **What is counted** | transactions **accepted in blocks**, unique ids per node per minute, minus one coinbase per chain block. All senders plus TN10 base load (about 56 tx/s). |
| **Which nodes** | **two independent nodes:** `node_a` = n2 (the bot's own pruned TN10 node), `node_b` = muon-10.kaspa.blue (public TN10 node). `diff` = node_a − node_b. |
| **Bucketing** | **By block time:** the timestamp of the accepting chain block, not the time a node received it |
| **Block columns** | `net_blocks_blue` / `net_blocks_red`: blocks merged by the selected chain that minute (accepted / not accepted), as seen on node_a |
| **Miner columns** | `our_blocks`: blocks paying the bot's one miner, by n2 receive time; `our_found`, `our_hashrate`: the miner's own log |

This is our own live mirror of the "accepted in blocks, two independent nodes, per UTC minute, by block time" method (Kaspa Pulse's method, [credits](https://github.com/STP-KAS/tn10-storm-2026-10-10/blob/main/credits/KASPA-PULSE.md)). Earlier minutes of the run exist only in [chain-count.csv](chain-count.csv.METHOD.md).

Counts only: no txid, key, seed, IP, host, port or wallet address in the file. Kaspa Testnet-10 only; tKAS has no value.
