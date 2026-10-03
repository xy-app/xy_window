# 消息框 (MessageBox)

弹出一个系统原生模态对话框，阻塞流程继续执行，直到用户交互点击按钮关闭对话框，并返回用户点击按钮的结果代码。

## 平台与权限
* **支持平台**: `Cross-Platform`（Windows / Linux / macOS 全平台原生支持）
  * **Windows**: 操作系统原生置顶模态对话框
  * **Linux (Desktop)**: 桌面原生弹窗交互组件
  * **macOS**: 操作系统原生对话框
  * **Headless / 无图形环境**: 自动在控制台打印提示并返回默认确认码，保证后台无人值守流程正常推进
* **权限要求**: 普通用户权限

## 运行参数

| 参数名 | 类型 | 默认值 | 预设选项 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| `caption` | `String` | `""` | 自由输入 / 变量 | 对话框标题栏文本 |
| `text` | `String` | `""` | 自由输入 / 变量 | 对话框消息正文内容，支持多行文本 |
| `button_type` | `String` | `"OK"` | `OK`, `OKCANCEL`, `ABORTRETRYIGNORE`, `YESNOCANCEL`, `YESNO`, `RETRYCANCEL` | 按钮组合样式 |

## 输出

* **结果代码 (`Number`)**: 用户点击的按钮代码：
  * `1`: `IDOK` (确定)
  * `2`: `IDCANCEL` (取消)
  * `3`: `IDABORT` (中止)
  * `4`: `IDRETRY` (重试)
  * `5`: `IDIGNORE` (忽略)
  * `6`: `IDYES` (是)
  * `7`: `IDNO` (否)