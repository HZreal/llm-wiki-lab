---
type: comparison
created: 2026-07-02
updated: 2026-09-27
status: active
tags: [llm-wiki, rag]
---
# LLM Wiki vs 传统 RAG

## 核心差别
LLM Wiki 侧重维护持久知识成果，RAG 侧重通过检索为生成提供依据。两者可以组合：RAG 可以检索 wiki，wiki 也可以配备检索工具。

本页比较 idea 描述的典型“原始文档检索问答”与持续维护 wiki 的模式，不是所有 RAG 产品的能力调查。表中的实践判断是 Agent 综合。

传统 RAG 更像是把原始资料放进检索系统里，在提问时临时找相关片段。它主要解决“怎么从资料里找答案”。

LLM Wiki 更像是把资料持续加工成一个可维护的知识系统。它主要解决“怎么把资料变成可复用、可链接、可持续修订的知识库”。

## 对比
| 维度 | 传统 RAG | LLM Wiki |
|---|---|---|
| 知识形态 | 原始文档或文档切片 | 整理后的 wiki 页面 |
| 工作重点 | 检索相关片段 | 持续整理、改写、链接、校正 |
| 新资料进入后 | 建立/更新检索索引，可用关键词或向量 | 通过 [[wiki/concepts/ingest-workflow|ingest 流程]] 整合来源、知识页、链接、索引和日志 |
| 查询方式 | 直接从原始资料或 chunk 中找答案 | 优先查 `wiki/`，必要时再回看 `raw/` |
| 长期维护 | 取决于额外设计，检索本身不要求维护综合页 | 持续修订是明确工作流，仍需检查 |
| 知识结构 | 可使用关键词、向量、图等检索方式 | 稳定页面、概念关系和交叉链接，可叠加检索 |

## 为什么 LLM Wiki 不只是 RAG
传统 RAG 的核心动作是“检索”。它可以快速把相关片段交给模型，但这些片段本身不一定被整理成稳定知识，也不一定会反过来更新已有认知结构。

LLM Wiki 的核心动作是“沉淀”。新资料进入 `raw/` 后，会经过 [[wiki/concepts/raw-wiki-dual-layer|raw/wiki 双层结构]] 和 [[wiki/concepts/ingest-workflow|ingest 流程]]，转化为来源页、概念页与链接，形成 [[wiki/concepts/evolving-knowledge-system|持续进化的知识系统]]。

## 实践含义
- 如果目标是快速问答，传统 RAG 通常更直接。
- 如果目标是长期积累知识、降低重复阅读成本、让旧知识随新资料更新，LLM Wiki 更合适。
- LLM Wiki 可以使用检索能力，但检索不是最终形态；最终目标是把检索到的资料沉淀进 wiki 结构。

## 相关页面
- [[wiki/concepts/evolving-knowledge-system|持续进化的知识系统]]
- [[wiki/concepts/raw-wiki-dual-layer|raw/wiki 双层结构]]
- [[wiki/concepts/ingest-workflow|ingest 流程]]
- [[wiki/sources/2026-07-02-karpathy-llm-wiki|5分钟复刻 Andrej Karpathy 的 LLM Wiki]]

## 来源与修订

- [[wiki/sources/karpathy-llm-wiki-idea|真实 idea 来源]]：The core idea、Optional: CLI tools。
- 2026-09-27：补真实来源，限定典型 RAG 范围，纠正“必须向量化”和“无法长期积累”的泛化。早期对比来自模拟资料，本次已明确证据边界。
