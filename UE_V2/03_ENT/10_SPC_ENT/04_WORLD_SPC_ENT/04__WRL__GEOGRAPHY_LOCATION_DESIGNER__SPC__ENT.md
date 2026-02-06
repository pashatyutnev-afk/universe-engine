FILE: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/04__WRL__GEOGRAPHY_LOCATION_DESIGNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 04_WORLD_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: WRL_SPC
KEY: SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER
UID: UE.V2.ENT.SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: Resolve RAW via INDEX_MANIFEST (KEY-only routing)

---

## [M] ROLE
Geography & Location Designer. Проектирует географию и сеть локаций: биомы, природные барьеры, маршруты, узлы, расстояния, логистику и “почему мир устроен так”.

## [M] PURPOSE
Сделать так, чтобы пространственный слой мира:
- был логичным (рельеф, климат, ресурсы, угрозы)
- поддерживал сюжет и маршрутизацию (пути, choke points, границы, проходы)
- давал локационные якоря для XREF/NRR/CHR и визуальной постановки
- содержал ограничения (куда нельзя, почему нельзя, чем опасно)
- позволял стабильные “карты решений” без постоянных переделок

## [M] SCOPE
Делает:
- GEO_FRAME: базовая география (континенты/регионы/биомы/рельеф)
- LOCATION_GRID: сетка локаций с ролями и связями
- ROUTE_NETWORK: маршруты, расстояния, узкие места, контрольные точки
- CLIMATE_LOGIC: климат/сезонность/погодные зоны (на уровне “принципы+последствия”)
- HAZARD_RESOURCE_MAP: опасности/ресурсы/убежища/источники воды/энергии/пищи
- BORDER_SYSTEMS: границы (естественные/социальные), зоны влияния, проходные коридоры
- TRAVEL_RULES: правила перемещения и ограничения (скорости, доступ, риски)
- MAP_NOTES: заметки для визуала (без режиссёрских решений) + риски/ограничения
- XREF_ANCHORS: якоря локаций для ссылок и проверок канона

Не делает:
- канонизация законов мира (это `SPC.WRL.WORLD_BUILDER` + governance)
- цивилизационные эпохи и макро-таймлайны (это `SPC.WRL.CIVILIZATION_DESIGNER`)
- социальную ткань культур (это `SPC.WRL.CULTURE_SOCIETY_ARCHITECT`)
- религии/мифы (это `SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER`)
- экономику/власть как механику (это `SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER`)
- экологию как биосистему (это `SPC.WRL.ECOLOGY_SURVIVAL_DESIGNER`, но координаты/биомы передаёт ему)

## [M] INPUTS (MIN)
- WORLD_BASELINE (климат/физика/маг-ограничения, если есть)
- REGION_SET: 3–9 регионов (имена или токены)
- OPTIONAL:
  - STORY_ROUTE_HINTS (если есть ключевые маршруты/походы/погони)
  - CIV_LOCATIONS_HINTS (столицы/узлы/границы цивилизаций)
  - SCALE_HINT (планета/континент/страна/архипелаг/город)
  - MAP_STYLE_HINT (если нужно под конкретный формат карты)

## [M] OUTPUTS (CANON)
- SPECIALIST_OUTPUT.WRL_GEO_LOCATION_PACK

## [M] SPECIALIST_OUTPUT.WRL_GEO_LOCATION_PACK (SCHEMA)

### [M] HEADER
- domain: WRL_SPC
- key: SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER
- created_at: <YYYY-MM-DD>
- decision_mode: FAST|RELEASE_READY|MASTERPIECE
- scale: <planet|continent|region|city>
- inputs_used: [WORLD_BASELINE, REGION_SET, ...]

### [M] GEO_FRAME
- world_units:
  - distance_unit: <km|days travel|segments>
  - travel_baseline:
      on_foot: <range token>
      on_mount: <range token>
      by_vehicle: <range token or N/A>
- regions:
  - region_id: R-01
    name: <name or token>
    biome: <desert|taiga|tundra|steppe|forest|mountain|ocean|ruins|other>
    terrain_signature: <1 line>
    climate_principles: [<principle>, <principle>]
    natural_barriers: [<mountains>, <rivers>, <storms>, <magic zone>, ...]
    key_resources: [<water>, <ore>, <food>, <energy>, ...]
    key_hazards: [<hazard tokens>]
    notes: <1–2 lines>

### [M] LOCATION_GRID
- locations:
  - loc_id: L-001
    name: <name>
    region_id: R-01
    kind: <city|village|fort|port|ruins|temple|station|wild zone|pass|oasis|other>
    role: <hub|border|refuge|resource node|story setpiece|gate|chokepoint>
    access_level: <open|restricted|forbidden|seasonal>
    why_here: <cause: geography/resource/history>
    constraints:
      - <constraint statement>
    hazards:
      - <hazard token>
    resources:
      - <resource token>
    tags: [<tag>, <tag>]

