> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md)

# logs: where the results land

| Folder | Side | Who writes it |
|---|---|---|
| [bot/](bot/README.md) | Bot (five public TN10 nodes; n2 for reads and the miner) | TN10 ops (raw logs) and tn ops2 (count, write-up) |
| [build/](build/README.md) | Build (own desk node) | Grok Build |

Same file names and columns on both sides ([go/LOGGING.md](../go/LOGGING.md)), one `window` from 09:30 to 14:30 CEST, so files join on `minute_utc` and line up with Kaspa Pulse's count. The headline, network unique accepted tx/s, is counted once from chain data, never summed. After END: `COMBINED.md` and `WRITE-UP.md` here.

Counts only. No txid, key, seed, IP, host, port or wallet address.
