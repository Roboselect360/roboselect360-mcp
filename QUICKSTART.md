# Quickstart

## What you need

- **Claude Desktop** - the only client we have tested so far (Windows and macOS). Other MCP clients should work through Option B, but none has been verified yet.
- A free key starting with `rbs_` (Step 1 below).
- **For the manual setup only (Option B):** [Node.js](https://nodejs.org) (LTS version) - the connection tool `mcp-remote` runs on it.

## 1. Get a free key

Go to [roboselect360.com/en/contact.html](https://roboselect360.com/en/contact.html), fill in the **"Get started for free"** section with your email, then click the confirmation link you receive. Your `rbs_` key is delivered immediately - no manual review.

The free key works for **both** the MCP server and the REST API.

## 2. Connect

Two ways. Option A is the fastest if you use Claude Desktop; Option B works with any client.

### Option A - One-click bundle (Claude Desktop)

1. Download **[`roboselect360-free.mcpb`](https://github.com/Roboselect360/roboselect360-mcp/releases/latest)** from the latest release.
2. Open the file. Claude Desktop picks it up and shows its extension installer. If double-clicking does nothing, open Claude Desktop, go to **Settings > Extensions**, choose **install from file**, and select the `.mcpb`.
3. Paste your `rbs_` key when prompted, then enable the extension.

The connector and its dependencies ship inside the bundle, so there is no config file to edit and no download on first launch.

### Option B - Manual configuration

Use this for Claude Desktop if you prefer not to install the bundle, or for any other MCP client. Clients other than Claude Desktop are untested at this stage.

The server speaks **Streamable HTTP** at:

```
https://mcp-free.roboselect360.com/mcp
```

Authenticate with the header `X-API-Key: rbs_...`.

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
        "https://mcp-free.roboselect360.com/mcp",
        "--header",
        "X-API-Key: rbs_your_key_here"
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
        "https://mcp-free.roboselect360.com/mcp",
        "--header",
        "X-API-Key: rbs_your_key_here"
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
