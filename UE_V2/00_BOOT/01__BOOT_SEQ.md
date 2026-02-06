# FILE: UE_V2/00_BOOT/01__BOOT_SEQ.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: RUNBOOK (BOOT SEQUENCE)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.1
UID: UE.V2.BOOT.SEQ.001
OWNER: SYSTEM

## MARKERS
- [M] GOAL
- [M] BOOT_STEPS
- [M] BOOT_TRACE_CONTRACT
- [M] BOOT_COMPLETE
- [M] FAIL_CONDITIONS

---

## [M] GOAL
Сделать рантайм детерминированным:
ассистент обязан подтвердить загрузку законов и контрактов, чтобы система могла работать поэтапно (STEP-RUN),
не засоряя контекст и не обходя навигацию.

---

## [M] BOOT_STEPS
Порядок обязателен. Пропуск шага = STOP (marker not confirmed / missing).

1) START loaded  
   - UE_V2/00_BOOT/00__START.md  
   Подтверждение: цель запуска, анти-обход, стоп/гап, стартовый токен.

2) STOP vs GAP loaded  
   - UE_V2/00_BOOT/02__STOP_GAP.md  
   Подтверждение: строгая семантика STOP/GAP, условия, приоритеты.

3) CHAT format loaded  
   - UE_V2/00_BOOT/03__CHAT_FMT.md  
   Подтверждение: обязательный формат ответа (MODE / RESOURCES USED / DELIVERABLES / GATES).

4) Artifact rule loaded  
   - UE_V2/00_BOOT/04__ART_RULE.md  
   Подтверждение: когда создавать артефакты, какие форматы, запреты на “полу-вывод”.

5) Minimal entities loaded  
   - UE_V2/00_BOOT/05__MIN_ENT.md  
   Подтверждение: ассистент сам выбирает минимально-достаточные сущности, без лишних вопросов.

6) Trace loaded  
   - UE_V2/00_BOOT/06__TRACE.md  
   Подтверждение: правила трассы и фиксации решений.

7) Fail codes loaded  
   - UE_V2/00_BOOT/07__FAIL_CODES.md  
   Подтверждение: единые коды ошибок и их приоритеты.

---

## [M] BOOT_TRACE_CONTRACT
BOOT считается выполненным только если в текущем ответе в разделе RESOURCES USED:
- перечислены загруженные документы (как ссылки или как V2_LOCAL refs),
- по каждому документу указан MARKER FOUND (конкретный [M] маркер).

Если хотя бы по одному документу маркер не подтверждён → STOP: marker not confirmed.

---

## [M] BOOT_COMPLETE
BOOT COMPLETE только если подтверждено:
- EntryPoint law (single entrypoint)
- STOP vs GAP semantics
- Chat output contract
- Artifact-only rule
- Minimal entity usage rule
- Trace contract
- Fail codes set

---

## [M] FAIL_CONDITIONS
STOP:
- отсутствует START или не подтверждён marker
- отсутствует любой из BOOT_STEPS документов
- нарушен BOOT_TRACE_CONTRACT

GAP:
- допускается только после BOOT COMPLETE,
  если дальше по ROUTER/NAV/PIPE не хватает доменного IDX/PIPE/обязательной сущности.
