---
type: concept
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [go, concurrency]
---
# Go goroutine 生命周期

## 定义

每个 goroutine 都应有可预测的结束时刻，或有可通知的停止方式，并且启动方能够等待它结束。轻量并不意味着可以无限制、无管理地启动。

## 管理要点

依据原文 759–817 行：

- 区分停止信号和完成信号：发出停止请求后还要等待完成。
- 多个任务可用 WaitGroup 等待；单任务可关闭完成 channel 通知结束。
- 清理 ticker、文件等资源；不要在 init 中启动调用者无法关闭的后台任务。
- 后台任务由生命周期对象管理，暴露 Close、Stop 或 Shutdown，负责通知并等待。

原文 348–355 行偏好无缓冲或容量 1 的 channel，其他容量需要解释队列边界和阻塞行为。这是团队审查策略，不是其他容量非法。

## 边界与待核实

停止通知不会自动解除所有阻塞；业务操作必须能响应停止。重复关闭停止 channel 也需要管理。本段是 Agent 从生命周期要求推导的检查项，未提供并运行完整实现。
原文 ticker/tick 标识符不一致，知识页只保留机制，不复制错误示例。并行测试循环变量的版本条件见来源页复核。

## 相关页面与来源

- [[wiki/concepts/go-data-ownership|数据所有权]]：并发任务访问共享状态时需明确保护范围。
- [[wiki/concepts/go-error-contracts|错误契约]]：失败后的资源与任务退出。
- [[wiki/topics/go-coding-guidelines|Go 编码规范]]：主题入口。
- [[wiki/sources/uber-go-style-guide-cn|来源]]：348–355、759–817、1267–1312 行。
