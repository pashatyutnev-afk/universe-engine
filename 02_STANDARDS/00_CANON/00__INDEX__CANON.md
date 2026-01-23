# CANON INDEX (MASTER)
FILE: 02_STANDARDS/00_CANON/00__INDEX__CANON.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: INDEX
INDEX_TYPE: MASTER
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.STD.IDX.CANON.001
OWNER: SYSTEM
ROLE: Single SoT for NAV/EXISTENCE inside `02_STANDARDS/00_CANON` (RAW-only)

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: PATCH
- SUMMARY: "Enforced RAW-only navigation. Index contains only RAW links, no PATH navigation."
- REASON: "NAV_RULE: Use RAW links only."
- IMPACT: "Index becomes executable navigation entrypoint."

---

## PURPOSE (LAW)
Этот индекс — единственный источник истины (SoT) для навигации и существования файлов в области:
`02_STANDARDS/00_CANON`.

---

## NAVIGATION (RAW ONLY)
CANON MAP (files in scope):

- `02_STANDARDS/00_CANON/00__INDEX__CANON.md` — [RAW](https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_CANON/00__INDEX__CANON.md)
- `02_STANDARDS/00_CANON/01__ARCHITECTURE_OVERVIEW.md` — [RAW](https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_CANON/01__ARCHITECTURE_OVERVIEW.md)
- `02_STANDARDS/00_CANON/02__SYSTEM_CANON.md` — [RAW](https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_CANON/02__SYSTEM_CANON.md)

---

## EXISTENCE RULE (ABSOLUTE)
Канон области `02_STANDARDS/00_CANON` состоит только из файлов, перечисленных в CANON MAP выше.
Любой файл в этой папке, отсутствующий в CANON MAP, считается:
- неканоничным, или
- требующим регистрации (добавления в CANON MAP), или
- DEPRECATED/POINTER (если по стандарту должен быть заменён).

---

## NAV RULE (ABSOLUTE)
Внутри этого индекса допускаются только RAW ссылки.
Любые PATH/relative ссылки считаются нарушением и должны быть удалены/заменены на RAW.
