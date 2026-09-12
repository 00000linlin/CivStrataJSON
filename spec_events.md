# 规范：events JSON 生成要求（第一卷 P00）

## 1) 目录与文件

```
global_history/
└── events/
    └── 00_pre_civilization_foundations.json     ← 本卷唯一产物
```

## 2) 顶层结构

```json
{
  "period_id": "P00",
  "period_name_zh": "文明形成前的定居与生产基础",
  "start_year": -12000,
  "end_year": -7000,
  "events": [ ... ]
}
```

## 3) 单条事件模型（字段必须齐全）

```json
{
  "event_id": "EVT_TECH_AGRICULTURE_LEVANT_001",
  "event_type": "technology_emergence | technology_diffusion | institution_emergence | institution_change | demography | settlement | economy | military | knowledge | environment",
  "name_zh": "黎凡特地区野生谷物管理与早期栽培",
  "period_id": "P00",
  "date": {
    "year_estimate": -9500,
    "range_start": -10000,
    "range_end": -9000,
    "precision": "millennium | century | half_century | decade | year | unknown",
    "confidence": "high | medium | low"
  },
  "geography": {
    "historical_region": "黎凡特",
    "historical_polities": [],
    "modern_areas": ["以色列", "巴勒斯坦", "叙利亚", "约旦"]
  },
  "domains": ["agriculture", "subsistence"],
  "technology_ids": ["TECH_PLANT_CULTIVATION"],
  "institution_ids": [],
  "summary_zh": "1-3 句中文，说明发生了什么、为什么重要（对生产力/组织/传播的意义）",
  "effects": {
    "production": [],
    "state_capacity": [],
    "knowledge_diffusion": [],
    "military": [],
    "trade": []
  },
  "source_ids": [],
  "notes": "可选：争议点或年代不确定性说明"
}
```

## 4) 硬性约束

1. **只写 `events` 数组**，20–35 条，覆盖本卷 6 个主题：定居化、早期农业、动物驯化、磨制石器与工具、储藏与建筑、社会复杂化萌芽。
2. **横向覆盖**：至少覆盖西南亚（黎凡特/扎格罗斯）、东亚（长江/黄河）、中美洲、安第斯、非洲（尼罗河/萨赫勒）、新几内亚等独立起源中心，不要把事件集中在一个区域。
3. **每条事件的年代必须有范围**：`range_start <= year_estimate <= range_end`，且全部落在 -12000 到 -7000 之间；不确定就降低 precision 与 confidence，**不要编造精确年份**。
4. `event_id` 唯一，格式 `EVT_<大类>_<主题>_<区域>_<三位序号>`，全大写英文与下划线。
5. `technology_ids` / `institution_ids` 用统一大写命名（如 `TECH_POTTERY`、`INST_STORAGE_GRANARY`），本卷内保持同名一致，供后续卷引用。
6. `effects` 五个键必须存在（可为空数组），有影响的填短语（中文，如「人口承载力上升」）。
7. `source_ids` 本卷可为空数组（来源库尚未建立）。
8. 不要写人物传记式内容；不要把事件挂在「某朝/某王」之下，那属于后续卷。
9. 输出为合法 UTF-8 JSON；写完后用 `python3 -c "import json;json.load(open(...))"` 自检，并打印事件条数与区域分布统计。
10. **区域分布要重心分明，禁止「一区一条」平均铺开**：核心区域（近东、东亚、南亚、欧洲与地中海、非洲、美洲各文明中心）每个 3–6 条；次要区域（东南亚、大洋洲、日本列岛、北美等）至少 1 条。若某卷总条数 30 条左右而区域数超过 20 个，说明粒度分配失败，必须为核区补足条数。
11. 同一技术在同一区域的多个阶段（出现 / 扩散 / 成熟 / 被替代）应拆成不同事件，而不是合并成一条——这正是「事件而非条目」的意义。
