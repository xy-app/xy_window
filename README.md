# 🪟 官方窗口管理与枚举控制套件 (Native Window Management Suite)

[![Plugin Version](https://img.shields.io/badge/version-0.50.5-blue.svg)](manifest.json)
[![Group](https://img.shields.io/badge/group-Window-blue.svg)](#)
[![Platform](https://img.shields.io/badge/platform-All-green.svg)](#)
[![License](https://img.shields.io/badge/license-Freeware-brightgreen.svg)](#)

专为桌面自动化、RPA 流程编排与视窗交互设计的原生窗口控制与句柄管理套件。提供跨平台与 Win32 原生窗口全量枚举、标题/类名模糊与精确匹配查找、窗口前台激活与闪烁提醒、安全关闭、显示/隐藏/最大化/最小化控制、窗口绝对平移与尺寸缩放、Z-Order 层级置顶、父子祖先关系溯源、九宫格锚点坐标推导以及系统原生弹窗与 Win+R 运行调度。

---

## 📖 简介 (Overview)

`xy_window` 提供了直接针对操作系统视窗对象与内核句柄的高性能管理能力：
- **原生视窗探测与句柄查找**：支持遍历系统所有可见或顶层窗口（`EnumWindows`），支持通过窗口标题（模糊关键字）、类名（Class Name）高精度查找并返回窗口句柄 `Wnd`（`FindWindow`）。
- **视窗焦点与用户交互**：支持将目标窗口置于前台激活（`ActiveWindow`）、任务栏高亮闪烁提醒（`FlashWindow`）、原生模态/非模态弹窗对话框（`MessageBox`），以及调起系统 Win+R 运行窗口（`WinRun`）。
- **空间几何与排版调整**：支持平移窗口绝对坐标（`WindowXy`）、获取与设置宽高分辨率尺寸（`WindowSize`），以及基于窗口左上/右上/中心等 5 种锚点推导屏幕绝对坐标（`WindowPoint`）。
- **层级管理与状态控制**：支持 Z-Order 置顶与取消置顶（`PositionWindow`，TopMost/NoTopMost/Top/Bottom）、显示/隐藏/最大化/最小化/还原状态切换（`WindowVisible`），以及安全发送 `WM_CLOSE` 信号关闭窗口（`CloseWindow`）。
- **视窗树拓扑与特殊系统句柄**：支持快速获取桌面（Desktop）、任务栏（Shell_TrayWnd）等系统关键窗口（`SpecialWindow`），以及查询子控件的直接父级（Parent）、顶层根窗口（Root）与所属主窗口（`WindowAncestor`）。

---

## ✨ 核心特性 (Features)

- **原生句柄级直连**：基于原生视窗 API（如 Win32/X11），操作延迟在微秒级，无繁琐中间层。
- **灵活的匹配规则**：标题支持模糊匹配，类名支持精确检索，窗口入参同时兼容句柄数字（HWND）与文本表达式（如 `Foreground`, `Desktop`）。
- **锚点坐标推导系统**：通过 `WindowPoint` 算子，可根据窗口的 `TopLeft`、`TopRight`、`BottomLeft`、`BottomRight` 或 `Center` 快速计算出带偏移量的点击目标点，无惧分辨率动态变化。
- **全生命周期拓扑溯源**：支持通过 `WindowAncestor` 递归回溯 `Parent`（父窗口）、`Root`（根窗口）与 `RootOwner`（顶层所有者），精准处理嵌套多级 iframe 或复杂的桌面弹窗结构。
- **原生多模式弹窗系统**：内置原生系统消息框 `MessageBox`，支持 `ok`、`ok_cancel` 与 `yes_no` 样式，兼顾自动化流程阻塞交互与通知。

---

## 🛠️ 动作指令全景速查 (Action Catalog)

| 动作标识 (Tag) | 功能名称 | 描述 | 输出类型 |
| :--- | :--- | :--- | :--- |
| `FindWindow` | 查找窗口 | 根据类名或标题关键字精确/模糊查找并返回窗口句柄 | `Wnd` |
| `EnumWindows` | 枚举所有窗口 | 遍历系统所有窗口，支持 `visible`、`top_level` 与 `all` 规则过滤 | `Array` |
| `ActiveWindow` | 激活窗口 | 将指定窗口激活并置于前台获得焦点 | `Wnd` |
| `CloseWindow` | 关闭窗口 | 向指定窗口发送 `WM_CLOSE` 关闭信号 | `bool` |
| `WindowVisible` | 窗口显隐/最大最小化 | 控制窗口显示、隐藏、最大化、最小化或正常还原 | `bool` |
| `WindowXy` | 移动窗口位置 | 将目标窗口平移到屏幕指定 (X, Y) 像素物理坐标 | `bool` |
| `WindowSize` | 调整/获取窗口尺寸 | 重设窗口宽高分辨率 (W, H)，留空时读取当前尺寸 | `string` |
| `PositionWindow` | 调整窗口层级 | 调整 Z-Order 层级（置顶 TopMost、取消置顶 NoTopMost 等） | `bool` |
| `WindowCaption` | 获取/修改窗口标题 | 读取窗口当前标题，或将窗口重命名为新标题文本 | `string` |
| `WindowPoint` | 根据锚点计算窗口坐标 | 依据窗口左上/中心等锚点基准推导绝对屏幕坐标点 | `string` |
| `WindowAncestor` | 获取父级/祖先窗口 | 查询子窗口的直接父级 (Parent)、顶层根窗口 (Root) 或拥有者 | `Wnd` |
| `SpecialWindow` | 获取特殊系统窗口 | 快速提取系统桌面 (Desktop)、任务栏托盘或活动前台句柄 | `Wnd` |
| `FlashWindow` | 闪烁窗口提示 | 使指定窗口在任务栏或标题栏高亮闪烁提醒用户 | `bool` |
| `MessageBox` | 弹出提示消息框 | 弹出系统原生消息提示框（支持 OK/Cancel/Yes/No） | `string` |
| `WinRun` | 打开运行对话框 | 调起操作系统原生 Win+R 运行程序对话框 | `bool` |

---

## 📚 详细参数说明与使用参考 (Detailed Reference)

### 1. 窗口查找、枚举与特殊句柄 (Discovery & Windows Tree)

#### `FindWindow` - 查找窗口
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 说明 |
  | :--- | :--- | :--- | :--- | :--- |
  | `title` | 窗口标题 | `string` | `""` | 窗口标题文本（支持关键字模糊检索） |
  | `class_name` | 窗口类名 | `string` | `""` | 窗口系统类名 Class Name（如 `Notepad`, `Chrome_WidgetWin_1`） |
- **输出类型：** `Wnd`（找到的窗口句柄对象）

#### `EnumWindows` - 枚举所有窗口
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设选项 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `filter` | 过滤规则 | `string` | `visible` | `all`, `visible`, `top_level` | `visible`: 仅可见窗口；`top_level`: 顶层顶级窗口；`all`: 全量窗口 |
- **输出类型：** `Array`（窗口句柄与元数据列表）

#### `SpecialWindow` - 获取特殊系统窗口
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设选项 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `window` | 特殊窗口类型 | `string` | `Desktop` | `Desktop`, `Foreground`, `Shell_TrayWnd` | 提取桌面、前台焦点或任务栏托盘窗口 |
- **输出类型：** `Wnd`

#### `WindowAncestor` - 获取父级/祖先窗口
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设选项 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `window` | 子窗口对象 | `string` | `""` | - | 目标子窗口句柄或表达式 |
  | `ancestor` | 关系类型 | `string` | `Parent` | `Parent`, `Root`, `RootOwner` | 祖先层级：`Parent` 直接父级；`Root` 根窗口；`RootOwner` 属主窗口 |
- **输出类型：** `Wnd`

---

### 2. 窗口状态、显隐与层级控制 (State, Visibility & Z-Order)

#### `ActiveWindow` - 激活窗口
- **输入参数：**
  - `window` (*string*, 默认 `""`): 目标窗口句柄或匹配表达式（预设：`Foreground`, `Desktop`）。
- **输出类型：** `Wnd`

#### `WindowVisible` - 窗口显隐/最大最小化
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设选项 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `window` | 目标窗口 | `string` | `""` | - | 目标窗口句柄或表达式 |
  | `visible` | 显隐状态操作 | `string` | `Show` | `Show`, `Hide`, `Maximize`, `Minimize`, `Restore` | 状态控制操作指令 |
- **输出类型：** `bool`

#### `PositionWindow` - 调整窗口层级 (Z-Order)
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设选项 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `window` | 目标窗口 | `string` | `""` | - | 目标窗口句柄 |
  | `order` | 层级操作 | `string` | `TopMost` | `TopMost`, `NoTopMost`, `Top`, `Bottom` | `TopMost`: 强制置顶；`NoTopMost`: 取消置顶；`Top`: 调至前排；`Bottom`: 沉底 |
- **输出类型：** `bool`

#### `CloseWindow` - 关闭窗口
- **输入参数：**
  - `window`: 目标窗口句柄或匹配表达式。向目标视窗发送标准 `WM_CLOSE` 信号。
- **输出类型：** `bool`

---

### 3. 几何排版、位置与锚点推导 (Geometry, Position & Anchor Point)

#### `WindowXy` - 移动窗口位置
- **输入参数：**
  - `window`: 目标窗口句柄。
  - `xy` (*string*, 默认 `100,100`): 目标屏幕绝对物理坐标 `X, Y`（预设：`0,0`, `100,100`）。
- **输出类型：** `bool`

#### `WindowSize` - 调整/获取窗口尺寸
- **输入参数：**
  - `window`: 目标窗口句柄。
  - `size` (*string*, 默认 `800,600`): 尺寸大小 `W, H`（预设：`800,600`, `1024,768`, `1920,1080`）。**留空则返回当前窗口实际尺寸**。
- **输出类型：** `string`（当前尺寸或设定后的尺寸，格式如 `800,600`）

#### `WindowPoint` - 根据锚点计算窗口坐标
依据窗口的几何方位基准推算屏幕像素点，方便直接调用鼠标点击。
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设选项 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `window` | 目标窗口 | `string` | `""` | - | 目标窗口句柄 |
  | `relative` | 相对锚点方位 | `string` | `TopLeft` | `TopLeft`, `TopRight`, `BottomLeft`, `BottomRight`, `Center` | 定位基准原点 |
  | `offset` | 坐标偏移 (X, Y) | `string` | `0,0` | `0,0`, `10,10` | 相对选定锚点的像素位移量 |
- **输出类型：** `string`（计算得出的绝对屏幕坐标 `X, Y`）

---

### 4. 标题管理、通知与交互 (Caption & Notification Dialogs)

#### `WindowCaption` - 获取/修改窗口标题
- **输入参数：**
  - `window`: 目标窗口句柄。
  - `caption`: 准备设置的新窗口标题。**留空则读取当前标题**。
- **输出类型：** `string`

#### `MessageBox` - 弹出提示消息框
- **输入参数：**
  | 参数名 (Field) | 显示名称 | 类型 | 默认值 | 预设选项 | 说明 |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | `title` | 弹窗标题 | `string` | `提示` | `提示`, `警告`, `确认` | 消息框标题 |
  | `content` | 提示内容 | `string` | `操作完成` | - | 对话框消息文本 |
  | `buttons` | 按钮组合 | `string` | `ok` | `ok`, `ok_cancel`, `yes_no` | 对话框操作按钮式样 |
- **输出类型：** `string`（用户点击的按钮结果，如 `ok`, `cancel`, `yes`, `no`）

#### `FlashWindow` 与 `WinRun`
- **`FlashWindow`**：使目标 `window` 在任务栏高亮闪烁 `count` 次（默认 `3` 次），用于关键节点提醒操作者。
- **`WinRun`**：直接唤起 Windows 系统的标准 Win+R 运行对话框。

---

## 📦 插件清单定义 (Manifest Reference)

```json
{
  "plugin_id": "xy_window",
  "name": "官方窗口管理与枚举控制套件 (Native Window Management Suite)",
  "version": "0.50.5",
  "group": "Window",
  "group_icon": "🪟",
  "description": "提供Win32与跨平台原生窗口枚举、句柄查找、激活、关闭、显示/隐藏、坐标定位、大小调整、标题修改与系统运行弹窗控制",
  "actions": [...]
}
```

---

## 📄 许可证 (License)

本插件遵循免费专有许可协议 (Freeware)。供 小友+ 用户免费下载与使用，未经官方书面授权，严禁对二进制文件进行逆向工程、反编译或二次打包转售。
