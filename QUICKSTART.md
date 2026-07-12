# Quickstart

## What you need

- **[Node.js](https://nodejs.org)** installed (LTS version) - the connection tool `mcp-remote` runs on it.
- An MCP-compatible client (Claude Desktop, Cursor, or your own agent).
- A free key starting with `rbs_` (Step 1 below).

## 1. Get a free key

Go to [roboselect360.com/en/contact.html](https://roboselect360.com/en/contact.html), fill in the **"Get started for free"** section with your email, then click the confirmation link you receive. Your `rbs_` key is delivered immediately - no manual review.

The free key works for **both** the MCP server and the REST API.

## 2a. Connect from Claude Desktop

Add this to your `claude_desktop_config.json`:

### macOS

```json
{
  "mcpServers": {
    "roboselect360-free": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp-free.roboselect360.com/mcp",
        "--header",
        "X-API-Key: rbs_your_key_here"
      ]
    }
  }
}
```

### Windows

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
        "https://mcp-free.roboselect360.com/mcp",
        "--header",
        "X-API-Key: rbs_your_key_here"
      ]
    }
  }
}
```

**Quit Claude Desktop completely** (not just the window - close it from the taskbar / menu bar too), then reopen it. You should see the RoboSelect360 tools appear. First launch may take ~30 s while `mcp-remote` downloads.

## 2b. Connect from any MCP client

The server speaks **Streamable HTTP** at:

```
https://mcp-free.roboselect360.com/mcp
```

Authenticate with the header `X-API-Key: rbs_...`.

## 3. Try it

Ask your agent something like:

> "List the humanoid robots available and give me the full profile of Unitree G1."

Under the hood this calls `hardware_list_robots` and `hardware_get_robot`.

See [examples/](./examples/) for more.

## Upgrading to premium

The free tier is PUBLIC-only (catalogue + specs). Premium unlocks BOM teardowns, dependency profiles, geopolitical / critical-material risk analysis and cross-robot comparison (27 tools). To request premium access, email **contact@roboselect360.com** or visit [roboselect360.com/en](https://roboselect360.com/en).
