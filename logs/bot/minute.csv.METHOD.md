> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Method sidecar: kept next to the CSV so the CSV itself stays plain (header row first) for parsers.

# Method: minute.csv (11 Oct 2026, bot side)

| | |
|---|---|
| **One row** | one UTC minute, bot side, 07:00Z to 12:33Z |
| **Timezone** | UTC (`minute_utc`). CEST = UTC+2. |
| **Sender columns** (`sent`, `submit_ok`, `rejects`, `node_accepted`) | the bot's own senders only, summed from their per-second files. `submit_ok` = taken into a public node's mempool (not accepted). `node_accepted` = the bot's own transactions seen accepted on n2's virtual chain. |
| **Network columns** (`network_unique_accepted`, `blocks`, `tx_per_block`, `our_mined_blocks`) | from the live chain logger on **n2**: unique accepted ids on n2's virtual chain (all senders plus about 56 tx/s base load), blocks n2 received that minute, accepted tx per block, and blocks paying the bot's one miner |
| **Which node** | **One node: n2** for reads and network columns; submits went to the five public TN10 nodes |
| **Bucketing** | **By n2's receive time** (n2 wall-clock UTC minute), not by block time |
| **Host columns** | CPU, RAM and disk of the box, min or max over the minute |
| **Gap rows** | `node_state = gap` (07:39-07:42Z, 08:46-08:48Z, 09:57-09:59Z box pauses; 11:09-11:22Z n2 freeze): no data, reason in `note` |

For the headline use [chain-count.csv](chain-count.csv.METHOD.md), not this file's network columns. Columns: [go/LOGGING.md](../../go/LOGGING.md#minutecsv).

Counts only: no txid, key, seed, IP, host, port or wallet address in the file. Kaspa Testnet-10 only; tKAS has no value.
