---
type: source
created: 2026-09-27
updated: 2026-09-27
status: needs-review
tags: [go, source, coding-style]
---
# Uber Go 语言编码规范中文版

## 来源信息

- 原文：[[raw/ingested/xxjwxcuber_go_guide_cn Uber Go 语言编码规范中文版. The Uber Go Style Guide .|原始剪藏归档]]。
- 输入路径：`raw/xxjwxcuber_go_guide_cn Uber Go 语言编码规范中文版. The Uber Go Style Guide ..md`。
- 最终归档路径：`raw/ingested/xxjwxcuber_go_guide_cn Uber Go 语言编码规范中文版. The Uber Go Style Guide ..md`；摄入完成日期：2026-09-27。
- SHA-256：`c5c353c913a1334603bed2e06dcd9c22e2aa6321775e9af10cd4e40c8ed65692`。
- 剪藏日期：2026-09-27；发布时间未知，frontmatter 的作者为空。
- 中文来源：[xxjwxc/uber_go_guide_cn](https://github.com/xxjwxc/uber_go_guide_cn)。
- 原始指南：[uber-go/guide](https://github.com/uber-go/guide)；正文记载最初作者 Prashant Varanasi 和 Simon Newton，不能据此推断中文译者。
- 正文自报版本为 2024-08-10，对应提交 `97314412dfcb60c3f4f0372bc311f9ddcdac54a9`；未核对译文与该提交逐条一致性，也不称为最新版本。
- 本次完整分段读取本地文件。Markdown 表格中的代码被压成单行，不能直接当成可运行示例；未运行原文代码。

## 总结

指南围绕可维护性，说明 Go 中的接口、状态边界、错误契约、并发退出、API 演化、性能和团队一致性。通用机制与 Uber 团队偏好需要分别理解。

## 关键观点与原文位置

| 主题 | 关键内容 | 原文行号 |
|---|---|---|
| 接口与 API | 通常传接口值，编译期验证实现，明确方法集；避免嵌入泄漏公共 API | 128–302、604–646、1040–1073 |
| 数据所有权 | 在输入输出边界复制 slice/map；锁用命名字段；注意 nil slice 和序列化差异 | 303–337、1088–1106 |
| 资源与时间 | defer 清理资源；时间点用 Time、时间段用 Duration；跨系统字段明确单位 | 338–347、378–435 |
| 错误契约 | 区分匹配和上下文，选择 Is/As、%w/%v；错误通常只处理一次 | 436–584 |
| 生命周期 | 依赖注入代替可变全局，不依赖 init 副作用；退出集中在 main；goroutine 可停止且可等待 | 595–603、660–681、693–748、759–817 |
| 性能 | 高频场景下评估转换和容量；不要把旧 benchmark 数值视为项目保证 | 682–692、818–875 |
| 风格 | import、包名、声明和函数组织保持一致；减少嵌套，明确字段与参数含义 | 876–1264 |
| 模式与检查 | 表驱动测试、功能选项和一致的 lint 工具链 | 1265–1395 |

## 复核、冲突与限制

以下是 Agent 复核注释，不改写原始剪藏；外部验证日期为 2026-09-27。

- 原文“一次性退出”示例（约 717 行）注释称 log.Fatal 后 f.Close 会执行，与原文自己的“跳过清理”解释冲突。[os.Exit 官方文档](https://pkg.go.dev/os#Exit)明确退出不执行 defer；知识页采用此语义。
- “不要一劳永逸地使用 goroutine”示例声明 `ticker`，却引用 `tick.C`，存在标识符不一致；不能直接复制运行。
- 表驱动并行测试要求 `tt := tt` 的解释需要语言版本条件。[Go 官方说明](https://go.dev/blog/loopvar-preview)说明新循环变量语义适用于声明 Go 1.22 或更高版本的模块；不能把旧建议当成所有版本的必需步骤。
- 原文推荐 golint，但[官方仓库](https://github.com/golang/lint)已标记弃用和冻结；此工具建议不照搬。
- “接口本身就是一个指针”等译文补充不作为严谨定义，接口具体语义后续需专项核验。atomic 工具选择、go vet 的覆盖范围及 benchmark 没有在本次全面核验。
- Channel 默认容量、未导出全局加下划线、99 字符等属于指南约定，并非 Go 语言强制规则。指南中的复制是浅复制，不自动保证嵌套对象独立。

维护状态 needs-review 表示仍有技术表述待核实；不妨碍资料流程完成后归档。

## 相关页面

- [[wiki/topics/go-coding-guidelines|Go 编码规范]]：主题导航和应用检查表。
- [[wiki/concepts/go-error-contracts|Go 错误契约]]：匹配、包装和处理责任。
- [[wiki/concepts/go-goroutine-lifecycle|Go goroutine 生命周期]]：停止与等待。
- [[wiki/concepts/go-data-ownership|Go 数据所有权]]：共享状态与边界复制。
- [[wiki/concepts/go-api-design|Go API 设计]]：接口、组合和可选参数。
