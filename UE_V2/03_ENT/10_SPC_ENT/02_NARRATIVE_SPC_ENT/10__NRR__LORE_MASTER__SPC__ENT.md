FILE: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/10__NRR__LORE_MASTER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 02_NARRATIVE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: NRR_SPC
KEY: SPC.NRR.LORE_MASTER
UID: UE.V2.ENT.SPC.NRR.LORE_MASTER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Lore master. Хранитель лора и связей канона для narrative-артефактов.
Следит, чтобы факты мира, имена, таймлайн, причинность лор-уровня и связи сущностей не “плыли”.

## [M] PURPOSE
Выпустить LORE_CONSTRAINTS_PACK так, чтобы:
- все заявленные факты эпизода/сцен были совместимы с текущим каноном
- каждое новое утверждение было помечено как NEW/EXISTING/UNKNOWN и имело SoT-ключ
- противоречия были найдены до написания финального текста
- были выданы точные XREF требования (что связать, где обновить, какие ключи затронуты)
- команда получила “разрешение на использование” лор-элементов (allowed set)

## [M] SCOPE
Делает:
- проверку фактов, терминов, названий, титулов, географии, рас, технологий, правил мира
- контроль таймлайна и причинно-следственных связей на лор-уровне
- выпуск списка допустимых лор-элементов для эпизода (ALLOWED_LORE_SET)
- выпуск списка обязательных ссылок/сверок (REQUIRED_XREF_KEYS / REQUIRED_REG_KEYS)
- формирование лор-патчлиста: как исправить несостыковки с минимальной болью

Не делает:
- художественные решения вкуса/стиля (CRV спецы)
- драматургию сцен (DRAMATURG / STORY_ARCHITECT)
- финальную “власть канона” (если требуется вердикт) — это `SPC.GVN.GOVERNANCE_OWNER`

## [M] INPUTS (MIN)
- EPISODE_STRUCTURE или SCENE_LIST (включая имена, места, время, сущности)
- CURRENT_DRAFT (кратко/черновик)
- OPTIONAL:
  - WORLD_RULES / LAWS (если применимо)
  - список “хочу использовать” от showrunner/writers-room
  - существующие XREF/REG ключи (если уже известны)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.NRR_LORE_CONSTRAINTS_PACK

## [M] SPECIALIST_OUTPUT.NRR_LORE_CONSTRAINTS_PACK (SCHEMA)

### [M] HEADER
- domain: NRR_SPC
- key: SPC.NRR.LORE_MASTER
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- scope: EPISODE|ARC|SEASON
- dependencies_keys: [<KEY>, ...]

### [M] ALLOWED_LORE_SET
- allowed:
  - item: <name/term/entity>
    type: CHARACTER|FACTION|PLACE|ERA|TECH|LAW|ARTIFACT|EVENT|CREATURE|OTHER
    status: EXISTING|NEW_ALLOWED|NEW_NEEDS_GVN|UNKNOWN
    notes: <1–2 lines>
    required_xref_keys: [<KEY>, ...]
    required_reg_keys: [<KEY>, ...]

### [M] FACT_CHECK_MATRIX
- facts:
  - id: F1
    claim: <что утверждаем в тексте>
    location_in_draft: <scene/beat>
    canon_status: CONSISTENT|CONFLICT|UNKNOWN
    confidence: HIGH|MED|LOW
    evidence_keys: [<KEY>, ...]   # ключи SoT/XREF/REG
    action: KEEP|ADJUST|REMOVE|ESCALATE
    patch_hint: <минимальная правка>

### [M] TIMELINE_AND_CAUSALITY
- timeline_checks:
  - check: <что сверяем>
    result: OK|CONFLICT|UNKNOWN
    note: <коротко>
- causality_flags:
  - flag: <что ломает причинность лора>
    impact: LOW|MED|HIGH
    fix: <как починить>

### [M] NAMING_AND_TERMS
- canonical_names:
  - draft_name: <как написано>
    canon_name: <как должно быть>
    rule: <формат/титул/склонение если важно>
- banned_or_reserved_terms:
  - term: <...>
    reason: <почему нельзя/опасно>
    replacement: <вариант>

### [M] REQUIRED_XREF_AND_REG
- required_xref_keys: [<KEY>, ...]
- required_reg_keys: [<KEY>, ...]
- new_xref_requests:
  - target: <что нужно завести/обновить>
    reason: <почему>
    priority: P0|P1|P2

### [M] CONTRADICTIONS (MUST)
- contradictions:
  - conflict: <в чём противоречие>
    where: <scene/beat>
    canon_reference_keys: [<KEY>, ...]
    severity: BLOCKER|MAJOR|MINOR
    options:
      - option: <вариант исправления 1>
        cost: LOW|MED|HIGH
      - option: <вариант 2>
        cost: LOW|MED|HIGH

### [M] PATCHLIST (MINIMAL)
- minimal_patches:
  - where: <scene/beat>
    change: <что правим>
    reason: <какой канон сохраняем>
    cost: LOW|MED|HIGH

### [M] ESCALATION (IF NEEDED)
- needs_governance_verdict: YES|NO
- if YES:
  - reasons:
    - <почему нужен вердикт>
  - proposed_decision: APPROVE|REJECT|NEEDS_REVISION
  - questions_to_gvn:
    - <вопросы, чтобы быстро решить>

### [M] HANDOFF
- next_best_specialists: [<KEY>, ...]
- notes_for_showrunner:
  - <что держать в голове при финальных решениях>
- notes_for_writers_room:
  - <где чаще всего ошибаются>
- xref_actions_summary:
  - <короткий список что завести/обновить>

### [M] READY_GATE
- status: READY|NOT_READY
- blocking_issues: [<if NOT_READY>]

## [M] QUALITY_GATES
PASS если:
- есть ALLOWED_LORE_SET
- есть FACT_CHECK_MATRIX с минимумом по ключевым утверждениям
- CONTRADICTIONS заполнен (даже если пусто — явно “none”)
- REQUIRED_XREF_AND_REG задан (или “none” с причиной)
- есть PATCHLIST и HANDOFF
- если есть UNKNOWN/NEW_NEEDS_GVN — заполнена ESCALATION

FAIL если:
- “всё ок” без матрицы фактов
- нет ссылочной дисциплины через KEY (вместо этого текстовые “типа где-то было”)
- противоречия спрятаны/не названы
- нет конкретных правок

GAP если:
- нет EPISODE_STRUCTURE/SCENE_LIST или CURRENT_DRAFT

STOP если:
- попытка обхода KEY-only routing или вставка RAW в рабочие пакеты
