---
type: concept
created: 2026-09-27
updated: 2026-09-27
status: active
tags: [go, errors]
---
# Go 错误契约

## 定义

错误契约说明调用者收到什么错误、能否匹配其原因，以及在哪一层决定恢复、记录或终止。

## 选择与处理

来源“错误类型”“错误包装”“一次处理错误”（436–556 行）建议：

| 需求 | 选择 |
|---|---|
| 静态消息、无匹配需求 | errors.New |
| 动态上下文、无匹配需求 | fmt.Errorf |
| 需要识别固定错误 | 稳定错误值配合 errors.Is |
| 需要提取结构化信息 | 自定义错误类型配合 errors.As |
| 包装并暴露底层原因 | fmt.Errorf 的 %w，成为需要维护的契约 |
| 添加文本而不提供包装链 | %v |

没有新增上下文时可原样返回。上下文描述操作和对象，避免层层重复“failed to”。返回错误交由上层处理，或在本层恢复并记录，通常不要各层同时记录又返回。

## 退出与边界

可预期业务失败返回 error；不要把 panic/recover 当常规错误策略。退出决策集中到 main，业务函数返回错误，便于测试和清理。来源 565–584、693–748 行。
来源页已核对 os.Exit 不运行 defer，因此应在可返回的业务函数里完成清理后再退出。

## 相关页面与来源

- [[wiki/concepts/go-api-design|API 设计]]：导出错误也是公共契约。
- [[wiki/concepts/go-goroutine-lifecycle|goroutine 生命周期]]：错误退出也要安排清理与等待。
- [[wiki/topics/go-coding-guidelines|Go 编码规范]]：检查表。
- [[wiki/sources/uber-go-style-guide-cn|来源及复核]]：本页是该指南的归纳，不是运行测试结果。
