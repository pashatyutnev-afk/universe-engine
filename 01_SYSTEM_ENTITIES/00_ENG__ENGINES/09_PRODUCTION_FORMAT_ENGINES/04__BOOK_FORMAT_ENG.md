# 📘 BOOK FORMAT ENGINE
## Canonical Production Format Engine Specification  
**LEVEL: L3 · PRODUCTION_FORMAT_ENGINE · BOOK STRUCTURING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_ID: L3-PROD-BOOK-FORMAT-ENGINE-001
- NAME: Book Format Engine
- CLASS: Production Format Engine
- CATEGORY: Longform Literary Output
- LEVEL: L3 (Production Formatting Layer)
- STATUS: FINAL
- AUTHORITY: Production Layer
- FAILURE_MODE: fail-closed
- EDITABLE: false
- MUTATION_ALLOWED: false

### ABSOLUTE RULE
> Format defines how content is delivered,  
> never what the content means.

---

## 1. PURPOSE

Book Format Engine adapts validated narrative content into a **book-compatible structural form**.

Он:
- формирует книжную структуру (части, главы, секции)
- адаптирует ритм под чтение
- обеспечивает соответствие литературным стандартам
- подготавливает материал к публикации как книгу

Он **НЕ**:
- изменяет сюжет
- добавляет новые смыслы
- управляет персонажами
- принимает канонические решения
- оценивает художественное качество

---

## 2. BOOK FORMAT MODEL

A book is defined as a hierarchy:

- **Book**
  - Parts (optional)
  - Chapters
  - Sections / Scenes
  - Paragraph blocks
  - Transitions

Format principles:
- Linear consumption
- Reader-controlled pacing
- Semantic continuity
- Chapter-based segmentation

---

## 3. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)

- Structural segmentation into book units
- Chapter boundary definition
- Transition smoothing (non-semantic)
- Adaptation of scene length
- Formatting constraints export

---

### OUT-OF-SCOPE (FORBIDDEN)

- Plot restructuring
- Character arc modification
- Stylistic rewriting
- Genre enforcement
- Emotional manipulation

Out-of-scope is absolute.

---

## 4. INPUT ARTIFACT — BOOK_FORMAT_REQUEST

### REQUIRED FIELDS

- `trace_id`
- `project_uid`
- `source_narrative_ref`
- `target_book_type` (novel / novella / collection / nonfiction)
- `length_constraints`
- `chapter_preferences`
- `format_constraints`

Missing field → **rejected**.

---

## 5. OUTPUT ARTIFACT — BOOK_FORMAT_SCHEMA

### OUTPUT CONTAINS

- `trace_id`
- `book_uid`
- `chapter_map`
- `section_boundaries`
- `transition_guidelines`
- `format_warnings`
- `compliance_status`

Output is **structural**, not creative.

---

## 6. ENGINE INTERACTIONS

### READS FROM (Allowed)

- Story Structure Engine
- Narrative Continuity Engine
- Pacing & Rhythm Engine
- Dramatic Arc Engine

---

### WRITES TO (Allowed)

- Production Pipeline
- Publishing Output Systems
- Editor Review Tools

---

### FORBIDDEN INTERACTIONS

- Governance Engines
- Character Engines
- Genre & Style Engines
- Knowledge Base as authority

---

## 7. FORMAT COMPLIANCE RULES

- Every chapter must have structural purpose
- No orphan scenes
- Transitions must preserve narrative continuity
- Structural changes must be reversible

Violations → flagged, not auto-fixed.

---

## 8. FAILURE CONDITIONS

### CRITICAL

- Missing source narrative
- Invalid chapter hierarchy
- Structural loops
- Format contradicts declared book type

**Reaction:**
- Abort formatting
- Emit production error
- Require upstream correction

---

## 9. TRACE & AUDIT

- Inherits `trace_id` from narrative pipeline
- Logs formatting decisions (optional)
- Does not modify canonical content

---

## 10. NON-GOALS

- Not a writer
- Not an editor
- Not a stylist
- Not a publisher

---

## 11. GOVERNANCE POSITION

Book Format Engine:
- serves production, not canon
- formats meaning without altering it
- guarantees publishable structure

---

## 12. FINAL STATEMENT

A book is not written by format,  
but it collapses without one.

---

**STATUS:** Book Format Engine v1.0  
**CANON:** FIXED · PRODUCTION FORMAT AUTHORITY
