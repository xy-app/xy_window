# 判断窗口是否可见 (IsWindowVisible)

轻量级判断指定窗口在操作系统中当前是否处于显示/可见状态。

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
* 描述: 窗口是否处于可见状态（`true` 表示处于显示/可见状态，`false` 表示隐藏或不存在）。

## 使用示例

```json
{
    "tag": "IsWindowVisible",
    "window": "Foreground"
}
```
