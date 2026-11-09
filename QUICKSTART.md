# Quickstart

## What you need

- **Claude Desktop** or **claude.ai**, **ChatGPT** (custom connector), **Codex** (`codex mcp add roboselect --url https://mcp.roboselect360.com/mcp`) or **Kimi** - all connect on the free tier. Any MCP client that accepts an unauthenticated remote server should work.
- Nothing else. No key, no account, no install.

## 1. Connect

One address:

```
https://mcp.roboselect360.com/mcp
```

In **Claude Desktop** or on **claude.ai**: Settings, Connectors, **Add custom connector**, paste the address. Leave the **OAuth client ID and secret empty** - this server does not ask for them.

All 32 tools appear immediately. 11 answer for free - the robot catalogue, profiles, availability and viability scores across the semiconductor, mechanical and software layers, plus the access manifest and `prepare_pilot`, which prepares a first humanoid robot pilot; the others name the robot to buy to access them.

### Clients without a connector screen

`npx -y mcp-remote https://mcp.roboselect360.com/mcp` (requires [Node.js](https://nodejs.org)) - free tier only. Never pass your key this way: it ends up in clear text in the client's log.

## 2. Try it

Ask your agent something like:

"List the humanoid robots available and give me the full profile of Unitree G1."

Under the hood this calls `hardware_list_robots` and `hardware_get_robot`.

See [examples/](./examples/) for more.

## Upgrading to premium

The free tier covers the catalogue, robot profiles with their observed-capability labels, and pilot preparation (`prepare_pilot`). Paid access unlocks bill-of-materials teardowns, dependency profiles, geopolitical and critical-material risk, cross-robot comparison, the observed capabilities of each robot with every dated observation, and its after-sales support profile.

Paid access is sold **per robot, €390 excl. VAT**. You receive an `rbs_` key: add it as the `X-API-Key` header of your connector, on the same address `https://mcp.roboselect360.com/mcp` (in Claude: Settings > Connectors > Add custom connector, Authentication: None, then the request header). The same key works on the REST API.

Connector headers can only be set when the connector is created: to add your key, delete the free connector and create it again with the header. Keep a single RoboSelect360 connector - two connectors expose the same tool names and leave your client unable to tell which one to call.

The pilot decision file (`build_pilot_decision_file`) opens with its own access right, separate from robot access: request it at [roboselect360.com/en/prepare-a-robot-pilot.html](https://roboselect360.com/en/prepare-a-robot-pilot.html).

Buy access to a robot at [roboselect360.com/en/tarifs.html](https://roboselect360.com/en/tarifs.html). For anything else, email **contact@roboselect360.com**.
