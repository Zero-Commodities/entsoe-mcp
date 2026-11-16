<p align="center">
  <img src="logo.png" width="96" height="96" alt="entsoemcp logo">
</p>

<h1 align="center">entsoemcp</h1>

<p align="center">
  European power-market data for AI agents, over MCP.<br>
  <a href="https://entsoemcp.com">entsoemcp.com</a> ·
  <a href="https://entsoemcp.com/llms.txt">llms.txt</a> ·
  <a href="https://entsoemcp.com/coverage">coverage</a> ·
  <a href="https://entsoemcp.com/support">support</a>
</p>

Ask your AI assistant about European electricity markets and get answers from the publishers' own data: prices, load, generation by technology, cross-border flows, balancing and outages across European bidding zones, with history from 2015 for most series. It also computes capture prices and capture rates, negative-price hours, residual load, renewable share, CO₂ emissions and battery spreads.

It is one remote MCP server. There is no account and no API key, and every tool is read-only.

**This repository holds only the setup files.** The service runs at [entsoemcp.com](https://entsoemcp.com); its code is not public.

## Connect

Server URL: `https://entsoemcp.com/mcp` (streamable HTTP, no authentication)

| App | How |
|---|---|
| **Claude** (web and desktop) | Settings → Connectors → **Add custom connector**. Paste the server URL and leave the advanced settings empty. |
| **ChatGPT** | Settings → Apps → Advanced settings → turn on **Developer mode**. Then **Create app**, paste the server URL and set Authentication to **No Auth**. |
| **Claude Code** | `claude mcp add --transport http entsoe-mcp https://entsoemcp.com/mcp`, or install the [plugin](#claude-code-plugin). |
| **Cursor** | [Add to Cursor](https://cursor.com/en/install-mcp?name=entsoe-mcp&config=eyJ1cmwiOiJodHRwczovL2VudHNvZW1jcC5jb20vbWNwIn0=), or paste [`mcp.json`](mcp.json) into `~/.cursor/mcp.json`. |
| **VS Code** | [Install in VS Code](https://insiders.vscode.dev/redirect/mcp/install?name=entsoe-mcp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fentsoemcp.com%2Fmcp%22%7D), or copy [`.vscode/mcp.json`](.vscode/mcp.json) into your project. |
| **Gemini CLI** | `gemini extensions install https://github.com/Zero-Commodities/entsoe-mcp` |
| **Perplexity, Microsoft Copilot Studio, Mistral Le Chat** | Click-by-click steps on [entsoemcp.com](https://entsoemcp.com/#connect). |

Clients that read an `mcpServers` block with a `url` take [`mcp.json`](mcp.json) as it is:

```json
{
  "mcpServers": {
    "entsoe-mcp": {
      "type": "http",
      "url": "https://entsoemcp.com/mcp"
    }
  }
}
```

### Claude Code plugin

```
/plugin marketplace add Zero-Commodities/entsoe-mcp
/plugin install entsoe-mcp@entsoemcp
```

## Try asking

- "How many negative-price hours did Spain have each month this year?"
- "What was the solar capture rate in Germany in 2025?"
- "How much did wind and solar generate in Germany last week?"
- "What share of Poland's generation was renewable last month?"
- "Show the cross-border flows between France and Spain yesterday."

## What is in this repository

| File | For |
|---|---|
| [`mcp.json`](mcp.json) | Cursor and other clients that read an `mcpServers` block |
| [`.vscode/mcp.json`](.vscode/mcp.json) | VS Code |
| [`.mcp.json`](.mcp.json), [`.claude-plugin/`](.claude-plugin) | Claude Code: the plugin and its marketplace |
| [`gemini-extension.json`](gemini-extension.json) | Gemini CLI |
| [`logo.svg`](logo.svg), [`logo.png`](logo.png) | The logo |

## Data and licences

The data comes from the ENTSO-E Transparency Platform, Elexon, NESO, Elia, Energinet, the Low Carbon Contracts Company and the Baltic Transparency Dashboard. Each publisher's terms, and the attribution it asks for, are on [entsoemcp.com/licensing](https://entsoemcp.com/licensing). entsoemcp is not affiliated with any of the data publishers.

The [MIT licence](LICENSE) covers the files in this repository only. It does not cover the service or the data.

## Support

Issues are switched off here, so that everything reaches one inbox. Email [support@entsoemcp.com](mailto:support@entsoemcp.com), or see [entsoemcp.com/support](https://entsoemcp.com/support).

[Terms](https://entsoemcp.com/terms) · [Privacy](https://entsoemcp.com/privacy) · [Imprint](https://entsoemcp.com/imprint)
