# SCENE LINK LAW — PRJ ↔ OUT ↔ AST
FILE: 05_PROJECTS/00_PRJ_GOVERNANCE/05__SCENE_LINK_LAW.md

SCOPE: Universe Engine / Production Linking
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Закон связей: как сцена связывается со стеком, ассетами и финальными выходами.

---

## 0) CORE LAW
- SCENE (PRJ) описывает что нужно сделать.
- STACK (OUT) описывает многодорожечную партитуру сцены.
- ASSETS (AST) содержат медиа-кирпичи.
- FINAL OUT (OUT) — итоговые сборки (видео/аудио/текст).

---

## 1) REQUIRED LINKS
В паспорте SCENE:
- EP_REF: <EP_UID>
- STACK_REF: <STACK_UID>  (становится обязательным после создания STACK)
- XREFS: [<KB_UIDs>] (персонажи/локации/объекты по желанию)

В STACK:
- SCENE_REF: <SCENE_UID>
- XREFS: [<KB_UIDs>, <AST_UIDs>]

---

## 2) STORAGE
- PRJ паспорта живут в PRJ дереве
- STACK и выходы живут в OUT дереве
- ассеты живут в AST дереве

---
END.
