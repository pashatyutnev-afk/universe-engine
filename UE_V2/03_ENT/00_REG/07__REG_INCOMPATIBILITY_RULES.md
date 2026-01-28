# 07__REG_INCOMPATIBILITY_RULES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REGISTRY / RULES
UID: UE.V2.REG.INCOMPAT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Типовые несовместимости и запреты для сборки цепочки.

---

## [M] INTENT
Запретить конфликтные комбинации и "сам себе судья": генераторы не подписывают, валидаторы не производят, etc.

---

## [M] RULES (CANON)
R1) ROLE=ENG с CAP generate/transform не может иметь CAP signoff.
R2) ROLE=VAL не может иметь CAP generate/pack/signoff.
R3) ROLE=QA не может иметь CAP generate/signoff.
R4) ROLE=CTL не может быть единственным источником контента (CTL=политика, не производство).
R5) ROLE=XREF не принимает финальные решения, только карты.
R6) Один и тот же UID не может быть одновременно REQUIRED и INCOMPATIBLE в одной цепочке.
R7) Если сущность помечена INCOMPATIBLE с DOMAIN (например VIS-only), её нельзя использовать в другом домене.

---

## [M] INCOMPATIBILITY_TAGS (SUGGESTED)
- INC.SELF_JUDGE      (производит и принимает одно и то же)
- INC.DOMAIN_MISMATCH (не тот домен)
- INC.IO_MISMATCH     (не стыкуется по IO)
- INC.SIGNOFF_LOCK    (не имеет права на signoff)
- INC.KB_SCOPE        (нет или не тот KB scope)

---

## [M] GATES
PASS если:
- цепочка не содержит конфликтов по правилам R1–R7
REWORK если:
- конфликт обнаружен (поменять состав участников или роли)
