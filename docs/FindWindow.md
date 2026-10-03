# 查找窗口 (FindWindow)

根据窗口标题、窗口类名通配符、父窗口、可见性筛选条件及索引查找匹配的窗口对象 (`Wnd`)。支持检索隐藏窗口，便于后续配合 `WindowVisible` 动作将窗口显示到前台。

## 平台与权限
* **支持平台**: `Windows`
* **权限要求**: 普通用户权限

## 运行参数

| 参数名 | 类型 | 默认值 | 预设选项 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| `parent_window` | `Wnd` / `MixedType` | `""` | `Desktop`, `Foreground` | 父窗口对象；留空时在整个系统桌面顶层查找 |
| `caption` | `String` / `MixedType` | `""` | 自由输入 | 目标窗口标题（支持 `*` 通配符与模糊匹配，如 `*记事本*`） |
| `window_class` | `String` / `MixedType` | `""` | 自由输入 | 目标窗口类名（如 `Notepad`, `Chrome_WidgetWin_1` 等） |
| `visible` | `String` / `MixedType` | `"All (全部窗口)"` | `All (全部窗口)`, `Visible (仅可见窗口)` | 可见性筛选条件：默认检索全部（含隐藏窗口）；选择 `Visible` 仅检索可见窗口 |
| `index` | `String` / `MixedType` | `"0"` | `0`, `-1`, `1` | 匹配多实例时的索引：`0` 表示首个匹配，`-1` 表示最后一个 |

## 输出

* **目标窗口对象 (`Wnd`)**: 成功找到的窗口对象 (若未找到返回空窗口句柄 `hwnd = 0`)
