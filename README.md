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

Connect any MCP-compatible client (Claude Desktop, Cursor, custom agents) and query the catalogue directly.

---

## Quickstart (free tier)

1. **Get a free key** at [roboselect360.com/en/contact.html](https://roboselect360.com/en/contact.html) - the "Get started for free" section. You'll receive a key starting with `rbs_` (no card, no credits consumed).
2. **Point your MCP client** at the server:
   - Endpoint: `https://mcp-free.roboselect360.com/mcp`
   - Header: `X-API-Key: rbs_your_key_here`

   Clients typically connect through [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) (requires [Node.js](https://nodejs.org)):

   ```bash
   npx -y mcp-remote https://mcp-free.roboselect360.com/mcp --header "X-API-Key: rbs_your_key_here"
   ```

See [QUICKSTART.md](./QUICKSTART.md) for a ready-to-paste Claude Desktop config (Windows & macOS) and [examples/](./examples/) for sample calls.

---

## What the free tier gives you

The free tier exposes **9 PUBLIC tools** - the robot catalogue, specs and system status across the three teardown layers:

- `*_list_robots` - list the 34 robots
- `*_get_robot` - full commercial profile of one robot
- `*_get_system_status` - dataset coverage and freshness

(where `*` is `hardware_`, `mechanical_` or `software_`).

**Premium** unlocks the deep layers - BOM teardowns, dependency profiles, geopolitical / critical-material risk analysis and cross-robot comparison (**27 tools** across the three layers). Premium is provisioned on request: email **contact@roboselect360.com** or visit [roboselect360.com/en](https://roboselect360.com/en). Your existing `rbs_` key can serve for everything.

---

## Also available

- **REST API** - `https://api.roboselect360.com` (same `X-API-Key`)
- **Website & datasheets** - [roboselect360.com/en](https://roboselect360.com/en)

## License

Example code in this repository is released under the [MIT License](./LICENSE). The RoboSelect360 dataset, scoring methodology and teardown analyses are proprietary and are **not** included here - they are served through the API.

---

*RoboSelect360 - independent humanoid robot intelligence.*
