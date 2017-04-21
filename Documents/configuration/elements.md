# 元素

虽然图表类型提供了配置每个数据集的样式的设置，但有时您需要以同样的方式对所有数据集进行样式**。一个常见的例子是用相同颜色描绘条形图中的所有条，但是更改每个数据集的填充。可以为四种不同类型的元素配置选项： **[圆弧](#圆弧配置)**, **[线条](#线条配置)**, **[点](#点配置)**, 和 **[矩形](#矩形配置)**。设置时，这些选项适用于该类型的所有对象，除非被附加到数据集的配置专门覆盖。

## 全局配置

可以按图表或全局指定元素选项。元素的全局选项在`Chart.defaults.global.elements`中定义。例如，要设置全局所有条形图的边框宽度，您可以执行以下操作：

```javascript
Chart.defaults.global.elements.rectangle.borderWidth = 2;
```

## 点配置
点元素用于表示折线图或气泡图中的点。

全局点选项：`Chart.defaults.global.elements.point`

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `radius` | `Number` | `3` |点半径
| `pointStyle` | `String` | `circle` |点样式
| `backgroundColor` | `Color`| ``rgba（0,0,0,0.1）'`|点填充颜色。
| `borderWidth` | `Number` | `1` |点行程宽度。
| `borderColor` | `Color`| ``rgba（0,0,0,0.1）'`|点笔画颜色。
| `hitRadius` | `Number` | `1` |额外半径添加到点半径，用于命中检测。
| `hoverRadius` | `Number` | `4` |悬停时的点半径
| `hoverBorderWidth` | `Number` | `1` |徘徊时的行程宽度。

## 线条配置
线条元素用于表示折线图中的线条。

全局行选项：`Chart.defaults.global.elements.line` 

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `tension `| `Number` | `0.4` |贝塞尔曲线张力（没有贝塞尔曲线'0'）
| `backgroundColor` | `Color`| ``rgba（0,0,0,0.1）'`|线条填充颜色
| `borderWidth` | `Number` | `3` |线行宽
| `borderColor` | `Color `| ``rgba（0,0,0,0.1）'`|线笔画颜色
| `borderCapStyle` | `String` | ``butt`` |线帽样式（请参阅[MDN]（https://developer.mozilla.org/en/docs/Web/API/CanvasRenderingContext2D/lineCap））
| `borderDash` | `Array` | `[]`|换行符（请参阅[MDN]（https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/setLineDash））
| `borderDashOffset` | `Number` | `0` |换行符偏移量（参见[MDN]（https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineDashOffset））
| `borderJoinStyle` | `String` | `miter` |行连接样式（请参阅[MDN]（https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineJoin））
| `capBezierPoints` | `Boolean` | `true` | `true`将Bézier控件保留在图表中，`false`没有限制
| `fill` | `Boolean/String` | `true` |填写位置：`零`，`顶`，`底`，`真`（等式`零`）或`假`（无填）
| `step` | `Boolean` | `false` | `true`将线显示为分阶线（`张力`将被忽略）

## 矩形配置
矩形元素用于表示条形图中的条形。

全局矩形选项：`Chart.defaults.global.elements.rectangle`

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `backgroundColor` | `Color`| ``rgba（0,0,0,0.1）'`|酒吧填色。
| `borderWidth` | `Number` | `0` |行程宽度。
| `borderColor` | `Color`| ``rgba（0,0,0,0.1）'`|酒吧中风色。
| `borderSkipped` | `String` | `'bottom'` |跳过（不包括）边界：`底部`，`左`，`顶`或`右`。

## 圆弧配置
圆弧用于极地图，环形图和扇形图。

全局弧选项：`Chart.defaults.global.elements.arc`

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `backgroundColor` | `Color`| ``rgba（0,0,0,0.1）``|圆弧的填充颜色
| `borderColor` | `Color`| ``＃fff`` |圆弧的轮廓描边颜色
| `borderWidth` | `Number` | `2` |圆弧的轮廓描边
