# 等待窗口状态 (WaitWindow)

等待目标窗口达到指定的生命周期状态（出现 `Appears`、消失 `Disappears` 或激活为前台 `Active`），支持超时重试控制与防阻断防御。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（无需管理员提权）

## 运行参数

* **父窗口 (`parent_window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 父窗口限定。留空表示在桌面顶层等待。
* **窗口标题 (`caption`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 目标窗口标题（支持 `*` 通配符）。
* **窗口类名 (`window_class`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 目标窗口类名。
* **目标状态 (`state`)**
  * 类型: `string`
  * 默认值: `"Appears"`
  * 描述: 等待的目标窗口状态：`Appears` (等待出现), `Disappears` (等待消失), `Active` (等待激活)。
* **超时时间 (毫秒) (`timeout_ms`)**
  * 类型: `number`
  * 默认值: `30000`
  * 描述: 最长等待超时时间（毫秒）。
* **超时抛错 (`throw_on_timeout`)**
  * 类型: `number`
  * 默认值: `1`
  * 描述: 超时未满足状态时是否抛出异常阻断流程 (1 抛错, 0 不抛错)。

## 输出

* 类型: `Wnd`
* 描述: 返回匹配到的目标窗口对象 (`Wnd`)，超时且未抛错时返回空句柄 (`0`)。

## 使用示例

```json
{
    "tag": "WaitWindow",
    "parent_window": "",
    "caption": "*记事本*",
    "window_class": "",
    "state": "Appears",
    "timeout_ms": 30000,
    "throw_on_timeout": 1
}
```
