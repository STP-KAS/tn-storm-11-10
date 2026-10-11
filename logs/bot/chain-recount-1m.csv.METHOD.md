> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Method sidecar: kept next to the CSV so the CSV itself stays plain (header row first) for parsers.

# Method: chain-recount-1m.csv (11 Oct 2026)

| | |
|---|---|
| **One row** | one recount span, 06:43Z to 12:33Z; usually one UTC minute, `span_min` > 1 when minutes are lumped |
| **Timezone** | UTC (`minute_utc`, ISO with milliseconds). CEST = UTC+2. |
| **What is counted** | `chain_blocks`: chain blocks walked in the span. `accepted_ids`: accepted transaction ids of those chain blocks. `unique_accepted` = `accepted_ids` minus one coinbase per chain block. `unique_accepted_s` = `unique_accepted` / (60 × `span_min`). All senders plus TN10 base load (about 56 tx/s). |
| **Which node** | **One node: n2** (the bot's own pruned TN10 node), read-only, right after the halt and before pruning (Kaspa Pulse's "count soon after the run"). |
| **Bucketing** | **By n2's receive time.** The walk follows n2's selected chain and cuts it at the chain tips n2 had at each UTC-minute boundary of its wall clock (tips logged live during the run, kept local). Not by block timestamp. |
| **`note`** | `merged with N later minute(s): boundary sink not on the final chain` = that boundary tip was later reorganised off the chain, so the span covers N+1 minutes. |

This is the raw source behind [chain-count.csv](chain-count.csv.METHOD.md).

Counts only: no txid, key, seed, IP, host, port or wallet address in the file. Kaspa Testnet-10 only; tKAS has no value.
