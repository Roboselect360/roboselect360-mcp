# Examples

Sample interactions with the RoboSelect360 free MCP tier (9 PUBLIC tools).

These are natural-language prompts you can give an MCP-enabled agent; the agent
picks the right tool automatically.

---

### List the catalogue

> "List all the humanoid robots RoboSelect360 tracks."

Calls `hardware_list_robots` -> returns the 34 robots with id, name and tier.

---

### Get one robot's profile

> "Show me the full profile of the Unitree G1."

Calls `hardware_get_robot` with the robot id -> commercial specs, pricing,
availability, viability score.

---

### Check dataset coverage

> "What data does RoboSelect360 have, and how fresh is it?"

Calls `hardware_get_system_status` -> number of robots profiled, layers
covered, last update.

---

### Compare across layers (free vs premium)

The free tier answers the *commercial* questions above across the hardware,
mechanical and software catalogues (`hardware_*`, `mechanical_*`, `software_*`).

Deeper questions - "what chips are in this robot and where are they made?",
"what's the critical-material risk of its actuators?", "compare the supply-chain
risk of these two robots" - require a **premium** key and unlock the teardown
and dependency-profile tools. See the main [README](../README.md).

---

## Prompts to try in Claude Desktop

Once connected (see [QUICKSTART](../QUICKSTART.md)), paste any of these into a chat:

**Catalogue & specs (free)**

- "List all the humanoid robots tracked by RoboSelect360."
- "Show me the full profile of the Unitree G1."
- "What's the price and key specs of the Agility Digit?"
- "What's the viability score of the Figure 02?"
- "What data does RoboSelect360 have, and how fresh is it?"

**Compare robots (free - commercial data only)**

- "Compare the price, payload and viability score of the Unitree G1 and the Agility Digit."
- "Which robots are commercially available, and how do their viability scores compare?"

**Premium-only (these are refused on the free tier - expected, not a bug)**

- "Compare the Unitree G1 across the hardware, mechanical and software teardowns."
- "Give me the semiconductor BOM teardown of the Agility Digit."
- "Compare the supply-chain risk of the Unitree G1 and the Figure 02."

A polite `403` / "reserved for premium" on the premium-only prompts confirms the
free restriction is working as intended.

Deeper questions - "what chips are in this robot and where are they made?",
"what's the critical-material risk of its actuators?", "compare the supply-chain
risk of these two robots" - require a **premium** key and unlock the teardown
and dependency-profile tools. See the main [README](../README.md).
