# RoboSelect360 - Humanoid Robot Intelligence (MCP)

**Supply-chain and teardown intelligence for 34 humanoid robots, available as an [MCP](https://modelcontextprotocol.io) server.**

RoboSelect360 is an independent six-layer analysis platform covering the humanoid robotics market:

| Layer | What it covers |
|---|---|
| Commercial | Specs, pricing, availability, viability scoring for 34 robots |
| Semiconductors | Chip-level BOM teardown + geopolitical dependency risk |
| Mechanical | Actuators, bearings, magnets - BOM + critical-material risk |
| Software | Stack, licensing, jurisdiction, lock-in and export-control risk |
| Regulatory | CE / AI Act / Cyber Resilience Act due-diligence *(in progress)* |
| Reports | Automated buyer-side TCO reports |

Connect an MCP-compatible client and query the catalogue directly. **Claude Desktop is the tested path today** - see [Client support](#client-support) below.

---

## Quickstart (free tier)

1. **Get a free key** at [roboselect360.com/en/contact.html](https://roboselect360.com/en/contact.html) - the "Get started for free" section. You'll receive a key starting with `rbs_` (no card, no credits consumed).
2. **Connect your client** - two ways:

   **Claude Desktop (fastest)** - download [`roboselect360-free.mcpb`](https://github.com/Roboselect360/roboselect360-mcp/releases/latest) from the latest release, open it, and paste your key when prompted. No config file to edit.

   **Other MCP clients** (untested, see below) - point them at the server:
   - Endpoint: `https://mcp-free.roboselect360.com/mcp`
   - Header: `X-API-Key: rbs_your_key_here`

   These clients typically connect through [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) (requires [Node.js](https://nodejs.org)):

   ```bash
   npx -y mcp-remote https://mcp-free.roboselect360.com/mcp --header "X-API-Key: rbs_your_key_here"
   ```

See [QUICKSTART.md](./QUICKSTART.md) for both paths step by step (Windows & macOS) and [examples/](./examples/) for sample calls.

### Client support

**Claude Desktop is the only client we have tested so far**, on Windows and macOS.

The `.mcpb` bundle is a Claude Desktop extension format, so that path is specific to it. The server itself is standard MCP over Streamable HTTP, so other MCP clients may work using the endpoint and header above - we have not verified any of them. If you get it running elsewhere, tell us at **contact@roboselect360.com** and we will document it.

---

## What the free tier gives you

The free tier exposes **9 PUBLIC tools** - the robot catalogue, specs and system status across the three teardown layers:

- `*_list_robots` - list the 34 robots
- `*_get_robot` - full commercial profile of one robot
- `*_get_system_status` - dataset coverage and freshness

(where `*` is `hardware_`, `mechanical_` or `software_`).

**Premium** unlocks the deep layers - BOM teardowns, dependency profiles, geopolitical / critical-material risk analysis and cross-robot comparison (**27 tools** across the three layers). Premium is provisioned on request: email **contact@roboselect360.com** or visit [roboselect360.com/en](https://roboselect360.com/en). For MCP you receive **access credentials (an ID and a secret)** for the premium endpoint - not an `rbs_` key. If you also use the REST API, a premium `rbs_` key comes with it. Both channels draw on a single shared credit balance.

If you were already using the free connector, **remove it when you install the premium one**. Both expose the same tool names, and running them side by side leaves your client unable to tell which one to call.

---

## Also available

- **REST API** - `https://api.roboselect360.com` (same `X-API-Key`)
- **Website & datasheets** - [roboselect360.com/en](https://roboselect360.com/en)

## License

Example code in this repository is released under the [MIT License](./LICENSE). The RoboSelect360 dataset, scoring methodology and teardown analyses are proprietary and are **not** included here - they are served through the API.

---

*RoboSelect360 - independent humanoid robot intelligence.*
