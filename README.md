**在线演示（GitHub Pages）：https://wadesha.github.io/foreign-trade-data-framework/**

# 外贸后台全场景数据补充体系 · 项目展示

从最底层数据元模型（实体 · 属性 · 关系）出发，构建外贸后台全场景数据补充框架，并通过**家族化数据集**模拟生成可复现的演示数据。涵盖多平台、多渠道、全品类、ROI 监控四个扩展维度。

> 仓库地址：https://github.com/Wadesha/foreign-trade-data-framework
> 部署 GitHub Pages 后，第一行链接即可访问（见下方「部署到 GitHub Pages」）。

## 在线演示内容（10 个页签）

| 页签 | 内容 |
|---|---|
| **外贸决策模拟** | **关卡制业务模拟**：你扮演跨境电商运营主管，经历 10 个真实决策场景（投放预算/Prime Day/价格战/红海危机/账期谈判/锁汇/红人营销/库存积压/平台扩张/旺季备货），每场景 4 个选项卡片，选完立即展示经营数据变化 + 显眼的一句话评价，最终结算年度评级（S~D） |
| 总览仪表盘 | 8 个 KPI（家族/订单/平台/活动/实体/营收/广告支出/完整度）+ 6 张图表（平台营收/ROAS/品类/趋势/地域/状态环图） |
| 数据家族 | 选择任一客户（Root），展开完整家族树：平台列表 → 订单 → 行项 → 发票 → 付款 → 发货 → 营销归因 |
| 平台对比 | 6 大平台（Amazon / Alibaba / Shopify / eBay / TikTok Shop / Walmart）营收/佣金/转化率/广告花费对比 |
| 营销渠道 | 7 渠道（PPC/SEO/社媒/邮件/KOL/展会/内容）ROAS/CAC/CPA/LTV:CAC 矩阵 + 活动明细表 |
| 品类分析 | 10 个 HS 品类销售额/毛利率/订单量/增长率排行 |
| 补充演示 · 血缘 | 每条记录展示：实体 × 属性 从 NULL → 算子 → 关系路径 → 补充值 |
| 订单明细 | 订单分页表（含平台、营销归因列） |
| 模拟引擎 | 可调种子与家族数量，实时重新生成；相同种子 = 完全相同数据 |
| 质量报告 | 7 项质量检查 + 9 个家族标签「补充前→补充后」完整度对比 |

## 项目结构

```
├── index.html                             # 交互式项目演示（GitHub Pages 入口）
├── foreign-trade-data-framework.html      # 底层框架与体系化知识文档（含扩展章节）
└── README.md
```

## 核心概念速览

- **元模型**：任何数据 = 实体（Entity）+ 属性（Attribute）+ 关系（Relation）；**22+ 种核心实体、9 个家族标签、11 种关系代数**
- **数据补充**：本质是「沿着关系路径传播信息」，由 6 种原子算子执行 —— Lookup / Compute / Derive / Merge / Fill / Validate
- **家族化数据集**：以客户为 Root 的家族树（Root → Parent → Child → Leaf），保证因果一致性与模拟逼真度
- **扩展维度**：6 个平台（Amazon/Alibaba/Shopify/eBay/TikTok Shop/Walmart）、7 个营销渠道（PPC/SEO/社媒/邮件/KOL/展会/内容）、10 个 HS 品类、ROI 监控（ROAS/CAC/LTV:CAC/CPA）
- **缺失注入 → 补充 → 血缘**：演示数据先按真实比例注入缺失（region 12%、credit 15%、HS Code 8%、incoterm 10%、ETA 20%、平台佣金 15%、营销归因 20%、ROI 数据 25%），再由引擎补充并记录完整血缘

## 本地运行

纯静态页面，零依赖，直接用浏览器打开即可：

```bash
# 方式一：直接打开
open index.html

# 方式二：本地静态服务
python3 -m http.server 8000
# 访问 http://localhost:8000
```

## 部署到 GitHub Pages

1. 将本目录推送到 GitHub 仓库（`index.html` 位于仓库根目录）
2. 仓库 **Settings → Pages → Build and deployment → Source** 选择 `main` 分支 / 根目录
3. 访问 `https://wadesha.github.io/foreign-trade-data-framework/`

## 技术说明

- 单文件 `index.html`，纯原生 HTML / CSS / JavaScript，无任何外部依赖，离线可用
- 模拟数据由浏览器端 **mulberry32 种子化随机引擎**实时生成：默认种子 42、50 个客户家族（约 1500+ 实体、1000+ 关系边、200+ 血缘记录）
- 层叠式分布约束贴近真实外贸：地域（EU 30% / NA 25% / APAC 20%…）、币种（USD 55% / EUR 20%…）、订单金额（对数正态）、月度趋势（24 个月）
- 性能策略：订单表分页（10 条/页）、血缘记录仅展示种子化抽样的前 18 条、营销活动表仅展示前 12 条、图表基于聚合而非明细
- 知识体系文档 `foreign-trade-data-framework.html` 包含完整的总览图，可用浏览器打开阅读