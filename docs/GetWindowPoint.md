# 获取窗口相对坐标 (GetWindowPoint)

根据窗口锚点（如 `TopLeft`, `TopRight`, `BottomLeft`, `BottomRight`, `Center`）结合像素偏移量计算相对窗口的屏幕物理坐标 (`Point`)。

## 平台与权限

* **支持平台**: `Windows`
* **权限要求**: 普通用户权限

## 运行参数

* **目标窗口 (`window`)**
  * 类型: `Wnd` / `string`
  * 默认值: `""`
  * 描述: 目标窗口对象、标题表达式或句柄。常用预设：`Foreground`。
* **相对方位 (`relative`)**
  * 类型: `string`
  * 默认值: `"TopLeft"`
  * 描述: 基准锚点方位：`TopLeft`, `TopRight`, `BottomLeft`, `BottomRight`, `Center`。
* **X 偏移 (`offset_x`)**
  * 类型: `number`
  * 默认值: `"0"`
  * 描述: 相对锚点的 X 轴像素偏移量。
* **Y 偏移 (`offset_y`)**
  * 类型: `number`
  * 默认值: `"0"`
  * 描述: 相对锚点的 Y 轴像素偏移量。

## 输出

* 类型: `Point`
* 描述: 计算得出的绝对屏幕坐标点结构。

## 使用示例

```json
{
    "tag": "GetWindowPoint",
    "window": "Foreground",
    "relative": "Center",
    "offset_x": 0,
    "offset_y": 0
}
```
