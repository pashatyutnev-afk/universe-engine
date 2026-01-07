# REL POLICY + XREF STANDARD (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

SCOPE: Universe Engine / Standards
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Стандарт связей: кто с кем может взаимодействовать, в каком режиме, и как фиксируются ссылки/xref без путаницы.

REFERENCES:
- Marking SoT: `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`
- Doc Control: `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`

---

## 1) RELATION TYPES (CANON)
Каждая связь обязана иметь TYPE:

- CALLS        (вызывает / запускает)
- CONSUMES     (использует как вход)
- PRODUCES     (производит как выход)
- DEPENDS_ON   (зависит как предпосылка)
- VALIDATES    (проверяет валидность)
- QUALITY_GATES(проверяет качество)
- GOVERNS      (задаёт правила/рамки)
- REFERENCES   (ссылается без зависимости)

---

## 2) COMMUNICATION POLICY (WHO CAN TALK TO WHOM)
### 2.1 Allowed (DEFAULT)
- ORC CALLS ENG/SPC/CTL/VAL/QA
- SPC CONSUMES ENG/KB/PRJ и PRODUCES PRJ/AST/OUT/KB_suggestions
- CTL CHECKS PRJ/OUT readiness и PRODUCES checkpoint status
- VAL VALIDATES docs/artifacts against STD/ENG laws
- QA QUALITY_GATES outputs against style/naturalness constraints

### 2.2 Forbidden (DEFAULT)
- SPC MUST NOT CALL ORC (SPC не маршрутизирует)
- QA MUST NOT VALIDATE structure (это VAL)
- VAL MUST NOT judge artistic quality (это QA)
- CTL MUST NOT decide content (это SPC/ENG)
- Any ENT MUST NOT change STD (только governance/standards pipeline)

### 2.3 Conditional (ONLY IF EXPLICITLY DECLARED)
- ENG may reference outputs of SPC/QA/VAL as examples, но не как dependency без описания.

---

## 3) RELATION MODE (FREQUENCY TAG)
Чтобы описать “всегда/иногда/никогда” вводим MODE:

- ALWAYS     (по умолчанию, обязательная связь)
- SOMETIMES  (опционально, по условию)
- NEVER      (жёсткий запрет)

Запреты фиксируются для анти-ошибок.

---

## 4) XREF FORMAT (MANDATORY)
Любая ссылка на сущность/файл в документах оформляется так:

XREF:
- UID: <UE....>        (если есть)
- FILE: <canonical path> (если это документ)
- RAW: <raw link>      (если файл в репо)
- REL: <RELATION TYPE>
- MODE: <ALWAYS|SOMETIMES|NEVER>
- NOTE: "<коротко зачем>"

Если UID неизвестен (внешнее):
- UID: NONE
- SOURCE: <name>

---

## 5) MINIMUM XREF RULES
- Нельзя ссылаться “голой ссылкой” без REL и NOTE.
- Для ENT обязательно указывать UID.
- Для INDEX обязательно указывать RAW на файлы.

---

## 6) FINAL LAW
> Связи фиксируются явно. Скрытых связей не существует.

---
END.
