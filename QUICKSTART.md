# Quickstart

## What you need

- **Claude Desktop** or **claude.ai**, **ChatGPT** (custom connector) or **Codex** (`codex mcp add roboselect --url https://mcp.roboselect360.com/mcp`) - all verified on the free tier. Any MCP client that accepts an unauthenticated remote server should work.
- Nothing else. No key, no account, no install.
- **For the manual setup only:** [Node.js](https://nodejs.org) (LTS version) - the connection tool `mcp-remote` runs on it.

## 1. Connect

One address:

```
https://mcp.roboselect360.com/mcp
```

In **Claude Desktop** or on **claude.ai**: Settings, Connectors, **Add custom connector**, paste the address. Leave the **OAuth client ID and secret empty** - this server does not ask for them.

All 29 tools appear immediately. 10 answer for free - the robot catalogue, profiles, availability and viability scores across the semiconductor, mechanical and software layers, plus the access manifest; the others name the robot to buy to access them.

### Manual configuration

For clients without a connector screen. The server speaks **Streamable HTTP** and needs no authentication.

For Claude Desktop, add this to your `claude_desktop_config.json`:

#### macOS

```json
{
  "mcpServers": {
    "roboselect360": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.roboselect360.com/mcp"
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
    "roboselect360": {
      "command": "cmd",
      "args": [
        "/c",
        "npx",
        "-y",
        "mcp-remote",
        "https://mcp.roboselect360.com/mcp"
      ]
    }
  }
}
```

**Quit Claude Desktop completely** (not just the window - close it from the taskbar / menu bar too), then reopen it. You should see the RoboSelect360 tools appear. First launch may take ~30 s while `mcp-remote` downloads.

## 2. Try it

Ask your agent something like:

"List the humanoid robots available and give me the full profile of Unitree G1."

Under the hood this calls `hardware_list_robots` and `hardware_get_robot`.

See [examples/](./examples/) for more.

## Upgrading to premium

The free tier covers the catalogue and robot profiles. Paid access unlocks bill-of-materials teardowns, dependency profiles, geopolitical and critical-material risk, cross-robot comparison and the observed capabilities of each robot.

Paid access is sold **per robot, €390 excl. VAT**. You receive an `rbs_` key: add it as the `X-API-Key` header of your connector, on the same address `https://mcp.roboselect360.com/mcp` (in Claude: Settings > Connectors > Add custom connector, Authentication: None, then the request header). The same key works on the REST API.

Connector headers can only be set when the connector is created: to add your key, delete the free connector and create it again with the header. Keep a single RoboSelect360 connector - two connectors expose the same tool names and leave your client unable to tell which one to call.

Buy access to a robot at [roboselect360.com/en/tarifs.html](https://roboselect360.com/en/tarifs.html). For anything else, email **contact@roboselect360.com**.
