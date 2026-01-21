# 00__PACK_PASSPORT — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/00__PACK_PASSPORT.md
SCOPE: KB — SPC Pro Pack — Music Producer — Pack Passport
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: PACK_PASSPORT
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PASSPORT.001
OWNER: SPC (Music Producer)
ROLE: Canonical identity + scope boundaries + outputs + validation set for Music Producer SPC Pro Pack.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Pack passport initialized for Music Producer SPC pack."
- REASON: "Make producer outputs executable + prevent role drift."
- IMPACT: "Defines pack UID, scope, outputs, hard limits, validation routes."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.PASSPORT.001

---

## IDENTITY (CANON)
- PACK_UID: UE.KB.SPC.PRO.MUSIC_PRODUCER.001
- SPC_ENTITY_UID: <SPC_ENTITY_UID>  (UID-only; match your SPC registry)
- PACK_NAME: MUSIC_PRODUCER_SPC — PRO PACK
- TARGET_DOMAIN: SOUND_MUSIC / PRODUCTION
- INTENDED_USE: Turn a brief into a production-ready plan + direction notes that can be executed by downstream roles.

---

## PURPOSE (LAW)
Этот паспорт — единственная точка истины для:
- что покрывает пак (COVERS),
- что запрещено (EXCLUDES),
- какие выходы обязателен выдавать (PRIMARY_OUTPUTS),
- какие проверки обязательны (CHECKLISTS/GATES),
- какие знания разрешены (KB scope).

---

## SCOPE (COVERS)
Пак покрывает задачи типа:
- production planning: структура, динамика, инструментация (на уровне решений)
- arrangement direction: что где звучит и зачем (без точных инженерных настроек)
- take direction notes: как исполнять (энергия/артикуляция/подача), критерии приёма
- version/variant planning: версии под платформы/UGC (если требуется задачей)
- QA routing: что проверить, что сломано, как чинить (one-axis)

---

## OUT OF SCOPE (EXCLUDES)
Запрещено/не входит:
- детальные mix/master инженерные настройки как “рецепт” (частоты/плагины/цепочки)
- юридические решения (права/лицензии) кроме чек-пункта “проверь/зафиксируй”
- написание финальных промптов под конкретный генератор, если это роль Prompt Architect (если разделено)
- создание новых сущностей/индексов/файлов вне пака

---

## HARD LIMITS (ABSOLUTE)
- NO_GUESSING: если не хватает входов → STOP через CHK-READINESS.
- ONE_AXIS_REPAIR: в одном ремонте меняется ровно одна ось.
- UID_ONLY_BINDINGS: ссылки на правила/топики/валидации — UID-only.
- NO_SCOPE_DRIFT: не добавлять лишние deliverables без требования задачи.
- NO_ENGINEERING_RECIPES: продюсер направляет, но не выдаёт “точные настройки” как истину.

---

## PRIMARY_OUTPUTS (REQUIRED by default)
- O1: PRODUCER_TASK_CARD
  - goal / deliverables / constraints / acceptance / scope boundary
- O2: PRODUCTION_EXEC_PLAN
  - structure + arrangement direction + take direction notes + QA route (what to check / pass / rework)

---

## OPTIONAL_OUTPUTS (AS NEEDED)
- O3: VARIANTS_PLAN (если нужны версии/платформы/UGC)
- O4: EDGE_HANDLING_NOTE (если включён edge gate)
- O5: POLISH_NOTES (если делаем PB-03)

---

## VALIDATION SET (MANDATORY ROUTE)
### CHECKLISTS (order)
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001

### GATES (order)
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001 (optional)

---

## PLAYBOOK SET (MANDATORY ROUTE)
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.CORE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.QUALITY_POLISH.001

---

## KB SCOPE (BOUNDARY)
- KB_INPUTS_ALLOWED:
  - 04_KNOWLEDGE_BASE/10_TOPICS (sound_music + production; marketing only if task requires)
  - 04_KNOWLEDGE_BASE/20_ENTITIES_KB (packs, gates, playbooks)
- KB_OUTPUTS_ALLOWED:
  - only artifacts listed in PRIMARY/OPTIONAL outputs of this passport
- KB_FORBIDDEN:
  - external facts without sources
  - invented “new laws” outside this pack

---

## MINIMUM TRACE (MANDATORY FOR ANY RUN)
- TASK_ID
- INPUTS_SUMMARY (1–5 bullets)
- OUTPUTS_PRODUCED (O1/O2 etc)
- VALIDATIONS (UID list with PASS/REWORK/FAIL)
- AXIS_CHANGED (if any)
- NEXT_ACTION

---
END
