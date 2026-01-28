# 08__KB_SOURCES — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/08__KB_SOURCES.md
SCOPE: KB — SPC Pro Pack — Music Producer — KB Sources
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: KB_SOURCES
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.KB_SOURCES.001
OWNER: SPC (Music Producer)
ROLE: Allowed knowledge inputs/outputs/boundaries for producer pack (no guessing, no invented policies).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "KB sources initialized for Music Producer SPC pack."
- REASON: "Prevent hallucinated rules and uncontrolled external claims."
- IMPACT: "Locks producer pack to KB domains and UID-only references."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.KBSRC.001

---

## PURPOSE (LAW)
Фиксирует:
- откуда продюсер берёт знания (inputs),
- что имеет право выдавать (outputs),
- что запрещено использовать как “факт/истину”.

---

## KB INPUTS (ALLOWED)

### A) Entity KB
- Domain: 04_KNOWLEDGE_BASE/20_ENTITIES_KB
- Allowed:
  - SPC Pro Packs (including this pack)
  - gates/checklists/playbooks templates and standards (UID-only)
- Rule:
  - policy references must be UID-only.

### B) Topics KB (domain knowledge)
- Domain: 04_KNOWLEDGE_BASE/10_TOPICS
- Allowed by intent:
  - 50_SOUND_MUSIC (structure, hook, vocal direction, repeat guard, variants)
  - 60_PRODUCTION (roles/handoffs, QA, delivery/versioning)
  - 70_MARKETING (only if task asks packaging/distribution)

### C) Pillars
- Domain: 04_KNOWLEDGE_BASE/01_PILLARS
- Allowed:
  - conceptual principles that do not introduce external factual claims

---

## KB OUTPUTS (ALLOWED)
Only pack-defined outputs from passport:
- PRIMARY_OUTPUTS:
  - PRODUCER_TASK_CARD
  - PRODUCTION_EXEC_PLAN
- OPTIONAL_OUTPUTS:
  - VARIANTS_PLAN
  - EDGE_HANDLING_NOTE
  - POLISH_NOTES
- plus minimum trace.

---

## BOUNDARIES (STRICT)

### B1 — No external facts without sources
Запрещено утверждать внешние факты без источников.
Если нужен внешний факт:
- STOP + request source / routing note.

### B2 — No new policies invented
Запрещено придумывать новые “законы”.
Разрешено:
- компоновка существующих правил в deliverables пака.

### B3 — No engineering takeover
Продюсер не превращается в инженера микса/мастера.
Разрешено:
- test-level QA cues (читаемость, маскирование, перевод микса),
но не “рецепты настроек”.

### B4 — UID-only referencing
- checklists/gates/playbooks/topics referenced by UID-only.

---

## SOURCE RECORD FORMAT (OPTIONAL)
- SRC_ID:
- TYPE: <kb_internal|user_provided|web>
- SCOPE:
- DATE:
- TRUST_LEVEL:
- NOTES:

---

## REQUIRED UID REFERENCES
- PASSPORT:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PASSPORT.001
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- TOPIC BINDINGS:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.TOPIC_BINDINGS.001 (to be filled)

---
END
