# RoboSelect360 - Independent Humanoid Robot Intelligence (MCP)

**Independent intelligence on humanoid robots - proven capabilities, real cost, supply chain and bills of materials - available as an [MCP](https://modelcontextprotocol.io) server.**

Humanoid robots are moving from the lab to the factory, but the information needed to decide remains scattered, unverifiable or written by the manufacturers themselves. RoboSelect360 is an independent player in the humanoid robot ecosystem: it helps industrial leaders, buyers, integrators and developers move from demonstration to deployment.

| Question | What RoboSelect360 answers with |
|---|---|
| What can this robot actually do? | Observed capabilities, each backed by a dated source - failures included, manufacturer claims never taken as proof |
| What does it really cost? | Specs, pricing, availability and viability scoring; buyer-side TCO and ROI |
| What is inside, and from where? | Semiconductor, mechanical and software bills of materials, with supply-chain and geopolitical dependency risk |
| What does regulation require? | Machinery Regulation, AI Act and Cyber Resilience Act due diligence *(in progress)* |

Connect an MCP-compatible client and query the data directly - see [Client support](#client-support) below.

---

## Quickstart (free tier)

**No key, no account, no install.** Paste one address into your MCP client.

```
https://mcp.roboselect360.com/mcp
```

**Claude Desktop or claude.ai** - Settings, Connectors, Add custom connector, paste the address. Leave the OAuth fields empty. All 29 tools appear immediately: 10 answer for free, the others name the robot to buy to access them.

**Other MCP clients** - same address, no header. Clients without a connector screen can go through [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) (requires [Node.js](https://nodejs.org)):

```bash
npx -y mcp-remote https://mcp.roboselect360.com/mcp
```

A free `rbs_` key is still needed for the **REST API** (`api.roboselect360.com`, header `X-API-Key`). Request one at [roboselect360.com/en/contact.html](https://roboselect360.com/en/contact.html).

See [QUICKSTART.md](./QUICKSTART.md) for step-by-step instructions and [examples/](./examples/) for sample calls.

### Client support

**Verified with real users:** Claude (desktop and web) connects with no key, no account and no configuration file: the full connector URL is all that is required. **ChatGPT** (custom connector) and **Codex** (`codex mcp add roboselect --url https://mcp.roboselect360.com/mcp`) work the same way on the free tier. The URL must carry the `/mcp` path: the bare hostname returns 404 and the connector fails at "Connect to the server".

For paid access with an `rbs_` key, **Claude is the verified client** (key in the connector's `X-API-Key` header). Passing the key from ChatGPT or Codex has not been validated yet. **Perplexity refuses** (checked 2026-08-13): it requires OAuth with automatic client registration.

The server is standard MCP over Streamable HTTP, so any client that accepts an unauthenticated remote server should work. If you get it running elsewhere, tell us at **contact@roboselect360.com** and we will document it.

---

## What the free tier gives you

All 29 tools are listed; **10 answer without a key** - the robot catalogue, profiles and system status across the three teardown layers, plus the access manifest:

- `*_list_robots` - the full robot catalogue
- `*_get_robot` - full commercial profile of one robot
- `*_get_system_status` - dataset coverage and freshness
- `get_access_manifest` - what is open to you, and how to open the rest

(where `*` is `hardware_`, `mechanical_` or `software_`).

**Paid access** unlocks the deep layers - bill-of-materials teardowns, dependency profiles, geopolitical and critical-material risk, cross-robot comparison, and the observed capabilities of each robot. It is sold **per robot, €390 excl. VAT**, at [roboselect360.com/en/tarifs.html](https://roboselect360.com/en/tarifs.html), and opens that robot's full analysis. You receive an `rbs_` key: add it as the `X-API-Key` header of your connector, on the same address. The same key works on the REST API.

Connector headers can only be set when the connector is created: to add your key, delete the free connector and create it again with the header. Keep a single RoboSelect360 connector - two connectors expose the same tool names and leave your client unable to tell which one to call.

---

## Also available

- **REST API** - `https://api.roboselect360.com` (same `X-API-Key`)
- **Website & datasheets** - [roboselect360.com/en](https://roboselect360.com/en)

## License

Example code in this repository is released under the [MIT License](./LICENSE). The RoboSelect360 dataset, scoring methodology and teardown analyses are proprietary and are **not** included here - they are served through the API.

---

*RoboSelect360 - independent humanoid robot intelligence.*
