# Quickstart

## What you need

- **Claude Desktop** or **claude.ai** - the only client where the connection succeeds today (Windows and macOS). Any MCP client that accepts an unauthenticated remote server should work.
- Nothing else. No key, no account, no install.
- **For the manual setup only:** [Node.js](https://nodejs.org) (LTS version) - the connection tool `mcp-remote` runs on it.

## 1. Connect

One address:

```
https://mcp-free.roboselect360.com/mcp
```

In **Claude Desktop** or on **claude.ai**: Settings, Connectors, **Add custom connector**, paste the address. Leave the **OAuth client ID and secret empty** - this server does not ask for them.

The nine free tools appear immediately: the 34-robot catalogue, availability and viability scores, across the semiconductor, mechanical and software layers.

### Manual configuration

For clients without a connector screen. The server speaks **Streamable HTTP** and needs no authentication.

For Claude Desktop, add this to your `claude_desktop_config.json`:

#### macOS

```json
{
  "mcpServers": {
    "roboselect360-free": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp-free.roboselect360.com/mcp"
      ]
    }
  }
}
```

#### Windows

Use `cmd` as the command:

```json
{
  "mcpServers": {
    "roboselect360-free": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "-y",
        "mcp-remote",
        "https://mcp-free.roboselect360.com/mcp"
      ]
    }
  }
}
```

**Quit Claude Desktop completely** (not just the window - close it from the taskbar / menu bar too), then reopen it. You should see the RoboSelect360 tools appear. First launch may take ~30 s while `mcp-remote` downloads.

## 3. Try it

Ask your agent something like:

"List the humanoid robots available and give me the full profile of Unitree G1."

Under the hood this calls `hardware_list_robots` and `hardware_get_robot`.

See [examples/](./examples/) for more.

## Upgrading to premium

The free tier is PUBLIC-only (catalogue + specs). Premium unlocks BOM teardowns, dependency profiles, geopolitical / critical-material risk analysis and cross-robot comparison (27 tools).

For MCP you receive **access credentials (an ID and a secret)** for the premium endpoint - not an `rbs_` key. If you also use the REST API, a premium `rbs_` key comes with it, and both channels draw on a single shared credit balance.

If you were already using the free connector, **remove it when you install the premium one**. Both expose the same tool names, and running them side by side leaves your client unable to tell which one to call.

To request premium access, email **contact@roboselect360.com** or visit [roboselect360.com/en](https://roboselect360.com/en).
