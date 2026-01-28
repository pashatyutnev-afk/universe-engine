# TOPICS REALM — README (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.REALM.001
OWNER: SYSTEM
ROLE: Orientation for KB Topics realm: what Topics are, how entities must use them, scope boundaries per subrealm, and how taxonomy works (not navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created Topics realm README: purpose, usage order, subrealms, and taxonomy guidance without creating a second navigation authority."
- REASON: "Topics are the universal knowledge library; entities must load minimal relevant topics deterministically."
- IMPACT: "Cleaner scope selection, fewer mixed-domain modules, and more consistent output quality."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.README.001

---

## 0) PURPOSE (KB)
`10_TOPICS` is the domain knowledge library for the Knowledge Base.

Topics provide:
- craft knowledge (how to do things well)
- operational heuristics (labeled)
- common failure modes and fixes
- checklists/gates where possible

Topics are used by entities to improve output quality.

---

## 1) WHAT TOPICS ARE / ARE NOT
### TOPICS ARE
- domain modules (narrative/character/world/visual/sound/production/marketing/meta/reference)
- reusable knowledge units for competence packs and run execution

### TOPICS ARE NOT
- navigation authority (no RAW registry here)
- governance laws (that lives in `00_KB_GOVERNANCE`)
- a dumping ground for random links

---

## 2) NAVIGATION RULE (STRICT)
- The ONLY KB navigation/existence authority is:
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- This README and taxonomy files are orientation tools.
- Do not add RAW link registries here.

---

## 3) REQUIRED USAGE ORDER (DETERMINISTIC)
Any KB-driven work should follow:
1) Governance minimum set (rules/xref/rel/trace discipline).
2) Scope selection (which subrealm(s) apply).
3) Load minimal topic modules required for the task.
4) Apply checklists/gates.
5) Emit RUN_TRACE (UID-only sources + memory reuse flag).

---

## 4) SUBREALMS (WHAT LIVES INSIDE 10_TOPICS)
- 10_NARRATIVE: scene craft, causality, tension, structure tools
- 20_CHARACTER: motivation, trauma, values, pressure behavior, arcs
- 30_WORLD: constraints, lore consistency, tech level impacts
- 40_VISUAL: composition, shot grammar, lighting principles, continuity, shotlists
- 50_SOUND_MUSIC: songwriting, arrangement, vocals, mix/master, music QA
- 60_PRODUCTION: pipelines, handoffs, readiness, asset sets
- 70_MARKETING: positioning, packaging, distribution, growth loops
- 80_META: execution methods, drift control, QA consistency workflows
- 90_REFERENCE: glossaries, dictionaries, quick references, disambiguation

Rule:
- Keep knowledge in the correct subrealm; do not mix domains inside one module.

---

## 5) TOPIC TAXONOMY (HOW WE NAME AND TAG)
Two layers:
1) File placement (subrealm folder) defines the primary domain.
2) Skill tags / labels (inside modules) allow cross-domain referencing.

Naming principles:
- keep file names descriptive and atomic
- one topic = one craft function
- avoid “mega topics”

---

## 6) QUALITY RULES FOR TOPIC MODULES
A good topic module should include:
- purpose
- scope boundary (covers/excludes)
- actionable guidance (not only theory)
- failure modes and fixes
- mini checklist or measurable gate when feasible
- UID-only RELATED references

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- topics become a second navigation index (RAW registries)
- governance rules are written inside topic modules
- modules mix multiple domains without split
- invented facts are presented as KB-backed truth
- topic modules become long “courses” without operational structure

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: governance rules define hard boundaries for KB usage
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: trace discipline for KB-driven runs
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical skill tag taxonomy (when available)

--- END.
