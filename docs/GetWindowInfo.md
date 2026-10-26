# 获取窗口综合信息 (GetWindowInfo)

一次性读取并返回目标窗口的综合属性元数据（包含句柄、标题、类名、PID、进程名、绝对坐标、分辨率宽高、显隐及最大化/最小化状态）。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（无需管理员提权）

## 运行参数

* **目标窗口 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 目标窗口对象、标题表达式或句柄。常用预设：`Foreground`。

## 输出

* 类型: `string` (JSON 格式字典数据)
* 描述: 包含窗口完整属性信息的结构化 JSON 字符串。格式示例：
  `{"hwnd":65536,"title":"Notepad","class_name":"Notepad","process_id":1234,"process_name":"notepad.exe","x":100.0,"y":100.0,"width":800.0,"height":600.0,"is_visible":true,"is_minimized":false,"is_maximized":false}`

## 使用示例

```json
{
    "tag": "GetWindowInfo",
    "window": "Foreground"
}
```
