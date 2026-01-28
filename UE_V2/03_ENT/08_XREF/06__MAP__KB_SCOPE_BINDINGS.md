# 06__MAP__KB_SCOPE_BINDINGS

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF / MAP
UID: UE.V2.XREF.KB_SCOPE_BINDINGS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Привязка сущностей к KB_SCOPE: кто какие знания может использовать.

---

## [M] INTENT
Снизить перегруз и хаос: каждая сущность работает только в своём scope, ORC выбирает участников с подходящими scope.

---

## [M] RULES
1) Источник истины по KB scope: KB/09__KB_SCOPE_PROFILES.md (или доменные KB).
2) Любая сущность (кроме bootstrap-ядра) обязана иметь KB_SCOPE_ID в REG_ENTITY_CATALOG.
3) Несовпадение DOMAIN и KB scope — REWORK.
4) Если KB scope отсутствует — GAP (создать профиль и привязку).

---

## [M] BINDINGS (DEFAULT, EXAMPLES)
CORE:
- KB.SCOPE.CORE.GOV:
  - allowed_roles: SPC,ORC,CTL,XREF,REG
  - allowed_domains: CORE
- KB.SCOPE.CORE.STD:
  - allowed_roles: VAL,CTL
  - allowed_domains: CORE
- KB.SCOPE.CORE.QA:
  - allowed_roles: QA
  - allowed_domains: CORE

MUSIC:
- KB.SCOPE.MUSIC.PROD:
  - allowed_roles: SPC,ORC,ENG,CTL,VAL,QA
  - allowed_domains: MUSIC
- KB.SCOPE.MUSIC.LYRICS:
  - allowed_roles: SPC,ENG,VAL,QA
  - allowed_domains: MUSIC
- KB.SCOPE.MUSIC.REL:
  - allowed_roles: ORC,CTL,VAL,QA,SPC
  - allowed_domains: REL,MUSIC

---

## [M] GATES
PASS если:
- выбранные участники имеют KB_SCOPE_ID и он совместим с DOMAIN задачи
REWORK если:
- KB scope не совпадает по домену/ролям
GAP если:
- нет профиля KB scope или привязки
