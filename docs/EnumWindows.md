# 枚举所有窗口 (EnumWindows)

获取电脑当前打开的所有窗口列表与标题信息，支持父窗口限定、标题/类名过滤、可见性筛选及多种空间与层叠排序方式。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（无需管理员提权）

## 运行参数

* **父窗口 (`parent_window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 父窗口对象或句柄。留空时枚举所有顶层窗口。常用预设：`Desktop`, `Foreground`。
* **标题过滤规则 (`filter_by_title`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 根据窗口标题过滤（支持通配符 `*`），留空时不进行标题过滤。
* **进程/类名过滤 (`filter_by_name`)**
  * 类型: `string`
  * 默认值: `""`
  * 描述: 根据窗口类名或进程名过滤（支持通配符 `*`），留空时不进行类名过滤。
* **可见性筛选 (`visible`)**
  * 类型: `string`
  * 默认值: `"all"`
  * 描述: 窗口可见性筛选条件：`all` (全部窗口), `visible` (仅可见窗口), `hidden` (仅隐藏窗口)。
* **排序规则 (`sort_direction`)**
  * 类型: `string`
  * 默认值: `"Z"`
  * 描述: 窗口排序规则。常用预设：`Z` (Z-Order 深度顺序), `XY` (先横向后纵向), `YX` (先纵向后横向)。

## 输出

* 类型: `Array` (`Tuple` of `Wnd`)
* 描述: 满足过滤与排序条件的窗口对象数组列表，可用于循环遍历各窗口句柄。

## 使用示例

```json
{
    "tag": "EnumWindows",
    "parent_window": "Desktop",
    "filter_by_title": "*记事本*",
    "filter_by_name": "",
    "visible": "visible",
    "sort_direction": "Z"
}
```
