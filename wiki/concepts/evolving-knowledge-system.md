---
type: concept
created: 2026-07-02
updated: 2026-09-27
status: active
tags: [llm-wiki]
---
# 持续进化的知识系统

## 定义
持续进化的知识系统是一种把资料不断整理、改写、链接和校正的知识库形态。它关注知识页之间的结构化关系，而不只是把原始资料存起来等待检索。

## 核心特征
- 原始资料与整理结果分离，避免把未处理信息和稳定知识混在一起。
- 每次新增资料都触发页面更新、概念沉淀和交叉链接。
- 旧页面会随着新资料进入而被修订，而不是只追加新文件。
- 查询时优先使用已经整理过的 wiki 页面，必要时再回看原始资料。

## 与其他概念的关系
- 依赖 [[wiki/concepts/raw-wiki-dual-layer|raw/wiki 双层结构]] 来区分资料状态。
- 通过 [[wiki/concepts/ingest-workflow|ingest 流程]] 把新资料变成可复用知识。
- [[wiki/concepts/llm-wiki-vs-rag|LLM Wiki vs 传统 RAG]] 比较知识沉淀与查询时检索。
- [[wiki/syntheses/second-brain-system|第二大脑系统现状]]说明本仓库的具体实现。

## 维护边界

依据 idea 的 Operations / Indexing and logging，持续进化还包括成果回流、索引更新、追加日志和健康检查。Agent 必须识别冲突和证据缺口；持续维护不意味着内容自动正确。

## 来源
- [[wiki/sources/karpathy-llm-wiki-idea|真实 idea 来源]]：The core idea、Operations。
- [[wiki/sources/2026-07-02-karpathy-llm-wiki|5分钟复刻 Andrej Karpathy 的 LLM Wiki]]
