# 5分钟复刻 Andrej Karpathy 的 LLM Wiki

## 来源信息
- 原始文件：[[raw/2026-07-02-karpathy-llm-wiki|raw/2026-07-02-karpathy-llm-wiki]]
- URL：https://example.com
- 作者：xxx
- 日期：2026-04-27
- 入库日期：2026-07-02

## 一句话总结
这篇资料强调将知识库设计成一个可持续演进的 wiki，而不是一次性构建的检索系统；先建立清晰的资料分层和 ingest 规则，再逐步扩展规模。

## 关键观点
- 知识库的目标不是只做检索，而是维护一个会被持续整理、链接和修正的知识系统。
- 目录结构可以采用 [[wiki/concepts/raw-wiki-dual-layer|raw/wiki 双层结构]]：`raw/` 保存原始资料，`wiki/` 保存整理后的知识页。
- `AGENTS.md` 应作为仓库级规则文件，约束资料进入、页面更新、交叉链接和查询时的优先级。
- 新资料进入 `raw/` 后，需要通过 [[wiki/concepts/ingest-workflow|ingest 流程]] 转换成来源页、关键观点、概念页和交叉链接。
- 初期优先把 ingest 跑通，再考虑大规模资料导入、自动化处理或复杂检索能力。

## 提炼出的关键概念
- [[wiki/concepts/evolving-knowledge-system|持续进化的知识系统]]
- [[wiki/concepts/raw-wiki-dual-layer|raw/wiki 双层结构]]
- [[wiki/concepts/ingest-workflow|ingest 流程]]
- [[wiki/concepts/llm-wiki-vs-rag|LLM Wiki vs 传统 RAG]]

## 与本仓库规则的关系
这篇资料与当前仓库的 `AGENTS.md` 规则一致：回答问题时优先参考 `wiki/`，必要时再回看 `raw/`；新增资料时需要从原始资料沉淀为可链接、可更新的 wiki 页面。
