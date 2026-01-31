SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW / STANDARD
UID: UE.V2.LAW.TEMPLATES.DISCOVERY.018
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

---

## [M] PURPOSE
Сделать так, чтобы система НЕ “угадывала шаблоны”, а находила их детерминированно.

---

## [M] CANON LOCATION
Все шаблоны документов лежат в одном месте:

UE_V2/02_TEMPLATES/

Внутри:
- /NAV_STACK/ (INDEX_MANIFEST, PIPELINE_CONTRACT, START_NODE)
- /ENTITY/ (паспорт сущности, профили ролей)
- /KB/ (шаблоны баз знаний)
- /ARTIFACTS/ (output packs, отчёты, логи, карточки)

---

## [M] TEMPLATE INDEX
В корне UE_V2/02_TEMPLATES обязан быть:
00__TEMPLATES__INDEX_MANIFEST.md

Он содержит KEY → RAW на каждый шаблон.

---

## [M] DISCOVERY RULE (машинный)
Когда системе нужно создать документ:
1) открыть 00__TEMPLATES__INDEX_MANIFEST.md
2) найти KEY нужного шаблона
3) открыть шаблон по RAW и заполнить

Никаких “по памяти” и “на угад”.

---

## [M] GATES
PASS если:
- есть общий templates index manifest
- шаблоны лежат только в 02_TEMPLATES
GAP если:
- шаблоны раскиданы по папкам без центра
