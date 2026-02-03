# FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/02__GVN__RULE_ENFORCER__ORC__ENT.md
SCOPE: UE_V2
LAYER: 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_ENTITY
UID: UE.V2.ORC.GVN.RULE_ENFORCER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
LOCK: OPEN
TITLE: GOVERNANCE — RULE ENFORCER (ORC)

---

## MARKERS
- [M] INTENT
- [M] ROLE_IN_PIPE
- [M] ENFORCED_RULES
- [M] INPUTS
- [M] OUTPUTS
- [M] CHECKS
- [M] FAIL_GAP_POLICY
- [M] LOGGING
- [M] INTERFACES
- [M] GATES

---

## [M] INTENT
Жёстко гарантировать, что рантайм UE_V2:
- не обходит NAV/IDX и не “угадывает” пути
- не грузит деревья массово и не засоряет контекст
- работает детерминированно по ROUTE_TOKEN
- корректно применяет STOP/GAP и FAIL_CODES

Rule Enforcer — это “шлагбаум”: он либо пропускает шаг, либо останавливает/фиксирует дыру.

---

## [M] ROLE_IN_PIPE
Используется:
- после формирования ROUTE_TOKEN (ROUTER)
- перед любым доменным PIPE/ARTIFACT выполнением
- перед загрузкой новых файлов/сущностей в контекст

Цель: не дать рантайму “уехать” в обход правил.

---

## [M] ENFORCED_RULES
R1) NAV дисциплина
- Запрещён обход IDX: любые переходы к сущностям/панелям должны подтверждаться через NAV/IDX слой.
- Разрешены прямые переходы только внутри UE_V2 при наличии явного пути (без угадываний). (NAV_RULES)

R2) IDX дисциплина
- Индексы не должны содержать ссылок на индексы.
- “Линковая навигация” должна вести на сущности/панели/контракты, а не на другие IDX. (IDX_RULES)

R3) Anti-noise
- Всегда грузим минимум: START/MANIFEST/ROUTER/NAV_ROOT + 1 доменный IDX + 1–3 целевых файла.
- Запрещена массовая загрузка папок/деревьев.

R4) Deterministic routing
- Если ROUTE_TOKEN требует REQUIRED_IDX/REQUIRED_CHECKS — они обязательны.
- Нельзя “подменить” PIPE без явного правила маршрутизации.

R5) No-guessing
- Запрещено “восстанавливать” пути и UID по догадкам.
- Любая ссылка/зависимость должна быть подтверждена доступным индексом/панелью.

---

## [M] INPUTS
I1) TASK_TEXT (обяз.)
I2) ROUTE_TOKEN (обяз.)
I3) EXEC_MODE (STEP-RUN | FULL-RUN) — из ROUTE_TOKEN
I4) REQUIRED_IDX / REQUIRED_CHECKS — из ROUTE_TOKEN
I5) LOADED_SET (список уже открытых файлов/панелей в этом шаге)

---

## [M] OUTPUTS
O1) ENFORCE_RESULT: PASS | STOP | GAP
O2) VIOLATIONS: список кодов/правил, которые сработали
O3) REQUIRED_ACTION: что нужно загрузить/исправить, чтобы пройти
O4) SAFE_NEXT_STEP: что можно делать дальше (если PASS)

---

## [M] CHECKS
C1) Input present
- TASK_TEXT присутствует (иначе STOP)

C2) ROUTE_TOKEN integrity
- заполнены минимум: DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- если чего-то нет → GAP (не “додумывать”)

C3) NAV / IDX доступность
- REQUIRED_IDX доступен для открытия/проверки
- если REQUIRED_IDX отсутствует → GAP

C4) Anti-noise compliance
- если LOADED_SET превышает политику (массовая загрузка) → STOP (policy violation)

C5) No bypass confirmation
- любые прямые “прыжки” мимо IDX/панелей без разрешения NAV_RULES → STOP

---

## [M] FAIL_GAP_POLICY
STOP когда:
- нет TASK_TEXT
- нарушение политики (обход NAV/IDX, массовая загрузка, no-guessing violation)
- marker not confirmed в MUST_LOAD/обязательных стандартах

GAP когда:
- отсутствует REQUIRED_IDX / доменный PIPE / обязательная панель/сущность по ROUTE_TOKEN
- ROUTE_TOKEN неполный и требует достройки через разрешённый ROUTER шаг

Важно: GAP — это не ошибка качества. Это “дыра зависимостей”.
Если репа полная — GAP не появляется.

---

## [M] LOGGING
Пишем (или требуем записи) в:
- RUN_LOG: шаг, ENFORCE_RESULT, короткое пояснение
- DECISION_LOG: какая проверка сработала и почему
- TOKEN_ARCHIVE: ROUTE_TOKEN + ENFORCE_RESULT

---

## [M] INTERFACES
STANDARDS:
- UE_V2/02_STD/05__NAV_RULES.md
- UE_V2/02_STD/06__IDX_RULES.md
- UE_V2/02_STD/02__NAME_UID.md

BOOT:
- UE_V2/00_BOOT/02__STOP_GAP.md
- UE_V2/00_BOOT/07__FAIL_CODES.md

NAV:
- UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
- UE_V2/04_NAV/01__IDX_BOOT.md

ENT:
- UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__INDEX_MANIFEST__GVN__ORC__ENT.md

---

## [M] GATES
PASS если:
- TASK_TEXT есть
- ROUTE_TOKEN валиден (минимум заполнен)
- REQUIRED_IDX доступен
- нет нарушений NAV/IDX/Anti-noise/No-guessing

STOP если:
- нет TASK_TEXT
- нарушение политики (bypass / mass-load / guessing)

GAP если:
- отсутствует REQUIRED_IDX / обязательный PIPE/панель/сущность по ROUTE_TOKEN
- ROUTE_TOKEN требует достройки через ROUTER шаг
