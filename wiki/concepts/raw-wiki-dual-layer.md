---
type: concept
created: 2026-07-02
updated: 2026-09-27
status: active
tags: [llm-wiki, architecture]
---
# raw/wiki 双层结构

## 定义
raw/wiki 双层结构是指将知识库分成两个主要层级：`raw/` 存放原始资料，`wiki/` 存放经过整理、总结和链接后的知识页。

## 分层职责
- `raw/`：保留不可变的原始输入，适合追溯来源、核对细节和重新解读；更正以新版本保存。
- `wiki/`：保存可直接阅读、复用和互相链接的知识页面。

## 价值
- 降低原始资料噪音对日常查询的影响。
- 让整理后的页面具备稳定标题、明确主题和交叉链接。
- 支持 [[wiki/concepts/evolving-knowledge-system|持续进化的知识系统]]：新资料可以不断修正旧知识，而不是只堆积原文。
- 体现 [[wiki/concepts/llm-wiki-vs-rag|LLM Wiki 与传统 RAG 的差别]]：查询优先面对整理后的 `wiki/` 页面。

## 在 ingest 中的作用
当新资料进入 `raw/` 后，应通过 [[wiki/concepts/ingest-workflow|ingest 流程]] 生成来源总结页、提炼关键概念，并更新相关 wiki 页面。

## 完整架构还有 schema

“双层”只描述内容分层。真实 idea 的 Architecture 定义三层，第三层是 [[AGENTS|schema 规则文件]]，规范结构与维护流程。[[wiki/syntheses/second-brain-system|第二大脑系统]]采用完整三层架构。

## 来源
- [[wiki/sources/karpathy-llm-wiki-idea|真实 idea 来源]]：Architecture。
- [[wiki/sources/2026-07-02-karpathy-llm-wiki|5分钟复刻 Andrej Karpathy 的 LLM Wiki]]
