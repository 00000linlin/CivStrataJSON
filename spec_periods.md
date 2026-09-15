# 规范：periods.json 生成要求（来自用户 2026-09-12 的指示）

## 1) 时间分卷（22 个 period，主时间轴）


| period_id | 文件名                                          |          时间范围 | 主要历史内容                               |
| --------- | -------------------------------------------- | ------------: | ------------------------------------ |
| P00       | `00_pre_civilization_foundations.json`       | 约前12000—前7000 | 定居化、早期农业、动物驯化、磨制石器、储藏技术              |
| P01       | `01_neolithic_expansion.json`                |   前7000—前4000 | 农业扩散、陶器、纺织、早期灌溉、村落等级化、铜器萌芽           |
| P02       | `02_early_urbanization.json`                 |   前4000—前3000 | 城市化、行政记账、轮、帆船、铜冶金、原始文字、大型神庙组织        |
| P03       | `03_early_bronze_age_states.json`            |   前3000—前2000 | 早期国家、青铜、王权、税赋、官僚、城邦、长距离贸易            |
| P04       | `04_early_iron_age_empires.json`             |   前2000—前1000 | 帝国化、战车、成熟青铜体系、外交体系、成文法、宫殿经济          |
| P05       | `05_classical_axial_age.json`               |    前1000—前500 | 铁器扩散、货币萌芽、大型帝国、骑兵、字母文字、官僚强化          |
| P06       | `06_classical_late_empires.json`                    |      前500—0 | 希腊化、罗马、秦汉、孔雀帝国等；道路、法律、税制、标准化、国家工程    |
| P07       | `07_early_medieval.json`                     |       0—500 | 晚期帝国转型、宗教制度化、庄园经济、丝路重构、纸张扩散          |
| P08       | `08_high_medieval.json`                     |      500—1000 | 伊斯兰世界扩张、唐宋前期、欧洲封建化、印度洋贸易、数学与造纸传播     |
| P09       | `09_high_medieval.json`                      |     1000—1300 | 商业复兴、大学、行会、火药早期、印刷前身、农业技术进步          |
| P10       | `10_late_medieval_early_globalization.json`  |     1300—1500 | 火药武器成熟、活字印刷、远洋导航、蒙古后全球网络、黑死病后的制度变化   |
| P11       | `11_early_modern.json`                       |     1500—1700 | 全球航海、殖民体系、近代财政国家、印刷革命、科学革命、火器国家      |
| P12       | `12_proto_industrial_enlightenment.json`     |     1700—1780 | 启蒙、农业革命、金融制度、蒸汽机早期、机械化萌芽             |
| P13       | `13_first_industrial_revolution.json`        |     1780—1848 | 蒸汽、纺织机械、铁路早期、工业工厂、近代宪政、现代财政          |
| P14       | `14_industrial_nation_state.json`            |     1848—1870 | 民族国家、铁路网络、电报、钢铁工业、行政国家、现代征兵          |
| P15       | `15_second_industrial_revolution.json`       |     1870—1914 | 电力、化学、内燃机、电话、大企业、现代银行、社会保险           |
| P16       | `16_world_wars_and_mass_state.json`          |     1914—1945 | 总体战、无线电、航空、坦克、流水线、计划经济、福利国家扩张        |
| P17       | `17_postwar_industrial_order.json`           |     1945—1973 | 核能、半导体、喷气航空、电视、国际制度、去殖民化、大众消费        |
| P18       | `18_information_transition.json`             |     1973—1991 | 微处理器、个人计算机、卫星通信、金融全球化、产业自动化          |
| P19       | `19_global_internet_age.json`                |     1991—2007 | WWW、移动通信、全球供应链、电子商务、现代数据库和互联网基础设施    |
| P20       | `20_mobile_cloud_platform_age.json`          |     2007—2019 | 智能手机、云计算、社交平台、深度学习、基因编辑、新能源产业化       |
| P21       | `21_ai_biotech_geopolitical_transition.json` |     2020—2026 | 生成式 AI、先进芯片、机器人、新能源体系、生物技术、数字治理与产业政策 |


## 2) 宏观阶段（macro_periods，8 条，引用 period_ids）

```json
除了上面的 22 个时间文件，再建立一个：

text
periods.json


里面定义更大的宏观阶段：


[
  {
    "macro_period_id": "M01",
    "name": "农业与定居社会形成",
    "start": -12000,
    "end": -4000,
    "period_ids": ["P00", "P01"]
  },
  {
    "macro_period_id": "M02",
    "name": "城市国家与青铜文明",
    "start": -4000,
    "end": -1000,
    "period_ids": ["P02", "P03", "P04"]
  },
  {
    "macro_period_id": "M03",
    "name": "铁器帝国与古典国家",
    "start": -1000,
    "end": 0,
    "period_ids": ["P05", "P06"]
  },
  {
    "macro_period_id": "M04",
    "name": "后古典世界与跨区域文明体系",
    "start": 0,
    "end": 1500,
    "period_ids": ["P07", "P08", "P09", "P10"]
  },
  {
    "macro_period_id": "M05",
    "name": "全球化早期与近代国家形成",
    "start": 1500,
    "end": 1780,
    "period_ids": ["P11", "P12"]
  },
  {
    "macro_period_id": "M06",
    "name": "工业化与民族国家",
    "start": 1780,
    "end": 1914,
    "period_ids": ["P13", "P14", "P15"]
  },
  {
    "macro_period_id": "M07",
    "name": "工业化大众社会与世界体系",
    "start": 1914,
    "end": 1973,
    "period_ids": ["P16", "P17"]
  },
  {
    "macro_period_id": "M08",
    "name": "数字化与全球信息社会",
    "start": 1973,
    "end": 2026,
    "period_ids": ["P18", "P19", "P20", "P21"]
  }
]
```

## 3) 产物

只生成 `global_history/periods.json`，顶层为对象，包含两个数组：

- `periods`：22 条，字段 `period_id` / `name_zh` / `file` / `start_year` / `end_year` / `summary`（1-2 句中文，说明该时段的结构性变化）/ `highlights`（3-6 个中文关键词）
- `macro_periods`：8 条，字段 `macro_period_id` / `name_zh` / `start_year` / `end_year` / `period_ids`

约束：`end_year` 用四位数字或负数（公元前为负），不要用字符串；范围必须首尾相接、无重叠、覆盖 -12000 至 2026；JSON 必须为合法 UTF-8。

时间区间采用“共享过渡年”约定：相邻 period 或 macro period 可以共享边界年份，但同一事件只能由一个明确的 `period_id` 归属。`start_year` 与 `end_year` 是包含边界的报告窗口；“无重叠”指事件归属和已分配的时间段不重复，不把共享过渡年重复计入两个 period 的事件集合。查询实现必须优先使用事件的 `period_id`，不得仅凭闭区间年份推断唯一归卷。
