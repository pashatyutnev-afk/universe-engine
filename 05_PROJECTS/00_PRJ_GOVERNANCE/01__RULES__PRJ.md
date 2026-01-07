# PROJECTS (PRJ) — RULES
FILE: 05_PROJECTS/00_PRJ_GOVERNANCE/01__RULES__PRJ.md

SCOPE: Universe Engine / Project Rules
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила для PACK/EP/SCENE/SHOT. UID, регистрация, связи, анти-дубли.

---

## 0) CORE LAW
- UID обязателен и единственный идентификатор.
- Объект PRJ существует только после регистрации в PRJ Global Registry.
- Дубли PACK/EP/SCENE запрещены (S0).

---

## 1) UID FORMAT (PRJ)
Единый формат системы:
`UE.<GLOBAL>.<CATEGORY>.<FAMILY>.<NAME>`

Для PRJ:
- GLOBAL = PRJ
- CATEGORY = PACK | EP | SCENE | SHOT
- FAMILY = проектный домен (обычно GEN или NAR, если хочешь так делить)
- NAME = UPPER_SNAKE_CASE (например: ARCHITECTS_OF_WORLDS, EP01, SCN_003, SH_012)

Примеры:
- `UE.PRJ.PACK.GEN.ARCHITECTS_OF_WORLDS`
- `UE.PRJ.EP.GEN.EP01`
- `UE.PRJ.SCENE.GEN.EP01_SCN_003`

---

## 2) REQUIRED PASSPORT FIELDS (MINIMUM)
Для любого PRJ объекта:
- UID
- STATUS / LOCK / VERSION
- SUMMARY (1–5 строк)
- PARENT_REF (к чему принадлежит)
- XREFS / DEPENDS_ON (если есть)

---

## 3) STATUS POLICY
- DRAFT — планируется
- ACTIVE — в работе
- LOCKED — запрещены изменения (если используешь)
- ARCHIVED — завершено

(если не хочешь LOCKED как статус — оставь только STATUS + LOCK)

---

## 4) ANTI-DUPLICATION
Перед созданием нового EP/SCENE:
- проверить PRJ Registry
- проверить NAME (EP01_SCN_003 и т.п.)
Если дубль найден → не плодим.

---
END.
