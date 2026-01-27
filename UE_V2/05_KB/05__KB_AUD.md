# FILE: UE_V2/05_KB/05__KB_AUD.md
SCOPE: UE_V2
LAYER: 05_KB
DOC_TYPE: KB_DOMAIN
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.KB.AUD.001
OWNER: SYSTEM
TITLE: KB AUDIO (METRICS CORE)

## MARKERS
- [M] DEFINITIONS
- [M] THRESHOLDS
- [M] CONSTRAINTS

## [M] DEFINITIONS
- ID: AUD.RI | TYPE: DEF | BODY: RI_t = индекс читаемости вокала/лида в миксе. Цель: смысл читается при плотной аранжировке.
- ID: AUD.WTI | TYPE: DEF | BODY: WTI_t = индекс “износа/текстуры” (шероховатость, артефактность, ржавчина) без разрушения RI.
- ID: AUD.CF | TYPE: DEF | BODY: CF_3s_P50 = медиана crest factor на окнах 3s. Мера “ударности/пиковости” при заданной громкости.
- ID: AUD.LRA | TYPE: DEF | BODY: LRA = loudness range (LU). Мера динамического разрыва по треку.
- ID: AUD.DAIR | TYPE: DEF | BODY: ΔAIR% = относительное отклонение энергии 8–16 kHz от базового профиля “семьи”.
- ID: AUD.DLM | TYPE: DEF | BODY: ΔLM% = относительное отклонение энергии 250–500 Hz (low-mid) от базового профиля “семьи”.

## [M] THRESHOLDS
- ID: THR.RI.MIN | TYPE: THR | BODY: RI_t >= 0.62 (readability gate для релиза)
- ID: THR.CF.REL | TYPE: THR | BODY: CF_3s_P50 >= 11.5 (минимум “энергии” для релиза)
- ID: THR.LRA.HIGH | TYPE: THR | BODY: LRA > 12 LU (экстремальный режим, допускается только по LAW-13)
- ID: THR.DAIR.FLOOR | TYPE: THR | BODY: ΔAIR% >= -18% (нижний пол воздуха для “клаустрофобии”)
- ID: THR.DLM.MONO | TYPE: THR | BODY: ΔLM% = +5…+8% (монолитность вокала/центра)

## [M] CONSTRAINTS
- ID: CST.NO_CLONE | TYPE: CST | BODY: ΔAIR/ΔLM не должны совпадать “в ноль” между треками (иначе клоны), допускается вариативность в пределах доменных THR.
- ID: CST.RI_OVER_WTI | TYPE: CST | BODY: WTI разрешён только если RI не падает ниже THR.RI.MIN.
