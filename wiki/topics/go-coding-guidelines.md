---
type: topic
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [go, coding-style]
---
# Go 编码规范

## 范围

目前依据[[wiki/sources/uber-go-style-guide-cn|Uber Go 中文指南剪藏]]整理，是单来源主题总结，不是所有团队的统一标准。版本限制和原文疑点见来源页。

## 核心检查表

| 关注点 | 检查问题 | 相关知识 |
|---|---|---|
| 错误 | 调用者能否匹配？上下文是否清晰？是否重复记日志？ | [[wiki/concepts/go-error-contracts|错误契约]] |
| 并发 | 能否发出停止信号并等待结束？退出路径是否释放资源？ | [[wiki/concepts/go-goroutine-lifecycle|生命周期]] |
| 状态 | slice/map 是否泄漏可变内部状态？锁是否覆盖访问？ | [[wiki/concepts/go-data-ownership|数据所有权]] |
| API | 接口和序列化契约是否明确？嵌入是否暴露多余能力？ | [[wiki/concepts/go-api-design|API 设计]] |
| 测试 | 重复逻辑是否适合表驱动？并行测试是否共享可变状态？ | 原文“表驱动测试” |
| 性能 | 是否属于高频场景？容量与转换优化是否有项目测量依据？ | 原文“性能” |
| 风格与工具 | 是否保持包级一致性？工具配置是否匹配项目版本？ | 原文“规范”“Linting” |

## 补充原则

时间点用 `time.Time`、时间段用 `time.Duration`；外部数值字段注明单位。下一个日历日与经过 24 小时是不同意图，应分别考虑 AddDate 和 Add。来源：原文 378–435 行。

容量预分配、重复转换优化和 strconv 建议来自特定性能场景；本次未复现 benchmark。风格约定由团队选择，摄入这份资料不等于自动改变仓库的编码规则或安装工具。

表驱动测试和 lint 建议须结合语言/工具版本使用。来源页记录了 Go 1.22 循环语义与 golint 弃用的复核，避免继续传播旧说明。

## 综合理解

Agent 综合：这些原则共同围绕边界清晰展开，包括数据归谁管理、错误归谁处理、goroutine 归谁关闭、哪些能力成为公共 API。此理解由上述单份来源提炼，尚无独立多来源验证。

## 相关页面与来源

- [[wiki/sources/uber-go-style-guide-cn|来源总结]]：全文范围、证据位置与限制。
- [[wiki/overview|知识库首页]]：Go 主题入口。
