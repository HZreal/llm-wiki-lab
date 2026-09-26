---
type: concept
created: 2026-07-02
updated: 2026-09-27
status: active
tags: [llm-wiki, workflow]
---
# ingest 流程

## 定义
ingest 流程是指新资料进入 `raw/` 后，将其转化为 wiki 知识页的一组固定步骤。

## 基本步骤
1. 默认只扫描 `raw/` 根目录源文件，排除子目录、隐藏和临时文件；固定本批清单，完整阅读并核对重复、版本与证据范围。
2. 创建或更新来源总结页，提炼观点并链接原文。
3. 更新已有概念、实体、主题或综合；需要时建新页。
4. 处理冲突与时效，补有意义的交叉链接。
5. 更新[[wiki/index|索引]]并预检查；失败或部分完成保留原位。
6. 成功后移入 `raw/ingested/`，修复原文引用，核对校验值、附件和链接，向[[wiki/log|日志]]追加完成记录；失败按规则撤回归档。

## 队列与归档

`raw/` 根目录是待摄入队列，`raw/ingested/` 是完成归档，`raw/assets/` 是附件。默认摄入不递归扫描子目录，也不靠全量日志筛选队列。检索相关 wiki 和中断重试时仍需查对应来源记录。
同名文件不覆盖，更新资料作为新版本入队；归档只移动位置，原文内容不改。归档状态和证据可靠性分开记录。该队列方案是用户选择的实现，具体约束见[[AGENTS|规则]]。

具体操作与验收由[[AGENTS|Agent 规则]]定义。部分读取或中断不算完成，后续处理登记到维护报告。

## 实施原则
- 先保证流程能稳定跑通，再扩大资料规模。
- 优先把资料变成可链接、可维护的页面，而不是只保留摘要。
- 对已有页面进行增量更新，避免同一概念在多个页面中重复散落。
- [[wiki/concepts/llm-wiki-vs-rag|RAG 对比]]说明这一流程在知识维护上的侧重点。

## 与其他概念的关系
- 基于 [[wiki/concepts/raw-wiki-dual-layer|raw/wiki 双层结构]] 运作。
- 服务于 [[wiki/concepts/evolving-knowledge-system|持续进化的知识系统]]。
- [[wiki/syntheses/second-brain-system|系统现状]]记录该流程的落地。

## 来源
- [[wiki/sources/karpathy-llm-wiki-idea|真实 idea 来源]]：Operations、Indexing and logging。
- [[wiki/sources/2026-07-02-karpathy-llm-wiki|5分钟复刻 Andrej Karpathy 的 LLM Wiki]]
