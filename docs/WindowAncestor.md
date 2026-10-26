# 获取父级/祖先窗口 (WindowAncestor)

检索指定子窗口在 UI 树关系中的上级祖先窗口对象（包括直接父窗口、顶级父窗口以及顶级所有者窗口）。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（无需管理员提权）

## 运行参数

* **子窗口对象 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 目标子窗口对象、标题或窗口句柄。常用预设：`Foreground`, `Desktop`。
* **关系类型 (`ancestor`)**
  * 类型: `string`
  * 默认值: `"Parent"`
  * 描述: 检索关系层级类型。常用预设：`Parent` (直接父级窗口), `Root` (顶级根窗口), `RootOwner` (顶级拥有者窗口)。

## 输出

* 类型: `Wnd`
* 描述: 检索获取到的父级/祖先窗口对象 (`Wnd`)，若无对应上级窗口返回空句柄 (`0`)。

## 使用示例

```json
{
    "tag": "WindowAncestor",
    "window": "Foreground",
    "ancestor": "Parent"
}
```
