# 枚举窗口 (EnumWindows)

枚举操作系统中的所有顶层窗口或指定父窗口的子窗口列表，支持可见性筛选（检索全部窗口或仅可见窗口），并支持按 Z-Order、XY 或 YX 坐标规则排序过滤。

## 平台与权限
* **支持平台**: `Windows`
* **权限要求**: 普通用户权限

## 运行参数

| 参数名 | 类型 | 默认值 | 预设选项 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| `parent_window` | `Wnd` / `MixedType` | `""` | `Desktop`, `Foreground` | 父窗口对象；留空时枚举所有顶层窗口 |
| `filter_by_title` | `String` / `MixedType` | `""` | 自由输入 | 根据窗口标题过滤（支持通配符），留空不进行标题过滤 |
| `filter_by_name` | `String` / `MixedType` | `""` | 自由输入 | 根据窗口类名过滤（支持通配符），留空不进行类名过滤 |
| `visible` | `String` / `MixedType` | `"All (全部窗口)"` | `All (全部窗口)`, `Visible (仅可见窗口)` | 可见性筛选条件：默认检索全部（含隐藏窗口）；选择 `Visible` 仅检索可见窗口 |
| `sort_direction` | `String` / `MixedType` | `"Z"` | `Z`, `XY`, `YX` | 排序规则：`Z` (Z-Order顺序), `XY` (先横后纵), `YX` (先纵后横) |

## 输出

* **窗口列表 (`Wnds` / `Tuple` of `Wnd`)**: 匹配筛选并排序后的窗口对象集合
