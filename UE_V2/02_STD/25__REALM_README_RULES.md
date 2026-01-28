# 25__REALM_README_RULES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.REALM_README_RULES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Правила для README/RULES/REALM документов: что они содержат, какие ссылки дают, как не превращать их в свалку.

---

## [M] INTENT
Сделать навигацию по реалмам (ORC/CTL/VAL/QA/SPC/ENG/KB) понятной и лёгкой для контекста:
README и RULES ведут к индексам и правилам, а не дублируют содержимое сущностей.

---

## [M] DOCUMENT TYPES
A) REALM README
- "вывеска цеха": что это за реалм и куда входить

B) REALM RULES
- локальные правила реалма: нумерация, обязательные поля сущностей, запреты

C) REALM INDEX (00__INDEX_*)
- список сущностей реалма: кратко, структурно, без длинных описаний

---

## [M] REALM README MUST CONTAIN
1) INTENT (1–5 строк)
2) ENTRYPOINT LINKS (макс 7–12 ссылок):
   - главный индекс реалма (00__INDEX_*)
   - 1–3 ключевых entry файла (если есть)
   - 1 ссылка на STD/markers/token rules (если нужно)
3) LOAD_POLICY (anti-noise): "через IDX, не через дерево"
4) GATES (PASS/GAP/STOP кратко)

---

## [M] REALM RULES MUST CONTAIN
1) Naming/Numbering policy (как нумеруем файлы)
2) Required sections in entity files (паспорт, address line, interfaces, handoffs, gates)
3) Restrictions:
   - запрет длинных списков в README
   - запрет дублей функций без указания "AGGREGATOR vs EXECUTOR"
4) Link to:
   - STD/04 markers
   - STD/14 contribution token
   - STD/15 step token set (если релевантно)

---

## [M] INDEX MUST CONTAIN
- таблица/список: № / NAME / PURPOSE / STATUS / UID
- группировка: CORE / ENTRY / FOCUS / LEGACY / DEPRECATED (если нужно)

---

## [M] WHAT IS FORBIDDEN (ALL REALM DOCS)
- длинные полотна текста
- копирование содержимого сущностей внутрь README/INDEX
- огромные списки ссылок "на всё"
- навигация в обход индексов

---

## [M] GATES
PASS если:
- README/RULES ведут через IDX и остаются короткими
REWORK если:
- README/INDEX превращаются в свалку
