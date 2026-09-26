---
type: concept
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [go, state, concurrency]
---
# Go 数据所有权

## 定义

明确哪些代码可以修改数据、哪些只是读取，以及跨 API 边界时是否仍共享底层对象。本页用所有权描述设计责任，不表示 Go 有编译器强制的所有权类型系统。

## 输入、输出与锁

来源 303–337 行说明：slice/map 的传递可能保留对底层数据的共享。存储调用者传入的数据时，必要时复制；返回内部状态快照时，必要时在锁保护下复制再返回，避免调用者绕过锁修改内部状态。

零值 Mutex/RWMutex 可用，作为命名字段隐藏在实现内；不要为了方便把锁嵌入并暴露成 API。来源 303–317 行。

## 复制的边界

原文示例复制元素或键值，是浅复制。如果元素包含指针、嵌套 slice/map，内部对象仍可能共享；需要根据业务决定更深复制、只读约定或共享同步策略。不能把“已复制顶层容器”当成全部状态独立。

nil slice 可用于 len、range、append；判断是否为空通常看长度。但 nil 与非 nil 空 slice 在序列化时可能不同，遵循外部契约而不盲目统一。来源 1088–1106 行。

## 相关页面与来源

- [[wiki/concepts/go-api-design|API 设计]]：输入输出是否暴露状态。
- [[wiki/concepts/go-goroutine-lifecycle|goroutine 生命周期]]：共享访问与任务管理。
- [[wiki/topics/go-coding-guidelines|Go 编码规范]]：检查表。
- [[wiki/sources/uber-go-style-guide-cn|来源]]：303–337、1088–1106 行；复制局限由 Agent 结合原文示例归纳，未执行竞态测试。
