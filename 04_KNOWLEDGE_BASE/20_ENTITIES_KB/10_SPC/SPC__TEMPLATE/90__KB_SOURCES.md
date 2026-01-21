# 90__KB_SOURCES — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/90__KB_SOURCES.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (source registry)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.SOURCES.001
OWNER: SYSTEM
ROLE: Canonical source registry template for any SPC pack (provenance + refresh).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial KB sources template for SPC Pro Packs."
- REASON: "Ensure provenance for borrowed concepts and prevent untracked imports."
- IMPACT: "When external sources are used, they must be registered here."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.SOURCES.001

---

## PURPOSE (LAW)
Этот документ хранит **реестр источников** (внешних или внутренних), если:
- ты переносишь метод/правило/термины из внешнего материала,
- используешь стандарты/гайдлайны как основу,
- опираешься на конкретный документ как авторитет.

> RULES:
- Не копировать большие фрагменты текста.
- Фиксировать только: что взяли, где, когда, и как это влияет на пак.
- Если источников нет — оставить пустой список и отметку “NONE”.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## SOURCE RECORD CONTRACT (MUST USE THIS SHAPE)
### FIELDS
- SOURCE_UID: <unique>
- TYPE: WEB | PAPER | BOOK | INTERNAL_DOC | TOOL_DOC | OTHER
- TITLE: <name>
- AUTHOR/ORG: <author or organization>
- DATE_ACCESSED: <yyyy-mm-dd>
- AUTHORITY_TIER: A | B | C (A = primary/official, B = reputable secondary, C = weak/needs caution)
- SCOPE_USED: <what part of the pack it supports>
- EXTRACTED_POINTS:
  - <point_1>
  - <point_2>
- LIMITS / CAVEATS:
  - <what might be wrong / conditions>
- REFRESH_POLICY:
  - INTERVAL: <e.g., 180d>
  - TRIGGER: <when to re-check>
- LINKS (NAV ONLY):
  - RAW: <raw link or url if internal raw exists>

---

## SOURCES
### SOURCE_UID: NONE
- NOTE: No external sources are used in this pack template.

---

## OPTIONAL: INTERNAL CANON SOURCES (UID-ONLY)
> Если ты хочешь указывать “внутренние канон-доки”, делай это UID-only.

- <UID_1> — <why referenced>
- <UID_2> — <why referenced>

---
END
