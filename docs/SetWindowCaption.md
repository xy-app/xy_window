# 设置窗口标题 (SetWindowCaption)

将指定窗口的标题栏修改更新为新的文本内容。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（修改外部高权限进程窗口标题时可能受 UIPI 保护限制）

## 运行参数

* **目标窗口 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 目标窗口对象、标题表达式或句柄。常用预设：`Foreground`。
* **新标题 (`caption`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 要设置的窗口新标题文本内容。

## 输出

* 类型: `bool`
* 描述: 设置修改窗口标题执行结果（`true` 表示成功，`false` 表示失败）。

## 使用示例

```json
{
    "tag": "SetWindowCaption",
    "window": "Foreground",
    "caption": "新窗口标题"
}
```
