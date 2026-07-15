# 营销导购AI陪练系统

> **企业销售团队的AI实战练兵场 — Prompt定义角色，LLM生成战场**

[![Version](https://img.shields.io/badge/PRD-V1.1.0-blue)](./营销导购陪练智能体-PRD.md)
[![Status](https://img.shields.io/badge/status-Draft-orange)](./营销导购陪练智能体-PRD.md)
[![License](https://img.shields.io/badge/license-MIT-green)](./LICENSE)

一个面向企业销售团队的AI实战陪练SaaS平台。不依赖预标注对话数据，仅凭角色Prompt即可生成逼真AI顾客，支持文字和语音两种陪练模式。培训管理者可在30分钟内完成从场景配置到全团队陪练部署。

---

## 项目简介

营销导购陪练系统（AIDI Studio Training Agent）解决企业销售培训的四大核心矛盾：

- **新人上手慢**（45天 → 20天）：AI 7×24陪练替代老员工1对1带教
- **培训师人效瓶颈**（1:10 → 1:80）：从带教执行者转型为数据管理者
- **培训质量不可控**：统一评估量表 + 独立AI评估，偏差≤5分
- **ROI无法量化**：5维雷达图 + 成长曲线，培训效果可追踪可归因

核心理念来源于 `learn-claude-code` 工程哲学：**Agent = Model，Harness = Code**。不编写决策树或硬编码对话流程，而是为LLM提供工具、知识库和上下文管理机制，让模型自主完成角色扮演、对话推进和评估分析。

---

## 架构概览

```
┌─────────────────────────────────────────────────┐
│                 前端（React）                      │
│  角色配置面板 | 陪练对话界面 | 评估报告 | 管理后台   │
└──────────────────────┬──────────────────────────┘
                       │ REST / WebSocket / WebRTC
┌──────────────────────▼──────────────────────────┐
│           Training Backend（Python 微服务）        │
│                                                   │
│  Lead Agent Loop                                  │
│  ├── microcompact（清理旧 tool_result）            │
│  ├── auto_compact（token 超阈值时摘要压缩）         │
│  ├── inbox check（读取 Customer Agent 回复）       │
│  └── LLM API call → Tool Handlers                 │
│       ├── TodoWrite（单次陪练步骤追踪）             │
│       ├── spawn_teammate（派生 Customer Agent）    │
│       ├── evaluate（触发评估子Agent）               │
│       ├── load_skill（加载话术/量表）               │
│       └── task_update（跨会话任务图）               │
│                                                   │
│  MessageBus (JSONL)  │ TaskSystem (DAG)            │
│  Transcript Store    │ Voice Engine (ASR+TTS)      │
└──────────────────────┬──────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────┐
│              Infrastructure                      │
│  PostgreSQL (多租户) | Redis | LLM API | WebRTC   │
└─────────────────────────────────────────────────┘
```

### 核心数据流

```
学员发送销售话术（文字 / ASR转录）
  → Lead Agent 主循环：microcompact → token检查 → 
    读取MessageBus → LLM推理 → 执行Tool调用
  → Customer Agent 独立线程：读取MessageBus → 
    基于角色Prompt推理 → 生成回复
  → 前端展示（文字 / TTS语音）
```

---

## 核心能力

| 能力 | 说明 |
|------|------|
| **多Agent角色扮演** | Lead Agent + N个Customer Agent，JSONL邮箱异步通信，模拟"真人商量" |
| **Prompt即场景** | 30分钟创建新行业场景，零标注数据冷启动，覆盖6大业务场景 |
| **四级难度体系** | L1友好型 → L2犹豫型 → L3刁钻型 → L4多人决策（3+角色） |
| **语音陪练** | WebRTC实时通话，端到端≤800ms，支持PTT/VAD/打断三种交互模式 |
| **独立AI评估** | 派生评估子Agent，5维16粒度评分（沟通/需求挖掘/产品介绍/异议处理/成交推进） |
| **三层上下文压缩** | microcompact + auto_compact + manual，30-80轮对话后仍保持角色一致性 |
| **双层进度追踪** | TodoWrite（单次陪练步骤）+ TaskSystem（跨会话DAG培训计划） |
| **B端管理后台** | 团队数据看板/能力雷达图/培训任务下发/RBAC四级权限/审计日志 |

---

## PRD文档

完整的产品需求文档请参阅：

- [营销导购陪练智能体-PRD.md](./营销导购陪练智能体-PRD.md) —完整 PRD

PRD 包含：产品定位、用户画像、功能设计、系统架构、数据架构、非功能需求、竞品分析、路线图、成功指标、风险评估、定价策略。

---

## 路线图（规划）

| 阶段 | 时间 | 核心交付 | 目标 |
|------|------|---------|------|
| **MVP** | 2026 | 文字陪练 + 5维评估 + 6场景 + SSO | 5家种子客户 |
| **Phase 1** | 2026 | L4多人决策 + 雷达图 + 团队看板 + 任务下发 | ≥20家付费客户 |
| **Phase 1.5** | 2027 | 语音陪练 + 电销场景 + TTS多声线 | ≥30家，语音使用率≥20% |
| **Phase 2** | 2027 | CRM集成 + API开放 + 私有化部署 | ≥50家，ARR≥¥500万 |
| **Phase 3** | 2027 | 视频陪练 + AI实时指导 + 跨企业对战 | S级客户≥5家 |

---

## 技术栈

| 层级 | 技术选型 |
|------|---------|
| **前端** | React（角色配置面板 / 对话界面 / 评估报告 / 管理后台） |
| **后端** | Python 微服务（Lead Agent Loop / Tool Handlers / MessageBus） |
| **LLM** | Claude / GPT-4o（路由降级：主备模型切换） |
| **语音** | ASR（阿里云/讯飞/Whisper 多路热备）+ TTS（多声线）+ WebRTC（SFU） |
| **数据** | PostgreSQL（多租户）+ Redis（消息队列/缓存） |
| **部署** | Docker Compose / K8s（支持私有化部署） |
| **集成** | SSO（SAML 2.0 / OIDC）、企业微信/飞书/钉钉 |

