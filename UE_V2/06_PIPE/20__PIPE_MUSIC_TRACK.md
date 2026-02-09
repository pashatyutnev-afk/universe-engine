# 20__PIPE_MUSIC_TRACK

DOC_TYPE: PIPE
DOMAIN: MUSIC
PIPE_ID: MUS.TRACK
VERSION: 1.4.0
UPDATED: 2026-02-09

---

## PURPOSE
Собрать трэк (Suno-ready) через полную декомпозицию: SPC → ORC → CTL → VAL → QA → финальная сборка.
Этот PIPE — “главный маршрут” для трека и вызывает подпроцессы:
- 21__PIPE_MUSIC_LYRICS (текст)
- 22__PIPE_MUSIC_IDENTITY (идентика/бренд/метаданные)

---

## INPUTS (MIN)
- TASK_TEXT (что сделать, для кого, эмоция, стиль/смеси, ограничения)
- CONSTRAINTS (platform, duration, structure, language, vocal, tempo)
- BRAND/CONTEXT (если нужно: мастерская/проект/герой)

---

## OUTPUTS
- SUNO_PACK: Title / Lyrics / Prompt / Negative
- RELEASE_PACK: cover copy / tags / credits / notes
- RUN_LOG refs (ключевые токены стадий)

---

## ENTITY MAP (CANON PATHS)
### ORC (production)
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/02__MUS__GENRE_STYLE_ROUTER__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/05__MUS__LYRIC_BRIEF_FACTORY__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/06__MUS__LYRIC_DRAFTER__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/07__MUS__LYRIC_EDITOR__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/11__MUS__HOOK_FORGE__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/13__MUS__ARRANGEMENT_ROUTER__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/08__MUS__PROMPT_PACKAGER__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/09__MUS__TRACK_BUILD_STEP__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/10__MUS__HOOK_FOCUS_LOOP__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/11__MUS__MIX_FOCUS_LOOP__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/12__MUS__LYRICS_FOCUS_LOOP__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/17__MUS__MERGE_SYNTHESIS__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/18__MUS__RELEASE_ASSEMBLER__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/19__MUS__RELEASE_PACK__ORC__ENT.md

### CTL (controllers)
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/01__MUS__PROMPT_CONTRACT__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/03__MUS__DURATION_POLICY__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/09__MUS__QUALITY_GATES__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/11__MUS__CTL__TONE_AND_ETHOS__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/12__MUS__CTL__FLOW_AND_PRONUNCIATION__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/13__MUS__CTL__MIX_TIGHTNESS__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/16__MUS__FOCUS_LOOP_STOP_RULES__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/17__MUS__SYNTHESIS_MERGE_POLICY__CTL__ENT.md

### VAL (validators)
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/08__MUS__PROMPT_FIDELITY__VAL__ENT.md
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/11__MUS__CHAIN_COMPLETENESS__VAL__ENT.md
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/14__MUS__SYNTHESIS_COHERENCE__VAL__ENT.md
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/06__MUS__RELEASE_PACK_READY__VAL__ENT.md
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/11__MUS__VAL__SCORE_RUBRIC__VAL__ENT.md

### QA (quality)
- UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/05__MUS__MIX_TRANSLATION__QA__ENT.md
- UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/06__MUS__HOOK_PANEL__QA__ENT.md
- UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/10__MUS__TRACK_QA_PANEL__QA__ENT.md
- UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/11__MUS__QA__LYRICS_COMPLIANCE__QA__ENT.md
- UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/12__MUS__QA__SUNO_PACKAGE_CHECK__QA__ENT.md

### KB (knowledge fuel)
- UE_V2/05_KB/11__KB_NAV_ROOT.md
- UE_V2/05_KB/10_TOPICS/50_SOUND_MUSIC/*

---

## [M] STEP-RUN STAGES (CANON ORDER)
S0 INTAKE
- принять TASK_TEXT + CONSTRAINTS
- CTL: Duration Policy + Prompt Contract (каркас ограничений)

S1 STYLE ROUTING
- ORC: Genre Style Router → STYLE_PROFILE_A/B (смеси, feel, tempo, рефы)
- CTL: Quality Gates (минимальные требования, что считаем “PASS”)

S2 IDENTITY / METADATA
- вызвать подпроцесс 22__PIPE_MUSIC_IDENTITY → IDENTITY_TOKEN + NAMING_POLICY
- ORC: Release Assembler (черновик метаданных)

S3 HOOK EXPLOSION (12–24 хуков)
- ORC: Hook Forge → HOOK_POOL (ранжированный)
- QA: Hook Panel (быстрая оценка запоминаемости)
- VAL: Score Rubric (первичный скоринг)

S4 LYRICS FACTORY
- вызвать подпроцесс 21__PIPE_MUSIC_LYRICS → LYRICS_VARIANTS
- CTL: Tone/Ethos + Flow/Pronunciation
- QA: Lyrics Compliance

S5 ARRANGEMENT + PROMPT PACK
- ORC: Arrangement Router → ARR_PROFILE_A/B/C (динамика, half-time, инструменты)
- CTL: Mix Tightness + Prompt Contract
- ORC: Prompt Packager → SUNO_PACK variants (2–4)

S6 BUILD / GENERATE VARIANTS
- ORC: Track Build Step → VARIANT_BATCH (рекомендовать 3–8 генераций в Suno)
- QA: Mix Translation (проверка “как сядет” на телефоне/машине)
- VAL: Prompt Fidelity

S7 FOCUS LOOPS (если надо)
- ORC: Hook Focus Loop / Mix Focus Loop / Lyrics Focus Loop
- CTL: Focus Loop Stop Rules (когда прекращать гонять)

S8 SYNTHESIS MERGE
- ORC: Merge Synthesis → COMPOSITE_DRAFT
- CTL: Synthesis Merge Policy
- VAL: Synthesis Coherence

S9 FINAL QA + RELEASE PACK
- QA: Track QA Panel + Suno Package Check
- ORC: Release Pack → финальные Title / Prompt / Negative / Notes
- VAL: Release Pack Ready + Chain Completeness

---

## GATES (PASS/FAIL)
- CTL duration/structure PASS
- QA lyrics compliance PASS
- VAL prompt fidelity PASS
- VAL synthesis coherence PASS
- QA suno package check PASS
- VAL chain completeness PASS
