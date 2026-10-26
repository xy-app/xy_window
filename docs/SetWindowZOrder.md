# 设置窗口层级 (SetWindowZOrder)

独立控制指定窗口的 Z-Order 深度顺序（如常驻最顶层 `TopMost`、取消置顶 `NoTopMost`、移到最顶层 `Top` 或移到最底层 `Bottom`）。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限（无需管理员提权）

## 运行参数

* **目标窗口 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 目标窗口句柄或特征表达式。
* **层级操作 (`order`)**
  * 类型: `string`
  * 默认值: `"TopMost"`
  * 描述: Z-Order 操作选项：`TopMost` (常驻最顶层), `NoTopMost` (取消置顶), `Top` (移到当前顶层), `Bottom` (移到当前底层)。

## 输出

* 类型: `bool` (`Number`)
* 描述: 返回操作成功与否的逻辑结果 (`1` 成功，`0` 失败)。

## 使用示例

```json
{
    "tag": "SetWindowZOrder",
    "window": "Foreground",
    "order": "TopMost"
}
```
