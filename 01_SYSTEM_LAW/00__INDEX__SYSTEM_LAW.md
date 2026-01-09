# SYSTEM LAW INDEX — MASTER REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: INDEX
INDEX_TYPE: MASTER_LAW_REGISTRY
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.2.0
UID: UE.DOC.IDX.LAW.MASTER
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all system-level laws (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Rebuilt SYSTEM LAW master index as executable registry: RAW-only canon map, strict existence rule, authority order, no-extra-laws rule, and enforcement."
- REASON: "Layer requires deterministic navigation and strict existence enforcement; prevents silent drift and duplicate law entrypoints."
- IMPACT: "SYSTEM LAW becomes fully navigable and audit-compatible; any unregistered law files are treated as non-canon."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.INDEX.001

---

## 0) PURPOSE (LAW)
This INDEX is the single source of truth for NAV/EXISTENCE of layer `01_SYSTEM_LAW`.

It defines:
- which law files exist in this layer
- strict authority order for law application
- RAW-only canonical navigation
- anti-duplication and enforcement rules

---

## 1) EXISTENCE RULE (ABSOLUTE)
- If a law is not registered here — it does not exist for SYSTEM LAW.
- If a file exists but is not registered here — NON-CANON / ignored.
- NAV works only via RAW links (PATH is a label only).

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
- No additional law files are allowed in `01_SYSTEM_LAW/` beyond this canon map.
- Any extra files found in the folder must be:
  - removed, OR
  - converted into a pure POINTER to an existing canonical file (no extra rules inside).

---

## 4) ENFORCEMENT (MANDATORY)
### 4.1 MANDATORY CHECKS
- All listed RAW links must be valid.
- No duplicate entrypoints for SYSTEM LAW exist (SoT enforced).
- No unregistered file is treated as LAW authority.

### 4.2 FAIL CONDITIONS
- Any missing/invalid RAW link.
- Any additional law file present without pointer conversion.
- Any attempt to treat an unregistered file as authoritative.

### 4.3 FIX PROCEDURE
- Restore/update RAW links.
- Delete extra files OR convert to pure POINTER.
- Register new law only via canon protocol (never ad-hoc).

---

## 5) CANON MAP — SYSTEM LAW FILES (RAW-ONLY NAV)

00 — System Law (Core)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

01 — Naming Rules  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

02 — UID Rules  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

03 — Versioning & Change Policy  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

04 — Canon Protocol  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

05 — Artifact Schema Registry  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

06 — Constraints Registry  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

07 — Pipeline Registry  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

---

## FINAL RULE (LOCK)
This index is the only SoT for SYSTEM LAW existence and navigation.  
Any change must follow canon protocol and be logged.

OWNER: SYSTEM
LOCK: FIXED

--- END.
