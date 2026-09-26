---
type: source
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [llm-wiki, source]
---
# Karpathy 的 LLM Wiki idea

## 来源信息

- 原文：[[raw/ingested/2026-09-27-karpathy-llm-wiki-idea|英文 idea 原文快照]]。
- 输入路径：`raw/2026-09-27-karpathy-llm-wiki-idea.md`；归档日期：2026-09-27。
- 作者：Andrej Karpathy；Gist 创建时间：2026-04-04（GitHub 页面显示）。
- 地址：[llm-wiki.md](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)。
- 获取与入库：2026-09-27；版本：`ac46de1ad27f92b28ac95459c782c07f6b8c964a`。
- SHA-256：`dc3efe98ae62f23dd08acad13aba2e95287beb20b6bec2f4af0423557fe37401`。
- 完整读取英文正文；不包含评论区，也不把第三方评论当作者要求。

## 关键观点与位置

| 原文章节 | 来源观点 |
|---|---|
| The core idea | 持久 wiki 让综合成果继续积累；用户选材和引导，Agent 维护 |
| Architecture | 不可变来源、可修订 wiki、schema 三层 |
| Operations | ingest 整合资料，query 回答并可沉淀成果，lint 维护健康 |
| Indexing and logging | index 按内容导航，log 按时间只追加 |
| Optional: CLI tools / Tips and tricks | 搜索、图表、附件、插件按需求采用 |
| Note | 这是抽象模式，目录、模板和工具由使用者具体化 |

## 与已有知识的关系

[[wiki/concepts/raw-wiki-dual-layer|内容双层]]补充 schema 后构成三层；[[wiki/concepts/ingest-workflow|入库流程]]补齐索引和日志；[[wiki/concepts/evolving-knowledge-system|持续进化]]需要检查和修订。
[[wiki/concepts/llm-wiki-vs-rag|RAG 对比]]保留模式区别，同时限制过度概括。
具体落实见[[wiki/syntheses/second-brain-system|系统现状]]与[[AGENTS|规则]]。

## 限制

idea 是设计建议，没有提供事实准确性、维护成本或规模表现的验证数据。本仓库的字段、模板和验收细则为 Agent 实现选择。早期[[wiki/sources/2026-07-02-karpathy-llm-wiki|模拟资料]]不是此 Gist 的真实摘录证明。
