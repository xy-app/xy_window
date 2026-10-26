# 查找窗口 (FindWindow)

根据窗口标题文字或软件名称查找目标窗口对象。支持通配符模糊匹配、类名过滤、进程名过滤、父级范围、可见性筛选与多实例索引，并支持通过右键菜单直接选取 Desktop 或 Foreground 特殊窗口。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（无需管理员提权）

## 运行参数

* **父窗口 (`parent_window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 父窗口对象或句柄。留空时在整个系统桌面顶层查找。常用预设：`Desktop`, `Foreground`。
* **窗口标题 (`caption`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 目标窗口标题（支持 `*` 通配符模糊匹配，如 `*记事本*`；右键菜单可选择 `Desktop` 桌面或 `Foreground` 前台窗口）。
* **窗口类名 (`window_class`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 目标窗口类名（如 `Notepad`, `Chrome_WidgetWin_1` 等）。留空表示不限制类名。
* **进程名称 (`process_name`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 目标可执行进程名称（如 `notepad.exe`, `msedge.exe` 等）。留空表示不限制进程名。
* **匹配模式 (`match_mode`)**
  * 类型: `string`
  * 默认值: `"wildcard"`
  * 描述: 匹配模式：`wildcard` (通配符匹配), `exact` (精确完全匹配), `contains` (文本包含匹配), `regex` (正则表达式)。
* **可见性筛选 (`visible`)**
  * 类型: `string`
  * 默认值: `"all"`
  * 描述: 可见性筛选条件：`all` (检索全部窗口), `visible` (仅可见窗口), `hidden` (仅隐藏窗口)。
* **匹配索引 (`index`)**
  * 类型: `number`
  * 默认值: `0`
  * 描述: 匹配多个同名实例时的选取索引：`0` (首个匹配实例), `-1` (最后一个匹配实例), `1` (第二个实例)。
* **超时时间 (毫秒) (`timeout_ms`)**
  * 类型: `number`
  * 默认值: `5000`
  * 描述: 查找目标窗口的最长等待超时时间（毫秒，0 表示立即尝试）。

## 输出

* 类型: `Wnd`
* 描述: 成功找到的目标窗口对象 (`Wnd`)；若未找到匹配窗口则返回空窗口句柄 (`hwnd = 0`)。

## 使用示例

```json
{
    "tag": "FindWindow",
    "parent_window": "Desktop",
    "caption": "*记事本*",
    "window_class": "",
    "process_name": "",
    "match_mode": "wildcard",
    "visible": "visible",
    "index": 0,
    "timeout_ms": 5000
}
```