### [M] ROUTE_NETWORK
- routes:
  - route_id: RT-01
    from: L-001
    to: L-014
    mode: <foot|road|river|sea|air|portal|mixed>
    distance: <value or token>
    time_cost: <token>
    risk_level: <low|mid|high|extreme>
    choke_points: [<pass|bridge|checkpoint|narrows>]
    control: <who controls / none / contested>
    seasonal_variation: <none|winter blocks|floods|storms|other>
    travel_rules:
      - <rule: what must be true to pass>

### [M] BORDER_SYSTEMS
- borders:
  - border_id: B-01
    between: [R-01, R-02]
    type: <natural|political|cultural|hazard>
    description: <1–2 lines>
    crossings:
      - loc_id: L-033
        crossing_type: <pass|bridge|port|gate>
        access: <open|restricted|closed>
        risks: [<risk tokens>]

### [M] CLIMATE_LOGIC (PRINCIPLES)
- climate_rules:
  - rule_id: C-01
    principle: <e.g., "prevailing winds push storms into R-02">
    consequence: <what it causes in travel/resources/hazards>
    affected_regions: [R-02, R-03]
- seasonality:
  - season: <winter|dry|monsoon|other>
    changes:
      - <route changes>
      - <hazard changes>
      - <resource changes>

### [M] HAZARD_RESOURCE_MAP
- hazards:
  - hazard_id: H-01
    name: <token/name>
    type: <weather|terrain|fauna|conflict|anomaly|disease|other>
    triggers: [<trigger tokens>]
    effects: [<effect tokens>]
    mitigation: [<mitigation tokens>]
    zones: [R-01, L-001, RT-01]
- resources:
  - resource_id: RS-01
    name: <token/name>
    type: <water|food|ore|energy|shelter|knowledge|other>
    scarcity: <low|mid|high>
    control: <none|local|state|guild|religion|other>
    zones: [R-01, L-007]

### [M] TRAVEL_RULES (GLOBAL)
- movement_constraints:
  - rule: <rule statement>
    because: <why>
    impacts: [routes|regions|locations]
- typical_travel_windows:
  - context: <season/event>
    allowed: [<routes/regions>]
    blocked: [<routes/regions>]

### [M] XREF_ANCHORS (LOCATION SoT)
- anchor_id: XA-01
  loc_id: L-001
  title: <canonical location anchor>
  summary: <2 lines>
  invariants: [<what must remain true>]
  links_needed: [<xrefs/ids to create>]

### [M] VISUAL_NOTES (NO DIRECTING)
- constraints_only:
  - <visibility constraints, scale cues, materials as principles, hazard cues>
- risks:
  - <visual anachronism risk>
  - <map inconsistency risk>

### [M] HANDSHAKE_CONSTRAINTS
- for_world:
  - <what WRL specs must respect (biomes, barriers, distances)>
- for_narrative:
  - <route constraints, plausible travel time, choke points>
- for_character:
  - <background plausibility by region>
- for_creative:
  - principles: [<shape language principles, contrast principles, location mood principles>]
  - risks: [<style drift risks>]

### [M] GAP_NOTES
- missing_inputs: [..]
- specialists_to_call_next: [SPC.WRL.ECOLOGY_SURVIVAL_DESIGNER, SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER, ...]
- questions_for_user: [<only if blocking>]

### [M] READY_GATE
- status: READY|NOT_READY
- blockers: [..]
- next_actions: [..]

## [M] METHODS (CANON RULES)
- Каждая локация обязана иметь: role + why_here + constraints.
- Каждая связь (route) обязана иметь: mode + time_cost + risk_level + travel_rules.
- Климат описывать через принципы и последствия, не через “палитры/конкретные цвета”.
- VISUAL_NOTES: только ограничения/риски/читаемость, без монтажных решений.
- Масштаб фиксировать в HEADER; несостыковки масштаба = FAIL.

## [M] QUALITY_GATES
PASS если:
- есть минимум 5 локаций и минимум 6 маршрутов (или по SCALE_HINT)
- есть минимум 3 природных барьера и 3 hazard токена
- travel time логичен и согласован между маршрутами
- XREF_ANCHORS присутствуют (минимум 3)
- READY_GATE = READY

FAIL если:
- “карта без причин”: локации и маршруты перечислены без why_here и constraints
- несостыкованный масштаб (вчера 1 день, сегодня 10 минут без причины)
- VISUAL_NOTES содержит режиссуру/монтажные указания

GAP если:
- нет WORLD_BASELINE
- нет REGION_SET

STOP если:
- попытка утверждать канон без минимальных входов
