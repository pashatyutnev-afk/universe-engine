# 🎭 DRAMATIC ARC ENGINE
## Canonical Narrative Engine Specification  
**LEVEL: L2 · DOMAIN_NARRATIVE_ENGINE · STORY DYNAMICS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_ID: L2-NAR-DRAMATIC-ARC-ENGINE-001
- NAME: Dramatic Arc Engine
- CLASS: Domain Narrative Engine
- CATEGORY: Narrative Structure
- LEVEL: L2 (Narrative Core)
- STATUS: FINAL
- AUTHORITY: Narrative Layer
- FAILURE_MODE: fail-closed
- EDITABLE: false
- MUTATION_ALLOWED: false

### ABSOLUTE RULE
> A story without a dramatic arc  
> is not a story — it is a sequence of events.

---

## 1. PURPOSE

Dramatic Arc Engine defines the **fundamental progression of dramatic tension**  
within any narrative artifact.

Он:
- формирует рост и спад напряжения
- определяет драматическую форму истории
- обеспечивает ощущение движения и смысла

Он **НЕ**:
- пишет сцены
- генерирует диалоги
- управляет персонажами напрямую
- адаптирует формат

---

## 2. DRAMATIC ARC MODEL

Canonical arc phases:

1. **Exposition**
2. **Inciting Incident**
3. **Rising Action**
4. **Climax**
5. **Falling Action**
6. **Resolution**

Отсутствие любой фазы → **нарратив неполон**.

---

## 3. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)

- Определение фаз драматической дуги
- Контроль последовательности фаз
- Проверка целостности дуги
- Сигнализация разрывов дуги
- Передача структуры другим движкам

---

### OUT-OF-SCOPE (FORBIDDEN)

- Создание контента
- Изменение логики мира
- Изменение мотивации персонажей
- Форматирование под платформы
- Оптимизация под аудиторию

---

## 4. INPUT ARTIFACT — NARRATIVE_STRUCTURE_REQUEST

### REQUIRED FIELDS

- `request_id`
- `trace_id`
- `story_uid`
- `narrative_scope`
- `story_length_class`
- `genre_context`
- `constraints`
- `dependencies`

Missing field → **rejected**.

---

## 5. OUTPUT ARTIFACT — DRAMATIC_ARC_SCHEMA

### OUTPUT CONTAINS

- arc_type
- ordered_phase_list
- tension_curve (abstract)
- phase_dependencies
- validation_flags

Schema is **descriptive**, not executable.

---

## 6. INTERACTIONS

### READS FROM
- Narrative Logic Engine
- Theme & Meaning Engine

### WRITES TO
- Scene Construction Engine
- Pacing & Rhythm Engine
- Tension & Stakes Engine

### FORBIDDEN INTERACTION
- Production Engines
- Specialists
- Knowledge Base (as authority)

---

## 7. VALIDATION RULES

- Climax must exist
- Rising Action must precede Climax
- Resolution must reduce tension
- Circular arcs must be explicitly declared

Violation → **structure invalid**.

---

## 8. FAILURE CONDITIONS

### CRITICAL

- Missing climax
- Broken phase order
- Undefined arc type

**Reaction:**
- Narrative invalidation
- Downstream block
- Audit log entry

---

## 9. TRACE & AUDIT

- All arc decisions use `trace_id`
- Arc schema is trace-linked to story_uid
- Changes require Change Control approval

---

## 10. NON-GOALS

- Emotional manipulation
- Audience prediction
- Genre enforcement
- Style definition

---

## 11. GOVERNANCE POSITION

Dramatic Arc Engine:
- precedes scenes
- precedes pacing
- precedes emotional tuning
- never executes content

It defines **form**, not **matter**.

---

## 12. FINAL STATEMENT

Meaning emerges  
where tension has direction.

---

**STATUS:** Dramatic Arc Engine v1.0  
**CANON:** FIXED · STRUCTURAL
