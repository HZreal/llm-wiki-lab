---
type: synthesis
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [llm-wiki, second-brain]
---
# 第二大脑系统现状

## 实现与原文的对应

本页是 Agent 根据[[wiki/sources/karpathy-llm-wiki-idea|idea 来源]]编写的实现说明；规范以[[AGENTS|AGENTS.md]]为准。

| idea 要素 | 本仓库落实 |
|---|---|
| Raw sources | `raw/` 根目录为待摄入队列；成功后归档到 `raw/ingested/`，附件放 `raw/assets/`，原文内容不改写 |
| Wiki | 来源、概念、已有对比及本综合页；其他类型按需扩展 |
| Schema | AGENTS.md 规定证据、格式、流程和验收 |
| Ingest | 原文完整读取、来源总结、旧页修订、链接、索引与日志 |
| Query | 从索引找知识，带引用回答；有价值的成果按规则回流 |
| Lint | 检查结构与内容缺口，留下可追踪报告 |
| Index / Log | [[wiki/index|内容索引]]与[[wiki/log|追加日志]]职责分开 |
| 可选工具 | 使用已有 Git 和 Markdown；尚未安装搜索、展示或 Obsidian 插件 |

## 当前积累

[[wiki/concepts/evolving-knowledge-system|知识系统]]、[[wiki/concepts/raw-wiki-dual-layer|资料分层]]、[[wiki/concepts/ingest-workflow|入库流程]]和[[wiki/concepts/llm-wiki-vs-rag|RAG 对比]]已有真实 idea 作为依据；模拟笔记仍保留并明确其性质。

模板位于 `templates/`，供来源、概念、实体和综合成果复用。目录和元数据是本仓库选择，原文没有指定这些细节。

## 边界与下一步

系统规则和真实来源闭环已建立，内容仍处于起步阶段，并不等于用户全部生活和知识已导入。Uber Go 已整理为[[wiki/topics/go-coding-guidelines|Go 编码规范主题]]，版本限制和待复核项见[[wiki/sources/uber-go-style-guide-cn|来源页]]；首轮报告中的未入库记录仅代表当时状态。
下一步可以逐份导入编程、学习、阅读或个人决策资料；个人页只记录用户明确提供的信息。没有后台任务、跨设备同步或自动抓取机制。

## 相关页面

- [[wiki/overview|首页]]：日常使用入口。
- [[wiki/reports/2026-09-27-bootstrap-lint|健康检查]]：已解决和未解决项。
