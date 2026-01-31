# TOPIC — EXPOSITION INTEGRATION (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/12__NARRATIVE__EXPOSITION_INTEGRATION.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.EXPOSITION.001
OWNER: SYSTEM
ROLE: Atomic method to deliver exposition without lectures by embedding information into conflict, action, price-of-truth, and visible consequences; includes Exposition Ledger, pass/fail tests, and rewrite toolkit

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for exposition integration: anti-dump rules, info-as-weapon, price-of-truth, and scene-embedded delivery patterns with audits."
- REASON: "Exposition dumps kill pacing and credibility; information must be revealed through causality, stakes, and character action."
- IMPACT: "Entities can transmit world/plot info cleanly while maintaining tension, agency, and scene dynamics."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.012

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_narrative
- type_topic
- exposition
- info_delivery
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Экспозиция должна быть не “объяснением автора”, а частью действия.
Этот модуль даёт процедуру, как:
- определить, какая информация реально нужна,
- выбрать способ подачи (через конфликт/действие/цену/последствие),
- избежать инфо-дампа,
- сделать экспозицию проверяемой (pass/fail).

---

## 2) WHEN TO USE
- Персонажи слишком много объясняют словами.
- Сцены превращаются в “лекцию” о мире/плане.
- Информация нужна, но любая подача убивает темп.
- Возникают вопросы “почему они это рассказывают прямо сейчас”.

## 3) WHEN NOT TO USE
- История не требует объяснений (можно показать действиями без пояснений).
- Сначала нет цели/препятствия/ставок (см. Scene Craft + Objectives/Obstacles).
- Это справочная документация мира (это не экспозиция в сцене).

---

## 4) CORE PRINCIPLES (STRICT)
### P1 — Only necessary information
Давать только то, без чего сцена/решение не работает.

### P2 — Exposition must be motivated
Кто и зачем сообщает/получает информацию сейчас.

### P3 — Exposition must be paid
Правда стоит цены: уступка/риск/вина/компромат/время/ресурс.

### P4 — Exposition must change state
После получения инфы меняется цель/тактика/ставка/отношение.

### P5 — Show first, explain later (if needed)
Сначала эффект/последствие, потом минимальная причина.

---

## 5) INPUTS (MINIMUM)
- Сцена и её objective.
- Информация, которую надо донести (1–5 пунктов).
- Кто знает и кто не знает (holders).
- Ставки/давление (почему сейчас).

## 6) OUTPUTS (MINIMUM)
- Exposition Ledger (что, кому, зачем, каким способом, какая цена).
- План интеграции (в какие биты сцены вставить).
- PASS/REWORK/FAIL.

---

## 7) EXPOSITION TYPES (TOOLBOX)
Используй типы подачи:
- T1: Action proof (инфа через действие/демонстрацию)
- T2: Consequence first (сначала последствия, потом причина)
- T3: Price-of-truth dialogue (инфа добывается через торг/допрос/угрозу)
- T4: Artifact / document fragment (фрагмент, не лекция)
- T5: Environmental storytelling (следы/руины/символы)
- T6: Mistake reveal (ошибка/сбой показывает правило мира)
- T7: Time-pressure brief (минимальный бриф под дедлайном)

---

## 8) PROCEDURE (EXPOSITION LEDGER → SCENE INSERT)
### Step 1 — List REQUIRED INFO (max 5 bullets)
- I1:
- I2:
Правило:
- если больше 5 — инфу надо разбивать по сценам/эпизодам.

### Step 2 — Define “WHY NOW”
Одна строка:
- “Информация нужна сейчас, потому что ___ (давление/решение/опасность).”

### Step 3 — Define KNOWLEDGE HOLDERS
Для каждого I:
- кто знает
- кто должен узнать
- кто не должен узнать (risk)

### Step 4 — Choose DELIVERY TYPE per info (T1..T7)
Для каждого I выбери тип:
- лучше начинать с T1/T2/T5/T6 (показ),
- затем T3/T7 (слова), если без этого нельзя.

### Step 5 — Add PRICE OF TRUTH
Для каждого I:
- кто платит и чем
- какой риск/потеря возникает

Если цена “нулевая” — это почти всегда инфо-дамп.

### Step 6 — Insert into SCENE BEATS (3–7)
Размести I1..I5 по битам:
- Beat X: инфа появляется как часть конфликта/тактики
- Beat Y: инфа меняет план (state change)

Запрет:
- “всё рассказали в начале сцены”.

### Step 7 — Anti-dump checks
Проверить:
- персонажи не говорят то, что они оба знают
- нет “монолога на 10 строк” без сопротивления
- после инфы меняется действие/тактика
- инфа не ломает правила мира

### Step 8 — Rewrite if dump detected
Если инфо-дамп:
- сократи до 1–2 строк + вынеси остальное в действие/последствия
- добавь цену (торг/риск/время)
- переведи часть инфы в T5/T6 (следы/ошибка)

---

## 9) EXPOSITION LEDGER FORMAT (COPY)
EXPOSITION LEDGER:
| INFO_ID | INFO (what) | HOLDER (who knows) | TARGET (who must learn) | WHY NOW | DELIVERY TYPE (T1..T7) | PRICE OF TRUTH | WHERE (beat/scene) | STATE CHANGE |
|---|---|---|---|---|---|---|---|---|

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] Инфа ≤ 5 пунктов на сцену/кусок
- [ ] Есть WHY NOW
- [ ] Для каждого пункта указан holder/target/risk
- [ ] Для каждого пункта выбран delivery type (T1..T7)
- [ ] Для каждого пункта есть price of truth
- [ ] Инфа распределена по битам, не свалена в монолог
- [ ] После инфы есть state change (тактика/цель/ставка)
- [ ] Anti-dump checks пройдены

PASS IF:
- все пункты true

REWORK IF:
- инфа нужна, но подача лекционная или без цены

FAIL IF:
- инфо-дамп, персонажи “объясняют мир”, сцена стоит на месте

---

## 11) REWRITE TOOLKIT (FAST FIXES)
- Fix A: Cut 60% текста, оставить только то, что меняет действие сейчас.
- Fix B: Показ вместо слов: заменить объяснение демонстрацией (T1/T6).
- Fix C: Заплати за правду: торг/угроза/уступка (T3).
- Fix D: Разбей инфу на 2–3 сцены с разными “WHY NOW”.
- Fix E: Последствия вперёд: сначала провал/ущерб, потом короткая причина (T2).

---

## 12) EXAMPLES (MANDATORY)
### 12.1 PASS EXAMPLE (price-of-truth)
INFO:
- “дверь открывается только на узле сети и поднимает тревогу”
WHY NOW:
- герой собирается открыть шлюз прямо сейчас
DELIVERY:
- T6 mistake reveal: герой пробует — включается тревога
PRICE:
- охрана реагирует, время уменьшается (state change)
WHY PASS:
- инфа показана действием и сразу меняет тактику.

### 12.2 FAIL EXAMPLE (lecture)
Персонаж 12 строк объясняет “как устроен мир”, никто не сопротивляется, после этого ничего не меняется.
WHY FAIL:
- нет цены, нет мотива, нет state change.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/11__NARRATIVE__SCENE_OBJECTIVES_OBSTACLES.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/07__NARRATIVE__DIALOGUE_SUBTEXT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/08__NARRATIVE__REVEALS_SECRETS_INFORMATION_FLOW.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/09__NARRATIVE__CONFLICT_SCENE_DYNAMICS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (no lecture dumps; exposition must be motivated, paid, and state-changing)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
