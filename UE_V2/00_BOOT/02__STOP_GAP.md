# FILE: UE_V2/00_BOOT/02__STOP_GAP.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: LAW (STOP/GAP SEMANTICS)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.1.0
UID: UE.V2.BOOT.STOPGAP.001
OWNER: SYSTEM

---

## PURPOSE
Единые правила, когда рантайм:
- **STOP**: останавливается немедленно и законно
- **GAP**: уходит в разрешённую ветку “создать недостающее” и возвращается в пайплайн

Цель: убрать “самовольные обходы”, “угадывания” и хаос по причинам остановки.

---

## MARKERS
- [M] DEFINITIONS
- [M] GAP_BRANCH
- [M] STOP_BRANCH
- [M] DECISION_RULE
- [M] RETURN_TO_PIPE
- [M] OUTPUT_CONTRACT
- [M] EXAMPLES

---

## [M] DEFINITIONS
**STOP** — аварийная остановка рантайма. Разрешена только по трём причинам (см. STOP_BRANCH).
STOP означает: “дальше идти нельзя, иначе будет ложь / шум / обход закона”.

**GAP** — разрешённая ветка рантайма для устранения нехватки артефактов системы.
GAP означает: “дальше идти можно, но сперва нужно создать/восстановить обязательное”.

**MUST_LOAD** — минимальный набор файлов/правил, без которых старт/маршрутизация/навигация незаконны.

**RAW missing** — отсутствует доступ к RAW-ссылке обязательного ресурса (или ресурс не открывается/404/403/empty).

**marker not confirmed** — файл открыт, но нужный [M]-маркер(ы) не найден(ы), либо содержимое не соответствует заявленному маркеру.

**input absent** — отсутствуют обязательные минимальные входы задачи (например TASK_TEXT).

---

## [M] GAP_BRANCH
GAP запускается, если для прохождения гейта не хватает “строительного блока системы”.

### GAP triggers (разрешённые причины)
1) **Нет нужной сущности** (SPC/ORC/CTL/VAL/QA/XREF), без которой доменный пайп не может быть исполнен.
2) **Нет нужного шаблона / формата артефакта**, чтобы собрать deliverable (например: TEMPLATE, SPEC, PROMPT_PACK, README-формат).
3) **Нет правила / стандарта / доменного IDX**, без которого нельзя подтвердить NAV/REG/XREF/KB/PIPE/LOG гейты.

### GAP запреты
- Нельзя идти в GAP, если причина относится к STOP (RAW missing / marker not confirmed / input absent).
- Нельзя использовать GAP, чтобы “улучшить качество” без необходимости. GAP — только про недостающее.

---

## [M] STOP_BRANCH
STOP разрешён **только** если:
1) **RAW missing** (в режиме, где RAW обязателен)
2) **marker not confirmed**
3) **input absent**

### STOP запреты
Запрещено использовать STOP по причинам:
- “сложно”, “долго”, “не уверен”
- “слишком много файлов”
- “я думаю лучше так”
- “не хочу открывать IDX”
- “мне кажется можно обойти”

---

## [M] DECISION_RULE
Детерминированное правило:

1) Если **нет TASK_TEXT** → **STOP (input absent)**
2) Если **не открывается RAW обязательного ресурса** → **STOP (RAW missing)**
3) Если **нет нужных [M]-маркеров** в обязательном файле → **STOP (marker not confirmed)**
4) Иначе, если **можно устранить проблему созданием недостающего артефакта** → **GAP**
5) Иначе → **продолжать основной пайплайн**

---

## [M] RETURN_TO_PIPE
После GAP рантайм обязан:
- зафиксировать “что создано/обновлено” (хотя бы как pending log, если LOG ещё не поднят)
- **вернуться** в основной пайплайн на тот же шаг, где был GAP, и повторить гейт(ы)

---

## [M] OUTPUT_CONTRACT
### STOP output (обязательный минимум)
- STATUS: STOP
- REASON: RAW missing | marker not confirmed | input absent
- WHAT_IS_MISSING: точное имя файла/маркер/вход
- NEXT_ACTION: “дать RAW / дать TASK_TEXT / починить маркер”

### GAP output (обязательный минимум)
- STATUS: GAP
- GAP_TARGET: что именно нужно создать (entity/template/standard/idx)
- GAP_DELIVERABLE: полный файл(ы) в готовом виде (не “скелет”)
- RETURN_STEP: куда возвращаемся в PIPE после закрытия GAP

---

## [M] EXAMPLES
### Example A: нет TASK_TEXT
→ STOP(input absent)

### Example B: есть TASK_TEXT, но RAW на MUST_LOAD не открывается
→ STOP(RAW missing)

### Example C: файл открылся, но в нём нет нужного [M] блока
→ STOP(marker not confirmed)

### Example D: всё открылось, но нет доменного IDX для выбранного ROUTE_TOKEN
→ GAP(создать доменный IDX) → return_to_pipe

### Example E: нет шаблона под нужный артефакт (например “PROMPT_PACK”)
→ GAP(создать шаблон/стандарт) → return_to_pipe
