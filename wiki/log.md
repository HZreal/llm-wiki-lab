---
type: log
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [maintenance]
---
# 演化日志

按实际操作追加；规范见[[AGENTS|Agent 规则]]，导航见[[wiki/index|索引]]。

## [2026-09-27] maintenance | 模拟阶段历史追记

- 根据已有文件与本会话记录，追记 2026-07-02 模拟来源入库、三个概念页建立及 LLM Wiki vs RAG 回答落地。
- 页面：[[wiki/sources/2026-07-02-karpathy-llm-wiki|模拟来源]]、[[wiki/concepts/evolving-knowledge-system|持续进化]]、[[wiki/concepts/raw-wiki-dual-layer|资料分层]]、[[wiki/concepts/ingest-workflow|入库流程]]、[[wiki/concepts/llm-wiki-vs-rag|对比页]]。
- 当时未建立追加日志；本条不代表当时执行过现有规则下的完整检查。

## [2026-09-27] ingest | Karpathy LLM Wiki idea

- 完整读取 Gist 英文正文，新增版本固定的 raw 快照与[[wiki/sources/karpathy-llm-wiki-idea|来源页]]。
- 更新四个已有概念/对比页，补真实来源、schema、索引和日志闭环；修正 RAG 泛化，标明模拟来源。
- 建立[[wiki/overview|首页]]、[[wiki/index|索引]]和[[wiki/syntheses/second-brain-system|系统现状]]，扩展 AGENTS.md 并新增四个模板。
- 原文快照与下载文件逐字节一致，已有两份 raw 的 SHA-256 未改变。
- 未入库 Uber Go 资料，本次只核对元数据和开头；个人知识尚未提供。

## [2026-09-27] lint | 初始系统迁移检查

- 范围：所有正式 wiki 页、内部链接、索引覆盖、必要元数据、原始资料完整性。
- 修复短路径链接、索引缺失、元数据缺失及模拟来源未标识问题。
- 结果和未解决项见[[wiki/reports/2026-09-27-bootstrap-lint|首轮健康检查]]。
- 验证通过：11 个正式页面、99 个内部链接、索引覆盖、入链与必需元数据；原文字节比对、既有 raw 校验值和差异格式检查通过。

## [2026-09-27] maintenance | 根目录队列与成功归档流程

- 用户采用目录状态方案，新增 `raw/assets/` 和 `raw/ingested/`（各含 `.gitkeep`）。
- 更新 AGENTS.md 的扫描范围、归档验收、重试、同名防覆盖、版本、附件及异常恢复规则；同步首页、流程、系统现状与来源模板。
- 已完成的两份 LLM Wiki 原文从 `raw/` 根目录移动到 `raw/ingested/`，来源页链接同步更新；来源页记录原输入路径与归档信息。
- 模拟来源归档只表示模拟摄入完成，其证据状态仍为 needs-review。Uber Go 文件保持根目录待摄入。
- 本次是流程迁移，没有重新摄入归档，也没有处理 Uber Go 正文；历史日志正文保持不变。
- 验证通过：两个归档文件的 SHA-256 与迁移前一致，所有 wiki 内部链接可解析，根目录仅剩一个待摄入源文件，差异格式检查通过。

## [2026-09-27] ingest | Uber Go 语言编码规范中文版

- 输入路径：`raw/xxjwxcuber_go_guide_cn Uber Go 语言编码规范中文版. The Uber Go Style Guide ..md`；完成后同名移入 `raw/ingested/`。
- 完整读取 1395 行，新增[[wiki/sources/uber-go-style-guide-cn|来源总结]]、[[wiki/topics/go-coding-guidelines|Go 规范主题]]与错误契约、goroutine 生命周期、数据所有权、API 设计四个概念页。
- 更新首页、索引、系统现状、历史报告原文引用及本日志；无既有 Go 概念需覆盖。
- 官方复核 os.Exit/defer、Go 1.22 循环变量语义和 golint 弃用，来源页附证据链接。部分技术表述仍待核验，来源维持 needs-review；未执行代码测试。
- 归档前检查通过，校验值为 `c5c353c913a1334603bed2e06dcd9c22e2aa6321775e9af10cd4e40c8ed65692`。

## [2026-09-27] lint | Uber Go 摄入后检查

- 范围与内容问题见[[wiki/reports/2026-09-27-uber-go-ingest-lint|检查报告]]，历史首轮“未入库”项已有后续记录。
- 最终验证通过：18 个正式页面、147 个内部链接，索引覆盖、入链和必需元数据有效；归档前后 SHA-256 一致，根目录待摄入文件为 0，差异格式检查通过。
