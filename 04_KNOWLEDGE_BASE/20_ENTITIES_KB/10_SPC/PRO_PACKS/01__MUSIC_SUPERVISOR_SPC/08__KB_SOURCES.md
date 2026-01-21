# 08__KB_SOURCES — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/08__KB_SOURCES.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — KB Sources
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: KB_SOURCES
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.KB_SOURCES.001
OWNER: SPC (Music Supervisor)
ROLE: Defines allowed knowledge inputs/outputs/boundaries for this pack (no fantasy, no guessing).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "KB sources initialized for Music Supervisor SPC pack."
- REASON: "Prevent hallucinated rules and uncontrolled external claims."
- IMPACT: "Locks pack to KB domains and UID-only references."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.KBSRC.001

---

## PURPOSE (LAW)
Этот файл фиксирует:
- откуда берём знания (inputs),
- что можно выдавать (outputs),
- что запрещено использовать как “истину”.

---

## KB INPUTS (ALLOWED)

### A) Entity KB (this layer)
- Domain: 04_KNOWLEDGE_BASE/20_ENTITIES_KB
- Allowed:
  - SPC Pro Packs (including this pack)
  - VAL/QA/CTL/ORC connector docs if they are referenced by UID
- Rule:
  - Use UID-only when citing policies/gates/checks.

### B) Topics KB (domain knowledge)
- Domain: 04_KNOWLEDGE_BASE/10_TOPICS
- Allowed topic realms (by intent):
  - 50_SOUND_MUSIC (supervision-level only)
  - 60_PRODUCTION (pipeline/roles/handoffs)
  - 70_MARKETING (only if task is distribution/packaging oriented)
- Not allowed:
  - topics unrelated to task scope (avoid scope creep)

### C) Pillars (high-level canon)
- Domain: 04_KNOWLEDGE_BASE/01_PILLARS
- Allowed:
  - conceptual principles that do not introduce external factual claims

---

## KB OUTPUTS (ALLOWED)
Only the pack-defined outputs:
- PRIMARY_OUTPUTS:
  - SUPERVISION_TASK_CARD
  - QUALITY_AND_ACCEPTANCE_ROUTE
- OPTIONAL_OUTPUTS (as needed):
  - POLISH_NOTES
  - EDGE_HANDLING_NOTE
- plus minimum trace blocks required by passport.

---

## BOUNDARIES (STRICT)

### B1 — No external facts without sources
- Запрещено утверждать факты “из мира” (история, статистика, право, цены, новости) без явно предоставленных источников.
- Если нужен внешний факт:
  - STOP + request source OR route to allowed web lookup policy (если он у вас существует отдельно).

### B2 — No new policies invented
- Запрещено придумывать новые “законы/правила”.
- Разрешено:
  - компоновка уже существующих правил в удобный формат
  - чеклист/гейт в рамках шаблона, если это часть пака

### B3 — No role mixing escalation
- Music Supervisor SPC не берёт на себя:
  - Prompt Architect final prompt authoring
  - Mixing engineer decisions
- Если задача требует:
  - routing note (who should handle it)

### B4 — UID-only referencing
- All internal references must be UID-only:
  - CHECKLIST_UID / GATE_UID / PLAYBOOK_UID / TOPIC_UID
- Avoid PATH links except for navigation (RAW).

---

## SOURCE RECORD FORMAT (FOR FUTURE EXPANSION)
Если вы ведёте “source records”:
- SRC_ID:
- TYPE: <kb_internal|user_provided|web>
- SCOPE:
- DATE:
- TRUST_LEVEL:
- NOTES:

(пока пусто — pack uses internal KB only)

---

## REQUIRED UID REFERENCES
- PASSPORT:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PASSPORT.001
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PRINCIPLES.001
- TOPIC BINDINGS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.TOPIC_BINDINGS.001 (to be filled)

---
END
