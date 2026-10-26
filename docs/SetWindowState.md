# 设置窗口形态与显隐 (SetWindowState)

统一控制指定窗口的显示/隐藏状态及最化/最小化形态（包含 `Show`, `Hide`, `Maximize`, `Minimize`, `Restore`）。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（无需管理员提权）

## 运行参数

* **目标窗口 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 目标窗口对象、标题表达式或句柄。常用预设：`Foreground`。
* **显隐状态操作 (`state`)**
  * 类型: `string`
  * 默认值: `"Show"`
  * 描述: 显隐控制选项：`Show` (显示窗口), `Hide` (隐藏窗口), `Maximize` (最大化), `Minimize` (最小化), `Restore` (还原)。

## 输出

* 类型: `bool` (`Number`)
* 描述: 返回操作成功与否的逻辑结果 (`1` 成功，`0` 失败)。

## 使用示例

```json
{
    "tag": "SetWindowState",
    "window": "Foreground",
    "state": "Show"
}
```
