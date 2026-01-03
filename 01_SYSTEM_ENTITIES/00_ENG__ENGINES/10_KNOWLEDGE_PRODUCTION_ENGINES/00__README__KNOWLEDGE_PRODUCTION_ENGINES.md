# KNOWLEDGE PRODUCTION ENGINES
00__README__KNOWLEDGE_PRODUCTION_ENGINES

CLASS_ID: KNOWLEDGE_PRODUCTION
LEVEL: L3
ROLE: Knowledge → Applied Decisions

---

## PURPOSE
Knowledge Production Engines превращают профессиональную базу знаний
(стандарты, best practices, “как правильно”) в прикладные решения,
которые могут использовать Orchestrators, Domain Engines и Specialists.

Ключевая функция: **трансформация знаний в исполнимые правила / чек-листы / пресеты / рекомендации**.

---

## SCOPE (ALLOWED)
- Извлечение релевантных стандартов из Professional Knowledge
- Компиляция знаний в:
  - чек-листы
  - пайплайны (в виде шагов)
  - пресеты и гайды
  - “правила качества”
  - типовые схемы решений
- Нормализация терминов (приведение к Glossary)
- Сопоставление “запрос → какой стандарт применить”
- Формирование “Applied Knowledge Pack” (структурированный результат для других сущностей)

---

## OUTCOME (WHAT IT PRODUCES)
Результат работы — не контент и не сюжет, а **Knowledge Pack**, например:
- Lighting_Standard_Pack
- Dialogue_Naturalism_Checklist
- Shot_Composition_Preset
- Mixing_Mastering_Workflow
- Platform_Spec_YouTube_Longform

Формат результата:
- кратко
- структурно
- применимо в процессе
- без художественной генерации

---

## FORBIDDEN
- Изменение канона системы
- Придумывание “из фантазии” вместо базы знаний
- Генерация сюжета, сцен, диалогов
- Продакшн-рендер, монтаж, выпуск
- Подмена валидаторов (не проверяет, а предлагает “как делать правильно”)

---

## RELATIONSHIPS (WHO USES IT)
### Typical Callers (ALLOWED)
- ORCHESTRATORS (для сборки процессов)
- DOMAIN_*_ENGINES (для правил домена)
- SPECIALISTS (как справочник-помощник)
- VALIDATION_ENGINES (как эталон стандартов для проверки)

### Typical Inputs
- запрос/задача (task intent)
- контекст проекта (project constraints)
- ссылки на Professional Knowledge / Glossary / Standards

### Typical Outputs
- Applied Knowledge Pack
- Checklist Pack
- Preset / Template Pack

---

## BOUNDARY RULE
> Knowledge ≠ Decision.
>  
> Knowledge Production Engine даёт “как правильно по стандартам”,
> но финальное решение остаётся за Orchestrator / Governance.

---

## COMMON MISTAKES
- Смешивать с “Knowledge Base” (это хранилище)  
  Здесь — **движок преобразования**.
- Пытаться “проверять” вместо “компилировать”
- Делать художественные ответы вместо прикладных пакетов

---

## CREATION RULE
Новый Knowledge Production Engine создаётся, если:
- есть крупная область знаний (свет/звук/монтаж/актёрка/драматургия/маркетинг)
- и нужно регулярно превращать её в применимый, повторяемый “пакет решений”.

Один движок = один тип компиляции знаний (одна специализация результата).

---

STATUS: FINAL (Class README)
