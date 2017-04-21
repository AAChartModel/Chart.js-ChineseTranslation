# 图例配置

图表图例显示有关图表上出现的区域的数据集的数据。

##配置选项
legend配置被传递到`options.legend`命名空间。图表图例的全局选项在“Chart.defaults.global.legend”中定义。

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `display` | `Boolean` | `true` |是显示的传奇
| `position` | `String` | `'top'` |图例的位置[更多...](#position)
| `fullWidth` | `Boolean` | `true` |标记这个框应该占据画布的整个宽度（按下其他框）。这在日常使用中不太可能需要改变。
| `onClick` | `Function`| |点击事件在标签项上注册时调用的回调
| `onHover` | `Function`| |在`mousemove`事件注册在标签项上时调用的回调
| `reverse` | `Boolean` | `false` | `Legend`将以相反的顺序显示数据集。
| `labels`| `Object` | |请参阅下面的[图例标签配置](＃legend-label-configuration)部分。

## 位置
图例的位置选项是：

* `'top'`//顶部
* `'left'`//左边👈
* `'bottom'`//底部
* `'right'`//右边👉

## 图例标签配置

图例标签配置使用`labels`键嵌套在图例配置下方。

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `boxWidth` | `Number` | `40` |彩盒宽度
| `fontSize` | `Number` | `12` |文字的字体大小
| `fontStyle` | `String` | `正常`|文字的字型
| `fontColor` |`Color`| `'＃666'` |文字颜色
| `fontFamily` | `String` | `Helvetica Neue`，`Helvetica`，`Arial`，`sans-serif`|字体系列的图例文字。
| `padding` | `Number` | `10` |彩色盒子之间的填充。
| `generateLabels` | `Function`| |为图例中的每个事物生成图例项目。默认实现返回颜色框的文本+样式。有关详细信息，请参阅[Legend Item](#chart-configuration-legend-item-interface)。
| `filter` | `Function`| `null` |从图例中过滤图例。接收2个参数， [Legend Item](#chart-configuration-legend-item-interface)和图表数据。
| `usePointStyle` | `Boolean` | `false` |标签样式将匹配相应的点样式（大小基于`fontSize`，在这种情况下不使用`boxWidth`）。




## 图例项目界面

传递给图例`onClick`函数的项是从`labels.generateLabels`返回的。这些项目必须实现以下界面。

```javascript
{
    //将要显示的标签
    text：String，

    //图例框的填充样式
    fillStyle：Color，

    //如果为true，则此项表示隐藏的数据集。标签将被渲染，具有贯穿效果
    hidden：Boolean，

    //对于小方块的边框请参阅https://developer.mozilla.org/en/docs/Web/API/CanvasRenderingContext2D/lineCap
    lineCap：String，

    //对于小方块的边框请参阅https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/setLineDash
    lineDash：Array [Number]，

    //对于小方块的边框请参阅https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineDashOffset
    lineDashOffset：Number，

    //对于小方块的边框请参阅https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineJoin
    lineJoin：String，

    //小方块的边框宽度
    lineWidth：Number，

    //图例小方块的中风风格
    strokeStyle：Color

    //图例小方块的点样式（仅在usePointStyle为true时使用）
    pointStyle：String
}
```

示例

以下示例将创建一个启用了图例的图表，并将所有文字变成红色。

```javascript
var chart = new Chart(ctx, {
    type: 'bar',
    data: data,
    options: {
        legend: {
            display: true,
            labels: {
                fontColor: 'rgb(255, 99, 132)'
            }
        }
}
});
```

## 自定义点击操作

想要在点击图例中的项目时触发不同的行为是常见的。这可以使用config对象中的回调轻松实现。

默认图例点击处理程序是：

```javascript

function（e，legendItem）{
    var index = legendItem.datasetIndex;
    var ci = this.chart;
    var meta = ci.getDatasetMeta（index）;

    //参见controller.isDatasetVisible注释
    meta.hidden = meta.hidden === null？ ！ci.data.datasets [index] .hidden：null;

    //我们隐藏了一个数据集...重新渲染图表
    ci.update（）;
}
```

假设我们希望链接前两个数据集的显示。我们可以相应地更改点击处理程序。

```javascript
var defaultLegendClickHandler = Chart.defaults.global.legend.onClick;
var newLegendClickHandler = function（e，legendItem）{
    var index = legendItem.datasetIndex;

    if（index> 1）{
        //做原始逻辑
        defaultLegendClickHandler（e，legendItem）;
    } else {
        让ci = this.chart;
        [ci.getDatasetMeta（0），
         ci.getDatasetM
```

假设我们希望链接前两个数据集的显示。我们可以相应地更改点击处理程序。

``` javascript
var defaultLegendClickHandler = Chart.defaults.global.legend.onClick;
var newLegendClickHandler = function（e，legendItem）{
    var index = legendItem.datasetIndex;

    if（index> 1）{
        //做原始逻辑
        defaultLegendClickHandler（e，legendItem）;
    } else {
        让ci = this.chart;
        [ci.getDatasetMeta（0），
         ci.getDatasetMeta（1）]。forEach（function（meta）{
            meta.hidden = meta.hidden === null？ ！ci.data.datasets [index] .hidden：null;
        }）;
        ci.update（）;
    }
};

var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        legend: {

        }
    }
});
```

现在当您单击此图表中的图例时，前两个数据集的可见性将被链接在一起。

## HTML图例

有时你需要一个非常复杂的传奇。在这些情况下，生成HTML图例是有意义的。图表在其原型上提供了一个`generateLegend（）`方法，该方法返回图例的HTML字符串。

要配置如何生成此图例，可以更改“legendCallback”配置属性。

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        legendCallback: function(chart) {
            // 返回 HTML 字符串
        }
    }
});
```
