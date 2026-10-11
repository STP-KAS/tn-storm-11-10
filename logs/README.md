> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# logs: where the results land

| Folder | Side | Who writes it |
|---|---|---|
| [bot/](bot/README.md) | Bot (five public TN10 nodes; n2 for reads and the miner) | TN10 ops (raw logs) and tn ops2 (count, write-up) |
| [build/](build/README.md) | Build (own desk node) | Grok Build |

Same file names and columns on both sides ([go/LOGGING.md](../go/LOGGING.md)), one `window` from 09:30 to 14:30 CEST, so files join on `minute_utc` and line up with Kaspa Pulse's count. The headline, network unique accepted tx/s, is counted once from chain data, never summed. After END: `COMBINED.md` and `WRITE-UP.md` here.

## Method per file

Each per-minute CSV has a method sidecar next to it (`<file>.METHOD.md`), so the CSVs stay plain for parsers: what is counted, which node or nodes, how minutes are bucketed, timezone UTC.

| CSV | Counted on | Bucketing | Method |
|---|---|---|---|
| [bot/chain-count.csv](bot/chain-count.csv) (headline) | n2 | n2 receive time (UTC-minute boundary tips) | [METHOD](bot/chain-count.csv.METHOD.md) |
| [bot/chain-recount-1m.csv](bot/chain-recount-1m.csv) | n2 | n2 receive time | [METHOD](bot/chain-recount-1m.csv.METHOD.md) |
| [bot/minute.csv](bot/minute.csv) | bot senders; n2 for network columns | n2 receive time | [METHOD](bot/minute.csv.METHOD.md) |
| [bot/pulse-method-minute.csv](bot/pulse-method-minute.csv) | n2 and muon-10.kaspa.blue | block time | [METHOD](bot/pulse-method-minute.csv.METHOD.md) |

The two bucketings give slightly different minutes for the same chain; totals over many minutes agree. Peak minute 11:28Z: 3,583.1 tx/s by n2 receive time, 3,645.9 by block time.

Counts only. No txid, key, seed, IP, host, port or wallet address.
