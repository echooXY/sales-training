<p align="center">
  <h1 align="center">多角色AI销售实战训练系统 · AIDI Studio Training</h1>
  <p align="center">企业销售团队的 AI 实战练兵场 — Prompt 定义角色，LLM 生成战场</p>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/PRD-V1.1.0-blue" alt="PRD">
  <img src="https://img.shields.io/badge/Multi--Agent-Lead%2BCustomer-6E56CF" alt="Multi-Agent">
  <img src="https://img.shields.io/badge/React-18-61DAFB?logo=react" alt="React">
  <img src="https://img.shields.io/badge/Python-3.12-3776AB?logo=python" alt="Python">
  <img src="https://img.shields.io/badge/LLM-Claude%20%2F%20GPT--4o-1C3C3C" alt="LLM">
  <img src="https://img.shields.io/badge/Voice-WebRTC%20%2B%20ASR%2FTTS-009688" alt="Voice">
  <img src="https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/Redis-7-DC382D?logo=redis" alt="Redis">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="License">
</p>

> 面向连锁零售与金融保险行业的 **B 端 AI 销售陪练 SaaS 平台**——不依赖预标注对话数据，仅凭角色 Prompt 即可生成逼真 AI 顾客，支持文字与语音双模式；培训管理者可在 30 分钟内完成从场景配置到全团队陪练部署，并用 5 维雷达图量化培训 ROI。

---

## 在线预览

| 原型 | 在线预览地址 |
|------|-------------|
| 学员端（移动端） | `https://echooxy.github.io/sales-training/prototype/营销导购陪练智能体-学员端.html` |
| 管理端（B 端后台） | `https://echooxy.github.io/sales-training/prototype/营销导购陪练智能体-管理端.html` |
| 信息架构图（8 大域 · 字段级设计） | `https://echooxy.github.io/sales-training/prototype/AI销售陪练系统-信息架构图.html` |
| 功能模块图（6 大模块 · 交互思维导图） | `https://echooxy.github.io/sales-training/prototype/AI销售陪练系统-功能模块图.html` |

---

## 项目速览

| 维度 | 内容 |
|------|------|
| **痛点** | 新人上岗慢（45 天）、培训师人效瓶颈（1:10）、培训质量不可控、ROI 无法量化 |
| **方案** | 多 Agent 角色扮演陪练 + Prompt 即场景零标注冷启动 + 独立 AI 评估 + B 端数据看板 |
| **效果** | 上岗周期 45→20 天、培训师人效 1:10→1:80、评估偏差 ≤5 分、5 维雷达图归因培训 ROI |

---

## 详细项目经历（STAR）

### S — 用户洞察（Situation）
连锁零售与金融保险行业的销售团队普遍面临"人带人"培训困局：老员工 1 对 1 带教人均耗时 20h+、新人上岗周期长达 45 天；1 名培训师最多只能带 10 名新人；培训效果只有出勤率统计，缺乏能力提升数据，管理者无法向上证明培训 ROI。围绕 **销售 VP / 培训经理 / 区域主管 / 一线新人** 四类角色梳理诉求，锁定"练得少、评不准、算不清"三大结构性矛盾。

### T — 产品定位（Task）
将产品定义为**面向连锁零售与金融保险行业的 B 端 AI 销售陪练 SaaS 平台**，用一句话统领全局设计——"30 分钟创建场景，7×24 自动陪练，量化培训 ROI"。目标：MVP 阶段验证 5 家种子客户，Phase 2 实现 ≥50 家付费客户、ARR ≥ ¥500 万。

