# 判断窗口是否存在 (IsWindowExists)

轻量级判断指定窗口当前是否存在于操作系统中，快速返回 `true` 或 `false`，不抛出异常。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限

## 运行参数

* **目标窗口 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 待检测的目标窗口对象 (`Wnd`)、窗口标题、类名或句柄表达式。常用预设：`Foreground`。

## 输出

* 类型: `bool`
* 描述: 窗口是否存在判断结果（`true` 表示窗口存在，`false` 表示未找到或不存在）。

## 使用示例

```json
{
    "tag": "IsWindowExists",
    "window": "Foreground"
}
```
