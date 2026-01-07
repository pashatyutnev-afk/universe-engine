# SCENE STACK 4TRACK STANDARD (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md

SCOPE: Universe Engine / Standards
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единый формат 4 дорожек сцены (NAR/VIS/SND/MOT) + правила сборки в финальный OUT.

REFERENCES:
- Marking SoT: `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`
- Rel Policy SoT: `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md`
- Storage Map: `02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md`

---

## 0) PURPOSE
Сцена описывается не “одним текстом”, а стеком дорожек.
Это даёт живость и контроль: каждая линия независима и потом склеивается.

---

## 1) THE 4 TRACKS (CANON MINIMUM)
Каждая сцена обязана иметь 4 дорожки:

1) NAR — Narrative Track
- что происходит по смыслу: событие/действие/конфликт/поворот

2) VIS — Visual Track
- что видно: композиция, окружение, свет, камеры, ключевые кадры

3) SND — Sound Track
- что слышно: атмосфера, SFX, музыка, тишина, ритм аудио

4) MOT — Motion/Behavior Track
- как двигаются/ведут себя: мимика, жесты, походка, темп, микро-движения, поведение фона

---

## 2) SCENE PACK (CANON CONTAINER)
Результат работы над сценой хранится как SCENE_PACK:

SCENE_PACK:
- SCENE_ID / SCENE_UID (если есть)
- META (цель сцены, ограничения, тон)
- TRACKS:
  - NAR: [...]
  - VIS: [...]
  - SND: [...]
  - MOT: [...]
- LINKS (xref на источники/решения)
- QA_NOTES (если есть)
- VERSION

---

## 3) TRACK EVENT FORMAT (MANDATORY)
Любая дорожка состоит из EVENT блоков:

EVENT:
  ID: <TNN>            # локальный номер в дорожке (T01, T02…)
  TIME: <story-time>   # OPTIONAL: если есть тайминг в истории
  FOCUS: <who/what>    # на что внимание
  ACTION: "<что происходит>"
  CONSTRAINTS: []      # что нельзя нарушать
  ASSETS: []           # что надо сгенерить/подготовить
  NOTES: ""            # доп. пояснение

---

## 4) LAYERING RULE (живость)
Сцена обязана иметь одновременно:
- Foreground (главное)
- Background (фон/мир)
- Ambient (атмосфера/жизнь мира)

Это реализуется через события в VIS/SND/MOT.
Запрещено “пустая сцена без фона”.

---

## 5) ASSET OUTPUT (AST)
Если в EVENT указан ASSETS — оно обязано быть оформлено как AST deliverable:
- тип ассета (image/sfx/music/shotlist/animation)
- краткий payload
- output target: AST

---

## 6) MERGE RULE (как склеиваем в OUT)
Сборка в OUT делается так:

OUT_SCENE (финальная сцена) строится по порядку:
1) NAR skeleton (каркас смысла)
2) VIS overlay (визуальные уточнения)
3) MOT overlay (поведение и движения)
4) SND overlay (звук/музыка/тишина)

Результат OUT должен содержать:
- SCENE TEXT (читабельный)
- VIS SHOT NOTES (если нужно)
- SND CUES (если нужно)
- MOT CUES (если нужно)

---

## 7) ORC PIPELINE HOOK (минимум)
ORC для сцены обязан:
- собрать 4 дорожки (SPC/ENG outputs)
- прогнать CTL readiness gate (все дорожки заполнены)
- прогнать VAL (формат/шапки/ссылки)
- прогнать QA (естественность/тон/стиль/анти-ИИ)
- собрать OUT_SCENE

---

## 8) FINAL LAW
> Если нет 4 дорожек — сцена incomplete.

---
END.
