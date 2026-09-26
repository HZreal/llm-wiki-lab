---
type: overview
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [navigation]
---
# 第二大脑

这里保存从资料和问题中积累的知识、联系和修订。当前已整理 LLM Wiki 和 Go 编码规范；个人目标、生活记录尚未提供，不预填个人信息。

## 入口

- [[wiki/index|知识索引]]：所有正式页面与说明。
- [[wiki/syntheses/second-brain-system|第二大脑系统现状]]：设计对应、运行边界与下一步。
- [[wiki/log|演化日志]]：实际执行的入库、查询沉淀和维护。
- [[wiki/reports/2026-09-27-bootstrap-lint|首轮健康检查]]：待处理来源与证据缺口。
- [[AGENTS|Agent 工作规则]]：规范入口。

## 已有知识

[[wiki/concepts/evolving-knowledge-system|持续进化的知识系统]]通过[[wiki/concepts/ingest-workflow|入库流程]]积累知识；[[wiki/concepts/llm-wiki-vs-rag|与 RAG 的对比]]说明这一模式的侧重点。
原始设计见[[wiki/sources/karpathy-llm-wiki-idea|Karpathy idea 来源页]]。

[[wiki/topics/go-coding-guidelines|Go 编码规范]]关联错误契约、goroutine 生命周期、数据所有权和 API 设计，原始依据与版本限制见[[wiki/sources/uber-go-style-guide-cn|Uber Go 来源页]]。

## 日常使用

将选择的源文件放入 `raw/` 根目录，附件放入 `raw/assets/`；请求“摄入新增资料”时只处理根目录队列，成功后原文归档到 `raw/ingested/`，失败留原位。提问先查已整理知识，有价值的回答保存到 wiki，资料积累或结构调整后进行健康检查。这些操作在当前会话执行，没有后台自动监视。
