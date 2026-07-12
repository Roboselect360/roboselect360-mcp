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
