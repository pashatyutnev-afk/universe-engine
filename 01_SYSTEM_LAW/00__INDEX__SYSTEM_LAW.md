# SYSTEM LAW INDEX — MASTER REGISTRY (CANON)

FILE: 01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
SCOPE: Universe Engine (All volumes)
LAYER: 01_SYSTEM_LAW
DOC_TYPE: INDEX
INDEX_TYPE: MASTER_LAW_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.1
UID: UE.IDX.LAW.SYSTEM_LAW.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all system-level laws (RAW-only navigation, no guessing).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "DOC CONTROL compliance: header formatted, STATUS set to ACTIVE, UID normalized, forbidden FINAL RULE meta-duplication removed, content reformatted."
- REASON: "Index must be auditable and executable as registry under RAW-only runtime; meta duplication is forbidden."
- IMPACT: "SYSTEM LAW layer becomes deterministic for navigation/existence; no hidden drift."
- CHANGE_ID: UE.CHG.2026-01-20.LAW.INDEX.002

---

## 0) PURPOSE (LAW)
This INDEX is the single source of truth for **NAV + EXISTENCE** of layer `01_SYSTEM_LAW`.

It defines:
- which law files exist in this layer;
- strict authority order for law application;
- RAW-only canonical navigation;
- anti-duplication and enforcement rules.

---

## 1) EXISTENCE RULE (ABSOLUTE)
- If a law is **not registered here** — it **does not exist** for SYSTEM LAW.
- If a file exists but is **not registered here** — it is **NON-CANON / ignored**.
- Navigation works **only via RAW links** (PATH is a label only).

---

## 2) ORDER OF AUTHORITY (PRIORITY)
0) `00__SYSTEM_LAW.md`  
1) `04__CANON_PROTOCOL.md`  
2) `03__VERSIONING_CHANGE_POLICY.md`  
3) `02__UID_RULES.md`  
4) `01__NAMING_RULES.md`  
5) `06__CONSTRAINTS_REGISTRY.md`  
6) `05__ARTIFACT_SCHEMA_REGISTRY.md`  
7) `07__PIPELINE_REGISTRY.md`

---

## 3) NO-EXTRA-LAWS RULE (ABSOLUTE)
No additional LAW files are allowed in `01_SYSTEM_LAW/` beyond this canon map.

Allowed non-LAW files in the folder:
- this INDEX file (`00__INDEX__SYSTEM_LAW.md`);
- pure POINTER aliases (redirect only, **no rules**) to canonical targets.

Any extra LAW-like file found in the folder must be:
- removed, OR
- converted into a pure POINTER to an existing canonical file (no extra rules inside).

---

## 4) ENFORCEMENT (MANDATORY)

### 4.1 Mandatory checks
- All listed RAW links must be valid.
- No duplicate entrypoints for SYSTEM LAW exist (SoT enforced).
- No unregistered file is treated as LAW authority.

### 4.2 Fail conditions
- Any missing/invalid RAW link.
- Any additional LAW file present without pointer conversion.
- Any attempt to treat an unregistered file as authoritative.

### 4.3 Fix procedure
- Restore/update RAW links.
- Delete extra files OR convert to pure POINTER.
- Register new law only via canon protocol (never ad-hoc).

---

## 5) CANON MAP — SYSTEM LAW FILES (RAW-ONLY NAV)

### 00 — System Law (Core)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

### 01 — Naming Rules
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

### 02 — UID Rules
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

### 03 — Versioning & Change Policy
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

### 04 — Canon Protocol
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

### 05 — Artifact Schema Registry
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

### 06 — Constraints Registry
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

### 07 — Pipeline Registry
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

---

## 6) CHANGE CONTROL (REMINDER)
This index is the only SoT for SYSTEM LAW existence and navigation.
Any change must follow Canon Protocol and be logged via CHANGE_NOTE/CHANGE_ID.

--- END.
