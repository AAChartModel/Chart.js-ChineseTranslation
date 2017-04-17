＃极地区

极地区域图与饼图类似，但每个段具有相同的角度 - 段的半径根据值而有所不同。

当我们想要显示类似于饼图的比较数据时，这种类型的图表通常很有用，但也显示上下文的值的比例。

{％chartjs％}
{
    “type”：“polarArea”，
    “data”：{
        “标签”： [
            “红”，
            “绿色”，
            “黄色”，
            “灰色”，
            “蓝色”
        ]，
        “datasets”：[{
            “label”：“我的第一个数据集”，
            “数据”：[11，16，7，3，14]，
            “背景颜色”： [
                “rgb（255，99，132）”，
                “rgb（75,192,192）”，
                “rgb（255，205，86）”，
                “rgb（201,203,207）”，
                “rgb（54，162，235）”
            ]
        }]
    }，
}
{％endchartjs％}

##使用示例

```javascript
新图表（ctx，{
    数据：数据，
    类型：'polarArea'，
    选项：选项
}）;
```

##数据集属性

极地区图表数据集中可以包含以下选项，以配置该特定数据集的选项。

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

这些是Polar Area图表特有的定制选项。这些选项与[全局图配置选项]（＃global-chart-configuration）合并，并形成图表的选项。

|名称|类型|默认|描述
| ---- | ---- | ------- | -----------
| `startAngle` | `Number` | `-0.5 * Math.PI` |起始角度来绘制数据集中第一个项目的弧线。
| `animation.animateRotate` | `Boolean` | `true` |如果为true，图表将使用旋转动画进行动画处理。该属性位于`options.animation`对象中。
| `animation.animateScale` | `Boolean` | `true` |如果为真，将从中心向外将图表缩放。

##默认选项

我们还可以为创建的每个PolarArea类型更改这些默认值，该对象在`Chart.defaults.polarArea`中可用。更改全局选项仅影响更改后创建的图表。现有图表不变。

例如，要使用`animateScale = false'配置所有新的极区图，您可以执行以下操作：
```javascript
Chart.defaults.polarArea.animation.animateScale = false;
```

＃＃ 数据结构

对于极地图，数据集需要包含一组数据点。数据点应该是一个数字，Chart.js将总计所有数字，并计算每个数据的相对比例。

您还需要指定一个标签数组，以便每个切片显示正确的工具提示。

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
