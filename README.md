# AuraMatrix MCP server

What AI compute costs, inside your AI assistant: list prices of language-model APIs per channel and GPU rental prices per provider,
each with its source and the time it was observed. Coverage: the United States and China.

- **Server URL:** `https://auramatrix.ai/mcp` (Streamable HTTP, remote)
- **No install, no API key, no account.**
- Setup page with one-click buttons: <https://auramatrix.ai/connect?ref=github-mcp>

This repository holds the connection files only (the server itself is hosted). The data is open under CC BY 4.0 at
[auramatrix-price-data](https://github.com/dadaobear-glitch/auramatrix-price-data).

## Connect

| Client | How |
|---|---|
| Claude Code | `claude mcp add --transport http auramatrix https://auramatrix.ai/mcp` |
| Cursor | [Add to Cursor](https://auramatrix.ai/prices/v1/go?to=cursor&ref=github-mcp), or put `{"mcpServers":{"auramatrix":{"url":"https://auramatrix.ai/mcp"}}}` in `.cursor/mcp.json` |
| VS Code | [Add to VS Code](https://auramatrix.ai/prices/v1/go?to=vscode&ref=github-mcp), or `{"servers":{"auramatrix":{"type":"http","url":"https://auramatrix.ai/mcp"}}}` in `.vscode/mcp.json` |
| Claude (web, desktop) | Settings → Connectors → Add custom connector → `https://auramatrix.ai/mcp` |
| Anything else | Any client that speaks Streamable HTTP: give it the URL above |

## Ask it

- Where is Claude Opus 5.5 cheapest? Give me the source.
- I send 20M input and 4M output tokens a day. What does that cost on three flagship models?
- What does an H100 cost on demand at each provider right now?
- Which models changed price this week?
- I was quoted $2.10 per hour for H100s on a one-year contract. Is that good?

## Tools

Ten tools only read. One, `share_price`, stores a price, and only after the user explicitly agrees.

- `list_models`: models with official input and output price and the lowest-priced channel
- `get_price`: one model on every channel, with region, plans, trust status and source
- `compare_channels`: channels for one model, sorted by price, with the difference from the official price
- `cheapest`: models ordered by their lowest input price
- `price_changes`: observed and vendor-announced price changes
- `estimate_cost`: cost of one request from token counts and the channel's billing rules
- `gpu_prices`: GPU rental prices per provider (on demand, spot, reserved, marketplace)
- `price_index`: token price indices by tier and GPU-hour reference prices (trial)
- `measured_performance`: measured time to first token, output speed, answer rate, charge against list price
- `check_price`: is a token price or a GPU quote the user was given a good one, against the prices on record
- `share_price`: adds a price the user pays, anonymously and only with their explicit consent, to the benchmark of what buyers pay

## What the numbers are

List prices as published, not invoices. Every answer names the channel or provider, the observation time and the source page.
Currencies are never converted. A missing price is unknown, not free. How the data is collected and checked:
<https://auramatrix.ai/prices/methodology?ref=github-mcp>. Privacy: <https://auramatrix.ai/account-data?ref=github-mcp>.

Contact: hello@auramatrix.ai
