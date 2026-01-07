# KB RULES (GOVERNANCE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULES
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.LAW.RULES.001
OWNER: SYSTEM
ROLE: Governance rules for KB layer: existence, structure, naming ranges, delegation (topics), anti-dup, alias policy

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "KB rules приведены к текущему дереву: realms, topics, delegation, aliases, anti-dup"
- REASON: "Чтобы KB работал как система: без коллизий и дублей"
- IMPACT: "KB growth, navigation, canon consistency"

---

## PURPOSE (LAW)
Эти правила задают, что считается каноном в KB и как слой расширяется без бардака.

---

## ORDER OF AUTHORITY (KB)
1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE`
3) `04_KNOWLEDGE_BASE/*` + `04_KNOWLEDGE_BASE/10_TOPICS/*`

---

## EXISTENCE RULE (ABSOLUTE)
- Канон KB существует только через master-index:
  `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE`
- Для subtree topics действует делегация:
  `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS` является SoT по существованию topics.
- Любой файл в репо, но не зарегистрированный в соответствующем index — NON-CANON / ignored.

---

## STRUCTURE MODEL (CANON)
- Governance: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/` (правила/карты/реестры/шаблоны/справочники)
- Realms: `04_KNOWLEDGE_BASE/01__* ... 08__*` (порталы/карта домена)
- Topics: `04_KNOWLEDGE_BASE/10_TOPICS/*` (конкретные статьи/пакеты)
- Aliases: `04_KNOWLEDGE_BASE/98__*` + `04_KNOWLEDGE_BASE/99__*` (только pointer)

---

## DOC CONTROL (MANDATORY)
См. SoT:
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL`

---

## ANTI-DUP (HARD)
- Один смысл → один KB-артефакт.
- Если тема нужна в нескольких местах — делается один topic + XREF из realms.
- Копировать большие куски текста между realms/topics запрещено — вместо этого XREF.

---

## LINKS (REL/XREF)
SoT:
- REL types: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES`
- XREF rules: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES`

---

## ALIAS POLICY (HARD)
- Alias файлы не канон и не содержат контента.
- Любой alias, который “начинает жить своей жизнью”, считается violation и должен быть вычищен.

---

--- END.
