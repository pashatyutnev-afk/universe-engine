# 🗺️ WORLD STRUCTURE ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · WORLD TOPOLOGY · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__WORLD_STRUCTURE_ENG.md
- ENGINE_ID: L2-DOM-WORLD-STRUCTURE-ENGINE-001
- UID: UE.ENT.ENG.DOM.WORLD.WORLD_STRUCTURE
- NAME: World Structure Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Topology, Realms, Locations, Factions & Connectivity
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for structural validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> If space is undefined, movement and causality cannot be trusted.

---

## 1. PURPOSE

World Structure Engine defines the **layout and connectivity** of the world.

It guarantees:
- explicit world scope (what exists / what does not)
- structural layers (regions, realms, zones, systems)
- location graph (nodes + edges)
- access and travel constraints
- faction territories and control zones
- choke points and strategic hubs

This engine is the “map brain” of the world.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define world scope and layers (planet, station, multi-world, etc.)
- Define location nodes (places) and edges (connections)
- Define travel modes and constraints (time/cost/risk)
- Define borders, territories, controlled zones
- Define hubs, choke points, forbidden zones
- Provide structure artifacts to geopolitics/economy/conflict engines
- Detect structural gaps (unreachable nodes, infinite travel, missing hubs)

### OUT-OF-SCOPE (FORBIDDEN)
- Defining physics/magic laws (World Law Engine)
- Defining history/epochs (Timeline & Epoch Engine)
- Defining culture/institutions (Civilization Engine)
- Defining conflicts (Conflict & Power Engine)
- Canon authority decisions (Governance)

---

## 3. STRUCTURE MODEL

### 3.1 Core Objects
- WORLD_SCOPE: boundary of existence (what’s included)
- LAYERS: hierarchy of spaces (realm → region → zone → site)
- LOCATION_NODE: place with properties
- CONNECTION_EDGE: link between places (route/gate/road/warp)
- ACCESS_RULE: who can enter/when/why
- TERRITORY: faction control region
- HUB: high-connectivity node
- CHOKE_POINT: strategic narrow passage
- FRONTIER: unstable border region

### 3.2 Edge Types (fixed)
- ROAD/LAND
- SEA_ROUTE
- AIR_ROUTE
- SPACE_ROUTE
- GATE/PORTAL
- SECRET_PASSAGE
- DIGITAL_CHANNEL (if virtual layers exist)

### 3.3 Constraints Fields (recommended)
- travel_time_range
- travel_cost
- travel_risk_level (LOW/MEDIUM/HIGH)
- visibility (public/hidden/secret)
- access (open/restricted/forbidden)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — WORLD_STRUCTURE_REQUEST
**REQUIRED FIELDS**
- `ws_id`
- `timestamp`
- `scope_description` (one paragraph)
- `world_scale` (local/continental/planetary/multi-world)
- `primary_layers` (list)
- `faction_seed_list` (optional)
- `travel_modes_allowed` (list)
- `constraints_refs` (genre/realism/project constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — WORLD_STRUCTURE_GRAPH
**REQUIRED FIELDS**
- `ws_id`
- `world_scope`
- `layers` (hierarchy)
- `location_nodes` (list: {node_id, name, layer, tags, properties})
- `connection_edges` (list: {edge_id, from, to, type, constraints})
- `territories` (list: {territory_id, faction_id, nodes_included})
- `hubs` (list of node_id with reason)
- `choke_points` (list of edge/node with reason)
- `frontiers` (optional list)
- `unreachable_nodes` (auto-detected)
- `structure_risks` (auto-detected: infinite travel, missing links, etc.)
- `trace_id` (if provided)

### 5.2 OUTPUT — WORLD_STRUCTURE_VERDICT
- `ws_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_SCOPE_AND_LAYERS
- OP_02: BUILD_LOCATION_NODE_SET
- OP_03: BUILD_CONNECTION_GRAPH
- OP_04: ASSIGN_TERRITORIES_AND_CONTROL
- OP_05: DETECT_HUBS_CHOKEPOINTS_UNREACHABLES
- OP_06: EMIT_WORLD_STRUCTURE_GRAPH

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Geopolitics Engine (actors move on structure)
- Economy & Resource Engine (flows follow edges)
- Conflict & Power Engine (frontlines/chokepoints)
- Timeline & Epoch Engine (place history anchors)
- Scene Construction Engine (location constraints)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Project constraints (scale, genre, realism)
- Travel modes allowed

### FORBIDDEN
- Infinite connectivity without cost (teleport-everywhere world)
- Locations without edges unless intentionally isolated (must be flagged)
- Treating structure graph as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No layers
- No connections (world cannot function)
- Majority of nodes unreachable with no narrative reason
- Travel has no time/cost/risk constraints (movement meaningless)
- Territories exist with no faction mapping

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add edges, add constraints, define hubs, clarify scope.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to downstream world artifacts

---

## 11. NON-GOALS
- Does not define laws of physics/magic
- Does not define history
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Structure is the skeleton of the world.
Without it, everything floats.

---

**STATUS:** World Structure Engine v1.0  
**DOMAIN:** ACTIVE
