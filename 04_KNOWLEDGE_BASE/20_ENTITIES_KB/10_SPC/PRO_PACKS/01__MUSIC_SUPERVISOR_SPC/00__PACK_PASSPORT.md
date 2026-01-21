# 00__PACK_PASSPORT — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/00__PACK_PASSPORT.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Pack Passport
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: PACK_PASSPORT
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PASSPORT.001
OWNER: SPC (Music Supervisor)
ROLE: Canonical identity + scope boundaries + outputs + validation set for this Pro Pack.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Pack passport initialized for Music Supervisor SPC pack."
- REASON: "Make playbooks/checklists/gates executable without guessing."
- IMPACT: "Defines pack UID, scope, outputs, hard limits, validation routes."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.PASSPORT.001

---

## IDENTITY (CANON)
- PACK_UID: UE.KB.SPC.PRO.MUSIC_SUPERVISOR.001
- SPC_ENTITY_UID: <SPC_ENTITY_UID>  (UID-only; match your SPC registry)
- PACK_NAME: MUSIC_SUPERVISOR_SPC — PRO PACK
- TARGET_DOMAIN: SOUND_MUSIC / PRODUCTION (music supervision)
- INTENDED_USE: Produce/validate music-direction artifacts and supervision decisions.

---

## PURPOSE (LAW)
Этот паспорт — единственная точка истины для:
- что именно покрывает пак (COVERS),
- что запрещено (EXCLUDES),
- какие выходы обязателен выдавать (PRIMARY_OUTPUTS),
- какие проверки обязательны (CHECKLISTS/GATES),
- какие знания разрешены (KB scope).

---

## SCOPE (COVERS)
Пак покрывает задачи типа:
- supervision decisions for a track/album/scene: intent, constraints, acceptance criteria
- alignment of style/genre/mood with brief
- structure + hook/pacing supervision guidance (в рамках supervisory уровня)
- QA routing: what to check, what failed, how to rework (one-axis)
- packaging notes for release readiness (без “инженерных” действий)

---

## OUT OF SCOPE (EXCLUDES)
Запрещено/не входит в пак:
- фактический “mix/master engineering” (технические настройки/плагины/частоты как решения)
- написание финальных промптов под конкретный генератор, если это роль Prompt Architect (если у вас разделено)
- юридические решения (права/лицензии) кроме чек-лист напоминаний “проверь/зафиксируй”
- создание новых сущностей/индексов/файлов вне пака

---

## HARD LIMITS (ABSOLUTE)
- NO_GUESSING: если не хватает входов для решения — STOP и запрос недостающего (через CHK-READINESS).
- ONE_AXIS_REPAIR: при ремонте менять только одну ось за итерацию.
- UID_ONLY_BINDINGS: ссылки на правила/топики/валидации — UID-only (RAW только для навигации).
- NO_SCOPE_DRIFT: нельзя добавлять “лишние” блоки ради красоты, если не требуется deliverable.

---

## PRIMARY_OUTPUTS (REQUIRED by default)
> Эти выходы должны быть доступны в каждом нормальном прогоне PB-01, если задача не уточняет иное.

- O1: SUPERVISION_TASK_CARD
  - кратко: goal / deliverables / constraints / acceptance
- O2: QUALITY_AND_ACCEPTANCE_ROUTE
  - чеклисты/гейты + что считать PASS/REWORK/FAIL + куда маршрутизировать

## OPTIONAL_OUTPUTS (AS NEEDED)
- O3: POLISH_NOTES (если делаем PB-03)
- O4: EDGE_HANDLING_NOTE (если включён edge gate)

---

## VALIDATION SET (MANDATORY ROUTE)
### CHECKLISTS (order)
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.READINESS.001
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001

### GATES (order)
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.EDGE_CASES.001 (optional)

---

## PLAYBOOK SET (MANDATORY ROUTE)
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.CORE.001
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.DIAG_REWORK.001
- UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PB.QUALITY_POLISH.001

---

## KB SCOPE (BOUNDARY)
- KB_INPUTS_ALLOWED:
  - 04_KNOWLEDGE_BASE/10_TOPICS/(sound_music, production, marketing — only if task requires)
  - 04_KNOWLEDGE_BASE/20_ENTITIES_KB (SPC packs, gates, playbooks)
- KB_OUTPUTS_ALLOWED:
  - only artifacts listed in PRIMARY/OPTIONAL outputs of this passport
- KB_FORBIDDEN:
  - external facts without sources (если включён “no fantasy” режим)
  - inventing new policies not present in pack

---

## MINIMUM TRACE (MANDATORY FOR ANY RUN)
Каждый прогон обязан фиксировать:
- TASK_ID
- INPUTS_SUMMARY (1–5 bullets)
- OUTPUTS_PRODUCED (O1/O2 etc)
- VALIDATIONS (passed/failed UID lists)
- AXIS_CHANGED (if any)
- NEXT_ACTION

---
END
