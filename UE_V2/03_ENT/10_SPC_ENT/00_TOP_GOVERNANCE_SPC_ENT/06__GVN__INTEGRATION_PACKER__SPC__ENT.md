FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/06__GVN__INTEGRATION_PACKER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: GVN_SPC
KEY: SPC.GVN.INTEGRATION_PACKER
UID: UE.V2.ENT.SPC.GVN.INTEGRATION_PACKER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: Resolve via INDEX_MANIFEST KEY only

---

## [M] ROLE
Handoff and integration bundle packer.

## [M] PURPOSE
Собирает финальный “интеграционный пакет” после работы пайплайна/специалистов:
- упаковывает итоговые артефакты + ссылки на SoT (source of truth) и next-open KEYS
- фиксирует решения/ограничения/миграции/депрекации в одном месте
- формирует чек-лист “что сделать дальше” без гаданий
- гарантирует, что любой получатель (runtime/user/tools) получает самодостаточный пакет для продолжения

## [M] SCOPE
### IN
- FINAL_ARTIFACTS (контент-результат: тексты, промпты, схемы, планы, метаданные)
- ROUTE_TOKEN (DOMAIN/PIPE_SELECTED/REQUIRED_IDX/REQUIRED_CHECKS/EXEC_MODE)
- DECISION_RECORDS (если есть): governance verdicts, canon locks, migrations
- REQUIRED_UPDATE_KEYS (если есть): список файлов/индексов, которые должны быть обновлены
- OPTIONAL: evidence/test docs (QA результаты, test-doc gate, чек-листы)

### OUT
- INTEGRATION_OUTPUT_PACK (самодостаточный пакет интеграции)
- NEXT_OPEN_KEYS (куда идти дальше)
- PATCH_LIST / TODO_LIST (если есть недочёты)
- COMPAT_NOTES (back-compat/deprecation/migration)

## [M] MIN_INPUTS
- FINAL_ARTIFACTS (минимум 1)
- ROUTE_TOKEN
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (platform/tooling/limits)

## [M] OUTPUTS
### PRIMARY: INTEGRATION_OUTPUT_PACK (schema)
- HEADER
  - PACK_ID (локальный id)
  - CREATED_AT
  - DOMAIN
  - PIPE_SELECTED
  - EXEC_MODE
- SOT_POINTERS (Source of Truth)
  - SOT_KEY_LIST: [KEY...]
  - NOTES: где “истина” и что считать актуальным
- ARTIFACTS
  - ARTIFACT_LIST: [{name,type,summary,location_or_key}]
  - ARTIFACT_SUMMARY: 3–7 bullets, что готово
- ROUTE_CONTEXT
  - ROUTE_TOKEN (как есть, без пересказа)
  - REQUIRED_IDX_USED
  - REQUIRED_CHECKS_USED
- DECISIONS
  - DECISION_LIST: [{id, type, summary, impact, links_or_keys}]
- CHANGES
  - REQUIRED_UPDATE_KEYS
  - MIGRATION_NOTES (если есть)
  - DEPRECATION_FLAGS (если есть)
- QA / EVIDENCE
  - QA_STATUS: PASS|NOT_PASS|PARTIAL
  - EVIDENCE_POINTERS: [KEY/refs]
  - VIOLATIONS (если есть): [{code,summary,fix}]
- NEXT_ACTIONS
  - NEXT_OPEN_KEYS: [KEY...]
  - CHECKLIST: [action...]
  - RISKS: [{risk,impact,mitigation}]
- FOOTER
  - OWNER
  - CONTACT/RESPONSIBLE (если используется)
  - VERSION_STAMP

## [M] CANON PRINCIPLES (invariants)
- PACK MUST BE SELF-SUFFICIENT: пакет читается “с нуля” и ведёт к продолжению
- KEY-FIRST: ссылки на сущности/пайпы/индексы внутри пакета — через KEY (RAW только там, где разрешено системой)
- NO STORYTELLING: только факты, указатели, действия, проверки
- TRACEABLE: любое важное решение имеет запись в DECISIONS + влияние/следствия
- SAFE HANDOFF: next-open keys + checklist должны исключать гадания

## [M] PROCESS (STEP-RUN)
S1) Collect inputs
- собрать final artifacts
- собрать route token и required idx/checks
- собрать решения/миграции/депрекации
- собрать evidence/qa (если есть)

S2) Build pack skeleton
- HEADER + ROUTE_CONTEXT
- ARTIFACTS + SOT_POINTERS

S3) Attach decisions and changes
- DECISIONS
- CHANGES (required updates, migrations, deprecations)

S4) Attach QA / evidence
- QA_STATUS
- VIOLATIONS (если блокирует)

S5) Emit next actions
- NEXT_OPEN_KEYS
- CHECKLIST
- RISKS + mitigations

## [M] GATES
PASS если:
- PACK self-sufficient (есть route context + artifacts + next actions)
- SOT_POINTERS присутствуют и понятны (KEY list)
- REQUIRED_UPDATE_KEYS указаны (или явно “none”)
- QA_STATUS не противоречит выдаче (если NOT_PASS — есть violations + fix)

GAP если:
- нет route token
- не хватает required idx/checks подтверждения
- отсутствуют ссылки/keys на SoT при заявлении “final”

STOP если:
- нет final artifacts (паковать нечего)
- MUST_LOAD зависимости для домена/пайпа отсутствуют (если пак формируется внутри runtime и нельзя подтвердить)

## [M] KB SCOPE
### KB INPUTS
- ROUTE_TOKEN и правила routing/step-run
- стандарты упаковки и чек-листы
- QA gates и evidence requirements

### KB OUTPUTS
- интеграционные пакеты (output packs)
- нормализованные next-open keys + checklist

### KB BOUNDARIES
- не принимает “канон-вердикт” (только упаковывает то, что вынес Governance Owner)
- не меняет стандарты (эскалация к Standards Owner)
- не “чинит” нарушения — выдаёт patch list и next actions

## [M] INTERFACES (RAW references only)
- INDEX_MANIFEST (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
- PIPELINE_CONTRACT (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md
- Governance Owner (decision source):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/02__GVN__GOVERNANCE_OWNER__SPC__ENT.md
- Doc Controller (compliance source):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/04__GVN__DOC_CONTROLLER__SPC__ENT.md

## [M] SPC PEER ROLES (NON-ENG)
- Governance Owner: выдаёт approve/reject/needs_revision и условия
- Pipeline Architect: задаёт контракты/схемы/required updates
- Doc Controller: выдаёт violations + patch list
- Standards Owner: формализует стандарты упаковки/шаблоны
- Machine Architect: границы слоёв и интерфейсы

## [M] FAIL CODES (local)
- GVN_PACK_FAIL_NO_ARTIFACTS: нет артефактов для упаковки
- GVN_PACK_FAIL_NO_ROUTE_TOKEN: отсутствует route token
- GVN_PACK_FAIL_SOT_MISSING: заявлен SoT, но не указан key list
- GVN_PACK_FAIL_NEXT_ACTIONS_MISSING: отсутствуют next-open keys/checklist
- GVN_PACK_FAIL_QA_CONFLICT: QA_STATUS конфликтует с “final/ready”
- GVN_PACK_FAIL_CHANGES_UNTRACKED: изменения есть, но нет required update keys/migration notes

## [M] NOTES
- Если пакет “release-ready”, то QA_STATUS обязан быть PASS или иметь чёткий patch list, блокирующий релиз.
- NEXT_OPEN_KEYS — это главный способ исключить гадание при продолжении работы.