### A — 关键决策（Action）
- **提出"Prompt 即场景"差异化定位**：不依赖预标注对话数据，编写角色 Prompt 即可在 30 分钟内创建新行业场景，把竞品的"周级"冷启动压缩到分钟级，已覆盖 6 大业务场景与 L1→L4 四级难度体系。
- **设计多 Agent 角色扮演引擎**：Lead Agent + N 个 Customer Agent，通过 JSONL 邮箱异步通信模拟"真人商量"，L4 支持 3+ 角色同屏多人决策；配合 microcompact + auto_compact + manual 三层上下文压缩，30–80 轮对话后仍保持角色一致性。
- **构建独立 AI 评估闭环**：陪练结束自动派生评估子 Agent，独立于对话链路输出 5 维 16 粒度评分（沟通 / 需求挖掘 / 产品介绍 / 异议处理 / 成交推进），保证评估中立、偏差 ≤5 分。
- **规划文字 + 语音双模式**：语音基于 WebRTC 实时通话，定义端到端延迟 ≤800ms、ASR 准确率 ≥95%、TTS MOS ≥4.0 等 5 项性能指标，支持 PTT / VAD / 打断三种交互模式与多路热备降级策略。
- **设计 B 端管理后台**：团队数据看板、能力雷达图、培训任务下发、RBAC 四级权限、审计日志与 ROI 报告，覆盖 VP / 培训经理 / 区域主管 / 学员四级角色。
- **完成商业化闭环**：4 家竞品深度分析（Megaview / FindAI / Hyperbound / 得助智能）输出多维功能矩阵，制定四档 SaaS 定价（免费试用 → ¥19.8 万/年企业版）与 GTM 上市策略。

### R — 核心指标（Result）
| 指标 | 目标 |
|------|------|
| 北极星指标 | 每周完成陪练并收到改进建议的活跃学员数 |
| 新人上岗周期 | ≤20 天（基线 45 天） |
| 培训师人效 | ≥1:80（基线 1:10） |
| 评估偏差 | ≤5 分 |
| 企业续费率 | ≥85% |
| ARR / 付费客户 | ≥¥500 万 / ≥50 家（Phase 2） |

### 项目成果
输出 **完整 PRD**、GTM 策略、技术可行性论证、指标仪表盘设计、竞品分析，形成"规划 → 论证 → 商业化"完整闭环；并交付高保真交互原型（学员端 / 管理端）及交互式架构图（信息架构图 / 功能模块图），覆盖登录、RBAC、多 Agent 切换、评估报告、对话回放等完整交互链路。

---

## 产出物索引

### 产品文档（`docs/`）
| 文档 | 说明 |
|------|------|
| [营销导购AI陪练系统-PRD.md](docs/营销导购AI陪练系统-PRD.md) | 完整产品需求文档 |
| [GTM策略草案.md](docs/GTM策略草案.md) | 上市策略：定价、渠道、种子客户获取 |
| [技术可行性论证.md](docs/技术可行性论证.md) | 逐模块技术路线选型与风险评估 |
| [指标仪表盘设计.md](docs/指标仪表盘设计.md) | 6 大模块数据看板与埋点设计 |
| [竞品分析摘要表.md](docs/竞品分析摘要表.md) | 4 产品 × 8 维度竞品深度对比 |

### 交互原型（`prototype/`）
| 原型 | 说明 |
|------|------|
| [营销导购陪练智能体-学员端.html](prototype/营销导购陪练智能体-学员端.html) | 手机移动端全链路（新手引导 / 陪练 / 评估 / 成长曲线） |
| [营销导购陪练智能体-管理端.html](prototype/营销导购陪练智能体-管理端.html) | B 端后台（SSO 登录 / 看板 / 场景 / 团队 RBAC / 报告推送） |
| [AI销售陪练系统-信息架构图.html](prototype/AI销售陪练系统-信息架构图.html) | 8 大域 ER 级信息架构（PK/FK/JSON/前端使用标注） |
| [AI销售陪练系统-功能模块图.html](prototype/AI销售陪练系统-功能模块图.html) | 6 大模块交互式思维导图（含任务 Tab 3 个子模块） |

---

## 核心差异化高亮

### ① Prompt 即场景
不编写决策树或硬编码对话流程，而是为 LLM 提供工具、知识库与上下文管理机制——**Agent = Model，Harness = Code**。编写角色 Prompt 即可在 30 分钟内冷启动新行业场景，零标注数据。相比 Megaview / FindAI 需预标注对话库的"周级"冷启动，实现分钟级即用；相比得助智能需 300+ 预训练智能体，本产品一个 Python 微服务即可支撑。

### ② 独立评估子 Agent · 5 维 16 粒度
陪练结束后自动派生**独立于对话链路的评估子 Agent**，避免"既当运动员又当裁判"。从沟通、需求挖掘、产品介绍、异议处理、成交推进 5 个维度、16 个粒度打分，输出雷达图与逐条扣分话术高亮，评估偏差 ≤5 分，让培训质量可量化、可归因、可追踪。

---

## 联系方式

- **邮箱**：2024124041@chd.edu.cn
