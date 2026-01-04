# Image Generation Engine
FILE: 05__IMAGE_GENERATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Produces reproducible image outputs via prompt packs, constraints, and QC loops

---

## PURPOSE

Этот движок превращает сцену+стиль в **воспроизводимую генерацию**:
- prompt pack
- негативы
- параметры
- референсы
- QA критерии

---

## INPUTS

- Scene spec + composition + lighting
- Style bible
- Output needs (resolution, aspect, count)
- Forbidden list (что нельзя)

---

## OUTPUTS

- Prompt Pack
- Generation settings (engine-agnostic)
- Variation plan
- QC checklist

---

## PROMPT PACK (CANON)

- BASE PROMPT (описание сцены)
- STYLE LOCK (ключевые признаки)
- CAMERA LOCK (линза/план/угол)
- LIGHT LOCK (key/fill mood)
- MATERIAL LOCK (если нужно)
- NEGATIVE PROMPT (что исключить)
- PARAMETERS (aspect, quality, seed policy)
- VARIATIONS (A/B/C цели вариаций)

---

## QC CHECKLIST

- does it match composition priority?
- does it match style locks?
- any forbidden artifacts?
- continuity errors (props, symbols)?
- readability at thumbnail?

---

## VALIDATION RULES

- IG1: Генерация должна быть повторяема: есть pack.
- IG2: Любая вариация должна иметь цель (не “рандом ради рандома”).
- IG3: QC обязателен перед “канонизацией” арта.

---
OWNER: Universe Engine
STATUS: FIXED
