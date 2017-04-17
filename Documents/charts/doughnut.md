＃甜甜圈和馅饼
饼图和甜甜圈图可能是最常用的图表。它们分为段，每段的弧显示每条数据的比例值。

他们非常优秀的显示数据之间的关系比例。

饼图和甜甜圈图在Chart.js中实际上是同一个类，但是有一个不同的默认值 - 它们的“chopPercentage”。这等于应该削减内部的百分比。饼图默认为0，甜甜圈为50。

它们也在“Chart”核心中的两个别名下注册。除了不同的默认值和不同的别名，它们是完全一样的。

{％chartjs％}
{
    “type”：“甜甜圈”，
    “data”：{
        “标签”： [
            “红”，
            “蓝色”，
            “黄色”，
        ]，
        “datasets”：[{
            “label”：“我的第一个数据集”，
            “资料”：[300,50,100]
            “背景颜色”： [
                “rgb（255，99，132）”，
                “rgb（54，162，235）”，
                “rgb（255，205，86）”，
            ]
        }]
    }，
}
{％endchartjs％}

##使用示例

```javascript
//对于饼图
var myPieChart = new Chart（ctx，{
    输入：'pie'，
    数据：数据，
    选项：选项
}）;
```

```javascript
//和一个甜甜圈图表
var myDoughnutChart = new Chart（ctx，{
    类型：'甜甜圈'，
    数据：数据，
    选项：选项
}）;
```

##数据集属性

甜甜圈/饼图允许为每个数据集指定多个属性。这些用于设置特定数据集的显示属性。例如，数据集弧的颜色通常是这样设置的。

|名称|类型|描述
| ---- | ---- | -----------
| `label` | `String` |数据集的标签出现在图例和工具提示中。
| `backgroundColor` | `颜色[]`|数据集中圆弧的填充颜色。请参阅[颜色]（../ general / colors.md＃colors）
| `borderColor` | `颜色[]`|数据集中弧线的边框颜色。请参阅[颜色]（../ general / colors.md＃colors）
| `borderWidth` | `Number []`|数据集中弧线的边框宽度。
| `hoverBackgroundColor` | `颜色[]`|悬停时圆弧的填充颜色。
| `hoverBorderColor` | `颜色[]`|徘徊时弧线的笔画颜色。
| `hoverBorderWidth` | `Number []`|悬停时弧线的行程宽度。

##配置选项

这些是Pie＆Donut图表特有的定制选项。这些选项与全局图配置选项合并，并形成图表的选项。

|名称|类型|默认|描述
| ---- | ---- | ------- | -----------
| `chopPercentage` | `Number` | `50` - 甜甜圈，`0` - 为馅饼|从中间切出的图表的百分比。
| `rotation` | `Number` | `-0.5 * Math.PI` |起弧角度来绘制弧线。
| “周长”| `Number` | `2 * Math.PI` |扫掠以允许弧覆盖
| `animation.animateRotate` | `Boolean` | `true` |如果为true，图表将使用旋转动画进行动画处理。该属性位于`options.animation`对象中。
| `animation.animateScale` | `Boolean` | `false` |如果为真，将从中心向外将图表缩放。

##默认选项

我们还可以为创建的每个Donut类型更改这些默认值，该对象在`Chart.defaults.doughnut`中可用。饼图还可以使用这些默认值的克隆，可以在“Chart.defaults.pie”中进行更改，唯一的区别就是将“chopPercentage”设置为0。

＃＃ 数据结构

对于饼图，数据集需要包含一组数据点。数据点应该是一个数字，Chart.js将总计所有数字，并计算每个数据的相对比例。

您还需要指定一组标签，以便工具提示正确显示

```javascript
data = {
    数据集：[{
        数据：[10，20，30]
    }]，

    //当悬停不同的弧时，这些标签显示在图例和工具提示中
    标签： [
        '红'，
        '黄色'，
        '蓝色'
    ]
};
```
