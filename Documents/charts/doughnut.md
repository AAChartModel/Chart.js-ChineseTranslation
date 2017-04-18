#环形图和扇形图
扇形图和环形图可能是最常用的图表。它们分为段，每段的弧显示每条数据的比例值。

他们非常优秀的显示数据之间的关系比例。

扇形图和环形图在Chart.js中实际上是同一个类，但是有一个不同的默认值 - 它们的“chopPercentage”。这等于应该削减内部的百分比。扇形图默认为0，环形图默认为50。

它们也在“Chart”核心中的两个别名下注册。除了不同的默认值和不同的别名，它们是完全一样的。

```javascript
{
    "type": "doughnut",//设置图形类别为环形图
    "data": {
        "labels": [
            "Red",
            "Blue",
            "Yellow",
        ],
        "datasets": [{
            "label": "我的第一个数据集",
            "data": [300, 50, 100],
            "backgroundColor": [
                "rgb(255, 99, 132)",
                "rgb(54, 162, 235)",
                "rgb(255, 205, 86)",
            ]
        }]
    },
```
 

##使用示例

```javascript
//扇形图
var myPieChart = new Chart(ctx,{
    type: 'pie',
    data: data,
    options: options
});
```

```javascript
//环形图
var myDoughnutChart = new Chart(ctx, {
    type: 'doughnut',
    data: data,
    options: options
});
```

##数据集属性

扇形图和环形图允许为每个数据集指定多个属性。这些用于设置特定数据集的显示属性。例如，数据集圆弧的颜色通常是这样设置的。

|名称|类型|描述
| ---- | ---- | -----------
| `label` | `String` |数据集的标签出现在图例和浮动提示框中。
| `backgroundColor` | `Color[]`|数据集中圆弧的填充颜色。请参阅[颜色](../general/colors.md#colors)
| `borderColor` | `Color[]`|数据集中弧线的轮廓描边颜色。请参阅[颜色](../general/colors.md#colors)
| `borderWidth` | `Number []`|数据集中弧线的轮廓描边宽度。
| `hoverBackgroundColor` | `Color[]`|悬停时圆弧的填充颜色。
| `hoverBorderColor` | `Color[]`|悬停时弧线的轮廓描边颜色。
| `hoverBorderWidth` | `Number []`|悬停时弧线的轮廓描边宽度。

##配置选项

这些是扇形图和环形图特有的定制选项。这些选项与全局图配置选项合并，并形成图表的选项。

|名称|类型|默认|描述
| ---- | ---- | ------- | -----------
| `chopPercentage` | `Number` | `50` - 环形图，`0` - 为扇形图|从中间切出的图表的百分比。
| `rotation` | `Number` | `-0.5 * Math.PI` |起弧角度来绘制弧线。
| “周长”| `Number` | `2 * Math.PI` |扫掠以允许弧覆盖
| `animation.animateRotate` | `Boolean` | `true` |如果为`true`，图表将使用旋转动画进行动画处理。该属性位于`options.animation`对象中。
| `animation.animateScale` | `Boolean` | `false` |如果为`true`，将从中心向外将图表缩放。

##默认选项

我们还可以为创建的每个`Donut`类型更改这些默认值，该对象在`Chart.defaults.doughnut`中可用。扇形图还可以使用这些默认值的克隆，可以在`Chart.defaults.pie`中进行更改，唯一的区别就是将`chopPercentage`设置为`0`。

##数据结构

对于扇形图，数据集需要包含一组数据点。数据点应该是一个数字，`Chart.js`将总计所有数字，并计算每个数据的相对比例。

您还需要指定一组标签，以便浮动提示框正确显示

```javascript
data = {
    datasets: [{
        data: [10, 20, 30]
    }],

    //当悬停不同在不同的圆弧上时，这些标签显示在图例和浮动提示框中
    labels: [
        'Red',
        'Yellow',
        'Blue'
    ]
};
```
