# 获取窗口标题 (GetWindowCaption)

读取当前目标窗口的标题栏文本内容。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限

## 运行参数

* **目标窗口 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 目标窗口对象、标题表达式或句柄。常用预设：`Foreground`。

## 输出

* 类型: `string`
* 描述: 读取到的窗口当前标题栏文本内容。

## 使用示例

```json
{
    "tag": "GetWindowCaption",
    "window": "Foreground"
}
```
