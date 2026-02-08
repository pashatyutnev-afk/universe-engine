# 02__STOP_GAP

SCOPE: UE_V2  
DOC_TYPE: BOOT_GUARD (STOP/GAP)  
UID: UE.V2.BOOT.STOPGAP.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: RAW only  
PURPOSE: Единый закон остановки (STOP) и мягкой деградации (GAP). Защищает рантайм от “угадывания”, обхода IDX и засорения контекста.

---

## [M] DEFINITIONS
- STOP: немедленная остановка рантайма. Никаких “догадок”, никакого продолжения.
- GAP: фиксируем дыру (отсутствие компонента/пайпа/индекса/сущности), но не ломаем систему. Разрешены только безопасные действия: запросить RAW/путь/указать недостающий маркер, либо выбрать дефолтный пайп если это разрешено ROUTER-ом.
- MUST_LOAD: минимальный набор файлов, обязательный для запуска (см. RUNTIME_MANIFEST).
- marker confirmed: внутри файла найден обязательный маркерный блок/секция (например [M], UID, SCOPE, NAV_RULE и т.д. — конкретный перечень задаётся RUNTIME_MANIFEST / ROUTER).

---

## [M] HARD STOPS (STOP CONDITIONS)
### STOP_01: INPUT ABSENT
Условие:
- нет TASK_TEXT (пусто / отсутствует / не задача)

Действие:
- вывести FAIL_CODE: STOP_01
- запросить TASK_TEXT
- завершить

---

### STOP_02: RAW MISSING (MUST_LOAD)
Условие:
- любой MUST_LOAD файл недоступен по RAW (нет ссылки / 404 / не найден / нет доступа)

Действие:
- FAIL_CODE: STOP_02
- перечислить: какой файл missing (PATH)
- запросить RAW ссылку или обновление ROOT_LINK_BASE
- завершить

---

### STOP_03: MARKER NOT CONFIRMED (MUST_LOAD)
Условие:
- файл по RAW доступен, но обязательный marker не найден/не подтверждён
  (например отсутствует SCOPE, UID, NAV_RULE, REQUIRED marker block [M], либо иной маркер из MUST_LOAD политики)

Действие:
- FAIL_CODE: STOP_03
- перечислить: какой файл + какой marker missing
- завершить

---

### STOP_04: NAV BYPASS ATTEMPT
Условие:
- попытка обойти IDX (открывать доменные файлы напрямую, массово грузить дерево, “давай все README”, “пробеги все папки” без ROUTE_TOKEN)

Действие:
- FAIL_CODE: STOP_04
- напомнить NAV_RULE: RAW only + IDX only
- вернуть управление в ROUTER / NAV step
- завершить

---

### STOP_05: ROUTE_TOKEN ABSENT AFTER ROUTING
Условие:
- после шага ROUTING не сформирован ROUTE_TOKEN (неполный или пустой)

Действие:
- FAIL_CODE: STOP_05
- указать отсутствующие поля ROUTE_TOKEN
- завершить

---

## [M] GAP CONDITIONS (SOFT DEGRADATION)
### GAP_01: DOMAIN PIPE NOT FOUND
Условие:
- ROUTE_TOKEN.PIPE_SELECTED указывает доменный пайп, но он отсутствует/недоступен

Разрешённое действие:
- зафиксировать GAP_01
- fallback только если ROUTER разрешает:
  - использовать PIPE_DEFAULT как временный, без доменных правил
- иначе: запросить недостающий RAW/файл пайпа

---

### GAP_02: REQUIRED IDX NOT FOUND
Условие:
- ROUTE_TOKEN.REQUIRED_IDX отсутствует/недоступен

Разрешённое действие:
- зафиксировать GAP_02
- запросить RAW ссылку на REQUIRED_IDX
- запретить выполнение PIPE (без IDX подтверждения)

---

### GAP_03: REQUIRED CHECK / PANEL MISSING
Условие:
- REQUIRED_CHECKS указывает обязательную проверку/панель (QA/VAL/CTL), но сущность/файл отсутствует

Разрешённое действие:
- зафиксировать GAP_03
- разрешить только:
  - продолжить до шага, не требующего этой проверки
  - либо вернуть в ROUTER для выбора альтернативного EXEC_MODE
- запретить выдавать “release-ready” результат без REQUIRED_CHECKS

---

### GAP_04: REG/XREF/KB/PIPE/LOG ACCESS NOT CONFIRMED VIA IDX
Условие:
- IDX открыт, но не подтверждает доступ хотя бы к одному из сегментов:
  REG, XREF, KB, PIPE, LOG

Разрешённое действие:
- зафиксировать GAP_04 (какой сегмент недоступен)
- запретить доменную работу до восстановления доступа
- разрешить только “repair navigation”: найти/исправить IDX/manifest

---

### GAP_05: SPC_PRIME NOT RESOLVED
Условие:
- BOOT_SEQ требует SPC_PRIME, но он не определён (нет DEFAULT_SPC_PRIME, нет ссылки из REG/IDX)

Разрешённое действие:
- зафиксировать GAP_05
- продолжить только в режиме “ROUTER-only” (без доменных решений и без ORC)
- запросить: где задан SPC_PRIME (manifest/REG)

---

## [M] ACTION OUTPUT FORMAT (MANDATORY)
При STOP:
- OUTPUT:
  - STATUS: STOP
  - FAIL_CODE: STOP_0X
  - MISSING: (что отсутствует)
  - NEXT: что нужно дать/исправить (1 конкретное действие)

При GAP:
- OUTPUT:
  - STATUS: GAP
  - GAP_CODE: GAP_0X
  - AFFECTED: (какой сегмент/файл/проверка)
  - ALLOWED: что можно сделать сейчас (строго из списка)
  - BLOCKED: что запрещено до закрытия GAP
  - NEXT: 1 следующий шаг

---

## [M] ANTI-NOISE ENFORCEMENT
Запрещено при STOP/GAP:
- подгружать дополнительные доменные файлы “на всякий случай”
- генерировать контент “как мог бы быть”
- заменять недостающие сущности догадками

Разрешено:
- 1 уточнение (что дать: TASK_TEXT или RAW/marker)
- 1 безопасный fallback (только если ROUTER разрешает)

---

## [M] CODES (NAMESPACING)
STOP codes:
- STOP_01 INPUT_ABSENT
- STOP_02 RAW_MISSING_MUST_LOAD
- STOP_03 MARKER_MISSING_MUST_LOAD
- STOP_04 NAV_BYPASS
- STOP_05 ROUTE_TOKEN_ABSENT

GAP codes:
- GAP_01 DOMAIN_PIPE_MISSING
- GAP_02 REQUIRED_IDX_MISSING
- GAP_03 REQUIRED_CHECK_MISSING
- GAP_04 SEGMENT_ACCESS_NOT_CONFIRMED
- GAP_05 SPC_PRIME_NOT_RESOLVED
