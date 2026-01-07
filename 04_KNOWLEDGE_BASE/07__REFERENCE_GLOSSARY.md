# REFERENCE GLOSSARY (KB REALM)
FILE: 04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_REALM
REALM: GLOSSARY
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.REALM.GLOSSARY.001
OWNER: SYSTEM
ROLE: Canonical glossary realm for KB: shared terms, short definitions, and disambiguation rules (used by all realms and passports)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Realm Reference Glossary канонизирован: единые термины + правила различения похожих понятий"
- REASON: "Без глоссария система начинает говорить разными словами про одно и то же"
- IMPACT: "Все KB realms, entity passports, indexes"

---

## 0) PURPOSE
Этот realm — единый словарь терминов KB.

Правило:
- если термин часто повторяется и влияет на понимание → он должен быть определён здесь.

---

## 1) BOUNDARIES (HARD)
### 1.1 This realm IS
- короткие определения терминов
- правила различения (disambiguation) похожих понятий
- единые названия для внутренних документов

### 1.2 This realm IS NOT
- длинные статьи и туториалы (это в realms)
- стандарты канона/UID/версий (это system law + standards)

---

## 2) DISAMBIGUATION RULE (MANDATORY)
Если есть 2 похожих понятия — у каждого должно быть:
- 1 строка “что это”
- 1 строка “чем не является”
- 1 строка “где живёт истина” (xref)

---

## 3) CORE TERMS (MINIMUM SET)
> Этот список можно расширять, но не превращать в энциклопедию.

### Artifact
**Что это:** любой результат, который хранится как файл/объект системы.  
**Не является:** “идеей в голове”.  
**Истина:** standards + storage map.

### Canon
**Что это:** то, что признано существующим и обязательным правилами.  
**Не является:** “файлом, который лежит в репо”.  
**Истина:** canon protocol + index existence rules.

### Index (Master Index)
**Что это:** файл-реестр существования и навигации внутри слоя.  
**Не является:** “списком для удобства”.  
**Истина:** system law indexes.

### Realm
**Что это:** тематический слой знаний (нарратив/персонажи/визуал и т.д.).  
**Не является:** стандартом формата.  
**Истина:** KB master index + realm files.

### SoT (Source of Truth)
**Что это:** единственный документ, где живёт смысл/правило.  
**Не является:** “копией этого правила в другом месте”.  
**Истина:** standards/specs + system law.

### Scene
**Что это:** минимальный блок действия/изменения (event + delta).  
**Не является:** “любым кусочком текста между абзацами”.  
**Истина:** narrative realm + scene standards.

### Event
**Что это:** факт изменения состояния в системе/истории.  
**Не является:** “описанием атмосферы без изменения”.  
**Истина:** expression engines + scene standards.

### Stakes
**Что это:** цена/риск потери, делающий выбор значимым.  
**Не является:** “важностью по словам автора”.  
**Истина:** narrative realm.

### Tension
**Что это:** давление неопределённости/угрозы/таймера на выбор.  
**Не является:** “громкой музыкой”.  
**Истина:** narrative realm + sound realm (как усиление, не причина).

### Pacing (Story-time)
**Что это:** ритм истории по поворотам/функциям сцен.  
**Не является:** темп монтажа.  
**Истина:** narrative realm.

### Editing Rhythm (Screen-time)
**Что это:** ритм восприятия через монтаж/планы/длительности.  
**Не является:** pacing истории.  
**Истина:** production/editing engines.

### Production Sound
**Что это:** звуковая читабельность, placement, ясность слоёв.  
**Не является:** композицией музыки.  
**Истина:** sound realm + production sound engine.

### Deep Music
**Что это:** композиция/гармония/аранж/вокал/микс/мастер.  
**Не является:** “музыкой как фоном в сцене”.  
**Истина:** sound/music engines (09 family).

### Handoff
**Что это:** передача между этапами пайплайна с контрактом.  
**Не является:** “скинул файлы и всё”.  
**Истина:** production pipeline realm.

### Checklist
**Что это:** критерии pass/fail, чтобы не спорить “нравится/не нравится”.  
**Не является:** “советом”.  
**Истина:** KB realms + QA practices.

### XREF / REL
**Что это:** явная связь документов/сущностей.  
**Не является:** “ссылка в тексте без правила”.  
**Истина:** REL policy + xref standards.

---

## 4) NAMING OF COMMON OBJECTS (KB)
- “Practice” = повторяемый приём
- “Method” = структурированный способ (шаги)
- “Checklist” = pass/fail контроль
- “Reference” = справка/определение
- “Case” = пример применения

---

## 5) NEXT EXTENSIONS (CONTROLLED)
Если терминов становится много:
- выделяем “Core terms” (обязательные)
- остальное группируем по realms

--- END.
