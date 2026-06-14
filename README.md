# Fishery Research Idea & Battle — Claude Skill

**A Claude Code Skill that acts as your senior fisheries scientist advisor for fisheries research.** It puts data first — before any literature review or opinion — searches the latest fisheries journals and data repositories, challenges your ideas like a rigorous reviewer, recommends target journals across four tiers, and guides you through the full lifecycle of a research idea from rough intuition to submission-ready contribution.

[English](#english) · [中文](#中文)

---

## English

### What It Does

`fishery-research-idea-and-battle` gives you a senior fisheries scientist in your Claude session — one who has reviewed for Fish and Fisheries, ICES Journal of Marine Science, Fisheries Research, CJFAS, Reviews in Fish Biology and Fisheries, Fisheries Oceanography, Marine Policy, Ecological Modelling, MEPS, Global Change Biology, and many more. They have watched research directions rise and die, and know that in fisheries, **data is the binding constraint on almost every idea**.

**Six core capabilities:**

| Mode | What You Get |
|------|-------------|
| **Data Assessment (Mandatory Step 0)** | Five-dimension data audit: species (with FishBase lookup), spatial scope, temporal scope, data types, data access. Scientific Data journal search for data descriptor papers. Scope-matching analysis. |
| **Idea Evaluation** | Field snapshot from real recent papers → data feasibility check → what's genuinely interesting → where to push back → specific path forward. Always data-first: an elegant idea with impossible data requirements isn't a research plan. |
| **Battle Mode** | Full devil's advocate as a hostile-but-fair fisheries journal reviewer. Data-limitation objections, ecological realism, statistical identifiability, management applicability. Every weakness surfaced. |
| **Idea Generation** | Two-tier proposals: Tier 1 (Fish and Fisheries / PNAS ambition, high ceiling, explicit data risk) + Tier 2 (ICES JMS / Fisheries Research / CJFAS — practical, achievable with existing datasets) |
| **Landscape Mode** | Paint the map — key research groups (NOAA, ICES, UBC, CSIRO, CEFAS, IMR, IFREMER), dominant open problems, data infrastructure status, where the field is going |
| **Journal Recommendation** | Four-tier journal map (17 journals across Flagship → Top Specialized → Solid Specialized → Wider-Audience). First-choice + backup + stretch journal, each with specific reasoning based on idea type, novelty, data richness, and audience. |

**What makes it different from just asking Claude:**

- **Data first, always** — Before any literature search or opinion, assesses species (FishBase), spatial/temporal scope, data types, and access. Searches Scientific Data and ESSD for data descriptor papers that can transform feasibility overnight.
- **Searches before speaking** — 5 parallel searches (data papers, landscape surveys, frontier papers, graveyard of failed approaches, institutional activity) before giving any opinion
- **Cites real papers and real data sources** — never fabricates references or datasets; if uncertain, says so and searches
- **Mentor first, critic second** — understands the idea deeply before stress-testing it
- **Knows the graveyard** — explicitly searches what was tried and abandoned, why it stalled, and whether conditions have changed
- **Species-aware** — proactively checks FishBase for life history parameters (K, L∞, M, trophic level, habitat, distribution) that fundamentally constrain what analyses are feasible
- **Scope-matching** — flags spatial/temporal mismatches between data and inference that kill papers at review

---

### The Data-First Philosophy

In computer science, you download ImageNet. In fisheries, you cannot download the ocean. This skill treats data assessment as **Step 0 — non-negotiable, before any literature search**:

1. **Five-dimension data audit:** Species → FishBase lookup (growth, mortality, habitat, trophic level, distribution). Spatial scope → bay / shelf / basin? Single or multi-jurisdiction? Temporal scope → 3-year project / 20-year hindcast / 50-year reconstruction? Data types → catch / survey / biological / environmental / socio-economic? Data access → in hand / public / agency request / needs collection?

2. **Data paper search:** Always checks Scientific Data (nature.com/sdata) and ESSD for data descriptor papers — peer-reviewed datasets designed for reuse — that can make an idea go from "impossible" to "doable in a semester."

3. **Scope-matching analysis:** Flags the 6 most common time/space mismatches that get papers rejected — spatial scope too small for the ecological process, too large for the data, temporal scope too short for the signal, too long for stationarity, scale mismatch between data sources, and jurisdictional mismatch.

4. **Data source recommendations:** A built-in database map covering FAO FishStat, RAM Legacy, ICES DATRAS, NOAA Stock Assessments, Global Fishing Watch, OBIS/GBIF, Copernicus Marine, FishBase/SeaLifeBase, Scientific Data, ESSD, RFMO databases, and national agency data — with what each contains and how to access it.

---

### Installation

```bash
# Project-level (recommended)
mkdir -p /path/to/your/project/.claude/skills/
cp -r fishery-research-idea-and-battle /path/to/your/project/.claude/skills/

# Global (available in all projects)
cp -r fishery-research-idea-and-battle ~/.claude/skills/
```

**Verify installation:**
```
/skills  →  look for "fishery-research-idea-and-battle"
```

---

### Usage

No special commands needed. Just talk about fisheries research naturally — the skill triggers automatically when it detects research ideation or academic debate context in fisheries science.

**Idea evaluation (data-first):**
```
I want to explore using environmental DNA for stock assessment of Pacific sardine. Is there potential here?
```
→ The skill will first ask: what's your spatial/temporal scope? Do you have eDNA time series or just snapshot samples? Are there concurrent trawl surveys for validation? Then search FishBase for sardine life history, Scientific Data for relevant eDNA datasets, and the literature before giving an opinion.

**Battle mode:**
```
Battle this idea: use machine learning on daily catch reports to replace annual stock assessments for tuna fisheries
```

**Direction recommendations (two-tier):**
```
Suggest some research directions in climate-adaptive fisheries management that could reach top journals
```

**Field landscape:**
```
What's happening in the data-poor stock assessment space right now? What methods are actually being adopted by RFMOs?
```

**Journal recommendation:**
```
Where should I submit this? It's a spatial stock assessment method using VAST, tested on North Sea cod and Norwegian herring.
```

**Mentorship:**
```
I've been working on surplus production models for three years. Should I pivot to something else or go deeper?
```

---

### What the Skill Does First (Always, Non-Negotiable)

Before giving any opinion, it completes a **mandatory data-first workflow**:

1. **Five-dimension data audit** — species (FishBase lookup), spatial scope, temporal scope, data types, data access
2. **Scientific Data / ESSD search** — find data descriptor papers that may transform feasibility
3. **5 parallel literature searches** — landscape surveys, frontier papers, graveyard of failed approaches, institutional activity tracking

It presents a **data assessment** and a **field snapshot** before engaging with your idea, so every opinion is grounded in what data actually exists and what the current literature says — not training-cutoff knowledge.

---

### Example Output

**Prompt:** *"I want to use VAST (vector autoregressive spatio-temporal models) for a tropical mixed-species trawl fishery. Is there potential?"*

> **Data assessment first:** Before I search the literature — what's your spatial scope (single fishing ground or the whole EEZ?), temporal scope (how many years of data?), and what data types do you have? Specifically: do you have fishery-independent survey data, or only commercial catch and effort? VAST models are data-hungry for spatial contrasts — they need survey data across a spatial gradient to estimate spatial correlations, not just catch locations. Also — which species? If it's mixed-species, are we talking about a handful of target species or dozens? FishBase life histories matter here: tropical multi-species fisheries often have very different K and M values across the species mix.
>
> *(After user provides details, then searches literature and data papers)*
>
> **Field snapshot:** VAST has been rapidly adopted in the US (NOAA) and North Atlantic (ICES) for single-species spatial index standardization. Grüss et al. (2024) extended it to multi-species with joint species distribution models, but the test case was 5 species in the Gulf of Alaska with 20+ years of survey data. Thorson et al. (2023) explicitly warn about the data requirements — you need spatial contrasts in abundance to estimate spatial correlations. I found no data descriptor paper in Scientific Data for tropical mixed-species trawl surveys at the resolution you'd need. That doesn't mean the idea is dead — but the data bottleneck is real, and you'll need to show how you handle it.
>
> For a journal target: if you can validate with simulation + one real system, **Fisheries Research** or **CJFAS** are realistic. If the data proves richer than expected and you can show cross-system generality, **ICES JMS** or **Methods in Ecology and Evolution** become options.

---

### Journal Recommendation Map

The skill has a built-in four-tier journal map (17 journals):

- **Tier 1 — Flagship:** Fish and Fisheries, Nature/Science, PNAS, Nature Sustainability
- **Tier 2 — Top Specialized:** ICES JMS, CJFAS, Fisheries Research, Reviews in Fish Biology and Fisheries, Fisheries Oceanography
- **Tier 3 — Solid Specialized:** MEPS, Transactions of the AFS, Fishery Bulletin, Journal of Fish Biology, Ecological Modelling, Marine Policy
- **Tier 4 — Wider-Audience:** Global Change Biology, Conservation Biology / Biological Conservation, Ecological Applications, Methods in Ecology and Evolution, Frontiers in Marine Science

Every journal recommendation comes with: **first-choice + reasoning**, **backup option**, and (if applicable) **stretch goal**. Never just journal names without rationale.

---

### See It In Action: Side-by-Side Comparison

Open [`example.md`](example.md) for a full side-by-side comparison using the research topic **"Response mechanism of Pacific saury population dynamics to the Kuroshio Current in the Northwest Pacific"**. The example shows how vanilla Claude gives vague encouragement and generic tool suggestions, while the skill-equipped Claude:

- Queries **FishBase** for saury life history (K, L∞, age~2) and infers modeling implications — a short-lived species needs a fundamentally different framework from long-lived ones
- Conducts a **five-dimension data audit** — identifies that the Kuroshio large meander operates on interannual-to-decadal scales, saury migrate >500 km annually, and 1°×1° SST averages erase the fine-scale thermal structure the fish actually experience
- Runs **5 parallel searches** including Scientific Data for data descriptor papers, finding that no public dataset for this fishery exists → flags the data-access bottleneck before the user commits to an unfeasible design
- Cites **real papers** (Yatsu 2013, 2019; Liu 2022, 2023; NPFC 2023) and frames novelty not as "we used method X" but as a mechanistic hypothesis: "Kuroshio large meander → shifts in spawning ground transport → altered proportion of larvae entering high-productivity Oyashio water → recruitment variability"
- Gives **three-tier journal recommendation** with conditional logic: Fisheries Oceanography (first choice) → ICES JMS (if methods are rigorous enough) → Fish and Fisheries (only if cross-species generality is demonstrated)
- Provides **three concrete paths forward** depending on data availability, from "step back and reframe for Chinese fishery data only" to "if you can access FRA long-term surveys back to the 1980s, the paper tier changes"

---

### Requirements

- Claude Code (any version)
- No additional API keys, MCP plugins, or dependencies required
- Works out of the box
- WebSearch and WebFetch tools are used for literature and data paper searches (automatically triggered by the skill)

---

### License

MIT

---

## 中文

### 功能介绍

`fishery-research-idea-and-battle` 在你的 Claude 会话中提供一位资深渔业科学家作为科研顾问——审稿经验覆盖 Fish and Fisheries、ICES JMS、Fisheries Research、CJFAS、Reviews in Fish Biology and Fisheries、Fisheries Oceanography、Marine Policy、Ecological Modelling、MEPS、Global Change Biology 等顶级期刊。他们见过研究方向的兴衰，深知在渔业研究中**数据是几乎所有想法的约束瓶颈**。

**六大核心能力：**

| 模式 | 你会得到什么 |
|------|------------|
| **数据评估（强制第0步）** | 五维度数据审计：物种（FishBase 查询）、空间范围、时间范围、数据类型、数据获取方式。Scientific Data 期刊数据描述论文搜索。时空匹配度分析。 |
| **Idea 评估** | 基于真实文献的领域快照 → 数据可行性检查 → 哪里真正有意思 → 哪里需要推敲 → 具体前进路径。始终数据优先：一个数据要求不可能实现的优雅想法不是研究计划，是愿望。 |
| **Battle 模式** | 全力扮演挑剔的渔业期刊审稿人。数据限制、生态真实性、统计可识别性、管理适用性——每个弱点都被挖出来。 |
| **Idea 生成** | 双层推荐：Tier 1（Fish and Fisheries / PNAS 级别创新，高天花板，明确标注数据风险）+ Tier 2（ICES JMS / Fisheries Research / CJFAS 级别——务实、数据可支撑、近期可发表）|
| **Landscape 模式** | 画地图——关键研究组（NOAA、ICES、UBC、CSIRO、CEFAS、IMR、IFREMER）、主要开放问题、数据基础设施现状、领域发展方向 |
| **期刊推荐** | 四级期刊地图（17本期刊，从旗舰级 → 顶级专业课 → 扎实专业课 → 更广受众）。第一选择 + 备选 + 冲刺期刊，每本都给出基于论文类型、创新程度、数据丰富度和目标读者的具体理由。 |

**和直接问 Claude 的区别：**

- **数据优先，始终如一** — 先于任何文献搜索和意见之前，评估物种（FishBase）、时空范围、数据类型和获取方式。搜索 Scientific Data 和 ESSD 寻找可以一夜之间改变可行性的数据描述论文。
- **先搜索再开口** — 5 路并行搜索（数据论文、领域综述、前沿论文、失败方向的墓地、机构动态）之后才给意见
- **引用真实论文和真实数据源** — 不编造文献或数据集；不确定就搜索，搜完再说
- **导师先于批评者** — 先深度理解你的想法，再压力测试它
- **知道墓地** — 专门搜索什么被试过了、为什么停了、条件是否已经改变
- **物种感知** — 主动查询 FishBase 获取生活史参数（K、L∞、M、营养级、栖息地、分布），这些参数从根本上约束了可行的分析框架
- **时空匹配检查** — 标记那些在审稿时会被毙掉的数据-推断时空不匹配问题

---

### 数据优先理念

在计算机科学中，你下载 ImageNet。在渔业中，你无法下载海洋。这个技能将数据评估作为**第0步——不可协商，在文献搜索之前**：

1. **五维度数据审计：** 物种 → FishBase 查询（生长、死亡、栖息地、营养级、分布）。空间范围 → 海湾 / 陆架 / 海盆？单一还是多辖区？时间范围 → 3年项目 / 20年后报 / 50年重建？数据类型 → 捕捞 / 调查 / 生物 / 环境 / 社会经济？数据获取 → 已有 / 公开 / 需向机构申请 / 需要从头采集？

2. **数据论文搜索：** 始终检查 Scientific Data（nature.com/sdata）和 ESSD，寻找数据描述论文——这些是经过同行评审、专为重复使用设计的数据集——可以让一个想法从"不可行"变成"一学期能做出来"。

3. **时空匹配分析：** 标记 6 种最常见的导致论文被拒的时空不匹配——空间范围太小不足以推断种群动态、太大数据无法支撑结论、时间序列太短检测不到信号、太长平稳性假设不成立、多源数据尺度不一致、管辖范围不匹配。

4. **数据源推荐：** 内建的数据库地图，覆盖 FAO FishStat、RAM Legacy、ICES DATRAS、NOAA Stock Assessments、Global Fishing Watch、OBIS/GBIF、Copernicus Marine、FishBase/SeaLifeBase、Scientific Data、ESSD、RFMO 数据库和国家机构数据——每项都标注了包含什么、如何获取。

---

### 安装方式

```bash
# 项目级（推荐）
mkdir -p /path/to/your/project/.claude/skills/
cp -r fishery-research-idea-and-battle /path/to/your/project/.claude/skills/

# 全局（对所有项目生效）
cp -r fishery-research-idea-and-battle ~/.claude/skills/
```

**验证安装：**
```
/skills  →  找到 "fishery-research-idea-and-battle"
```

---

### 使用方法

不需要特殊命令。直接说渔业科研相关的话，技能会自动触发。

**Idea 评估（数据优先）：**
```
我想探索用环境 DNA 做太平洋沙丁鱼的资源评估，有没有潜力？
```
→ 技能会首先问：你的时空范围是什么？你有 eDNA 时间序列还是只是快照采样？有没有同步的拖网调查做验证？然后搜索 FishBase 获取沙丁鱼生活史参数，搜索 Scientific Data 找相关 eDNA 数据集，搜索文献之后才给意见。

**Battle 模式：**
```
帮我 battle 这个想法：用机器学习分析日报捕捞数据，替代金枪鱼渔业的年度资源评估
```

**推荐研究方向（双层）：**
```
给我推荐一些气候适应性渔业管理领域值得做的方向，要能发好期刊
```

**领域全景：**
```
数据有限的种群评估现在在做什么？有什么方法真的被 RFMO 采用了？
```

**期刊推荐：**
```
这个该投哪里？是一个用 VAST 做空间资源评估的方法，用北海鳕鱼和挪威鲱鱼做了测试
```

**导师模式：**
```
我做了三年剩余产量模型了，是应该转向别的还是继续深入？
```

---

### 技能每次都会先做的事（强制，不可跳过）

在给出任何意见之前，完成**强制性的数据优先工作流**：

1. **五维度数据审计** — 物种（FishBase 查询）、空间范围、时间范围、数据类型、数据获取方式
2. **Scientific Data / ESSD 搜索** — 寻找可能改变可行性评估的数据描述论文
3. **5 路并行文献搜索** — 领域综述、前沿论文、失败方向的墓地、机构动态追踪

先给出**数据评估**和**领域快照**，再讨论你的想法——每个意见都基于当前真实存在的数据和文献，而不是训练截止日期的知识。

---

### 示例输出

**提示：** *"我想在热带混合物种拖网渔业中应用 VAST（向量自回归时空模型），有潜力吗？"*

> **数据评估优先：** 在我搜索文献之前——你的空间范围是什么（单个渔场还是整个 EEZ？），时间范围（有多少年的数据？），你有什么数据类型？具体来说：你有渔业独立调查数据，还是只有商业捕捞和努力量数据？VAST 模型对空间对比度要求很高——它们需要跨空间梯度的调查数据来估计空间相关性，而不仅仅是捕捞位置。另外——哪些物种？如果是混合物种，我们说的是几个目标物种还是几十个？FishBase 的生活史参数很关键：热带多物种渔业中不同物种的 K 值和 M 值通常差异很大。
>
> *（用户提供细节后，然后搜索文献和数据论文）*
>
> **领域快照：** VAST 已在美国（NOAA）和北大西洋（ICES）被快速用于单物种空间指数标准化。Grüss 等（2024）将其扩展到多物种联合物种分布模型，但测试案例是阿拉斯加湾的 5 个物种，有 20+ 年的调查数据。Thorson 等（2023）明确警告了数据需求——你需要丰度的空间对比来估计空间相关性。我在 Scientific Data 中没有找到你所需分辨率的关于热带混合物种拖网调查的数据描述论文。这不意味着这个想法死了——但数据瓶颈是真实存在的，你需要展示如何处理它。
>
> 关于期刊目标：如果你能用模拟 + 一个真实系统验证，**Fisheries Research** 或 **CJFAS** 是现实的选择。如果数据比预期的更丰富，且能展示跨系统的普适性，**ICES JMS** 或 **Methods in Ecology and Evolution** 就可以成为选项。

---

### 期刊推荐地图

技能内建四级期刊地图（17本期刊）：

- **Tier 1 — 旗舰级：** Fish and Fisheries、Nature/Science、PNAS、Nature Sustainability
- **Tier 2 — 顶级专业课：** ICES JMS、CJFAS、Fisheries Research、Reviews in Fish Biology and Fisheries、Fisheries Oceanography
- **Tier 3 — 扎实专业课：** MEPS、Transactions of the AFS、Fishery Bulletin、Journal of Fish Biology、Ecological Modelling、Marine Policy
- **Tier 4 — 更广受众：** Global Change Biology、Conservation Biology / Biological Conservation、Ecological Applications、Methods in Ecology and Evolution、Frontiers in Marine Science

每次期刊推荐都包含：**第一选择 + 理由**、**备选期刊**、以及（如适用）**冲刺目标**。绝不只列期刊名而没有理由。

---

### 实战对比：有无 Skill 的差异

打开 [`example.md`](example.md) 查看完整的一对一对比，研究主题为**"西北太平洋秋刀鱼种群变动对黑潮的响应机制"**。示例展示了裸 Claude 只能给出泛泛的鼓励和通用的工具建议，而装备了 Skill 的 Claude 则会：

- 查询 **FishBase** 获取秋刀鱼生活史参数（K, L∞, age~2），并推断建模含义——短寿命物种需要与长寿命物种完全不同的建模框架
- 进行**五维度数据审计**——识别出黑潮大弯曲在年际到年代际尺度上运行、秋刀鱼每年洄游 >500 km、1°×1° SST 平均值会抹去鱼类实际经历的细尺度温度场结构
- 执行 **5 路并行搜索**，包括 Scientific Data 搜索数据描述论文，发现该渔业没有公开数据集 → 在用户投入不可行研究设计之前提前预警数据获取瓶颈
- 引用**真实论文**（Yatsu 2013, 2019; Liu 2022, 2023; NPFC 2023），并将新颖性框定为机制假说："黑潮大弯曲 → 产卵场输送路径改变 → 仔稚鱼进入亲潮高生产力区域的比例变化 → 补充量波动"
- 给出**三级期刊推荐**附带条件逻辑：Fisheries Oceanography（第一选择）→ ICES JMS（如果方法够严谨）→ Fish and Fisheries（仅当能证明跨物种普适性）
- 提供**三条具体前进路径**取决于数据可得性，从"退一步，仅针对中国渔业数据框定问题"到"如果拿到 FRA 追溯到 1980 年代的长期调查数据，论文层级完全不同"

---

### 环境要求

- Claude Code（任意版本）
- 无需额外 API key、MCP 插件或依赖
- 开箱即用
- 使用 WebSearch 和 WebFetch 工具进行文献和数据论文搜索（技能自动触发）

---

### 许可证

MIT
