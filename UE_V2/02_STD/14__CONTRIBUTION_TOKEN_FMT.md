# 14__CONTRIBUTION_TOKEN_FMT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.CONTRIBUTION_TOKEN_FMT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единый формат "вклад-токена" от любой сущности (SPC/ENG/CTL/VAL/QA/XREF).

---

## [M] INTENT
Сделать участие сотен сущностей управляемым: каждый вклад короткий, полезный, сохраняемый, и пригоден для сборки "шедевра" без перегруза контекста.

---

## [M] RULES
1) Один вклад = один CONTRIBUTION_TOKEN.
2) Вклад обязан быть коротким: 5–12 буллетов максимум.
3) Вклад обязан иметь "что сделать" и "что не ломать".
4) Вклад обязан указывать, к какому DOMAIN и STAGE относится.
5) Вклад без проверяемых пунктов считается шумом (REWORK).
6) Вклад не должен включать длинные рассуждения. Только действия, риски, критерии.
7) Вклад может ссылаться на другие токены, но не тащит их содержимое в текст.

---

## [M] CONTRIBUTION_TOKEN_TEMPLATE
CONTRIBUTION_TOKEN:
- TOKEN_ID:
- STEP_ID:
- FOCUS_ID: (optional, если это FOCUS-LOOP)
- ROLE:
- ENTITY_UID:
- DOMAIN:
- STAGE:
- INPUT_REF: (кратко, 1–3 строки, или ссылки на токены)
- OUTPUT_TYPE: (из IO_TYPES)
- CONTRIBUTION (5–12 bullets):
  - ...
- DO_NOT_BREAK (1–3 bullets):
  - ...
- RISKS (0–3 bullets):
  - ...
- ACCEPTANCE (1–3 bullets):
  - ...
- NEXT_HINT (optional, 1–2 bullets):
  - ...

---

## [M] EXAMPLES (SHORT)
- CONTRIBUTION: "Сделать хук короче на 2 такта", "Добавить контраст в дропе", "Убрать частотный конфликт 200–400 Гц"
- DO_NOT_BREAK: "Не трогать темп", "Не менять тональность", "Сохранить узнаваемый мотив"
- ACCEPTANCE: "Хук узнаваем за 3–5 секунд", "Луп без шва", "Баланс держится на телефоне"

---

## [M] GATES
PASS если:
- заполнены ROLE, ENTITY_UID, DOMAIN, STAGE, CONTRIBUTION, DO_NOT_BREAK, ACCEPTANCE
REWORK если:
- больше 12 буллетов в CONTRIBUTION
- нет DO_NOT_BREAK или ACCEPTANCE
STOP если:
- отсутствует STEP_ID или непонятно к чему относится вклад
