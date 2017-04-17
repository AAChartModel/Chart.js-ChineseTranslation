＃气泡图

气泡图用于同时显示三维数据。气泡的位置由前两个尺寸和相应的水平和垂直轴确定。第三维由个体气泡的大小表示。

{％chartjs％}
{
    “type”：“bubble”，
    “data”：{
        “datasets”：[{
            “label”：“第一个数据集”，
            “data”：[{
                “x”：20，
                “y”：30，
                “r”：15
            }，{
                “x”：40，
                “y”：10，
                “r”：10
            }]，
            “backgroundColor”：“rgb（255，99，132）”
        }]
    }，
}
{％endchartjs％}

##使用示例

```javascript
//对于气泡图
var myBubbleChart = new Chart（ctx，{
    键入：'bubble'，
    数据：数据，
    选项：选项
}）;
```

##数据集属性

气泡图允许为每个数据集指定多个属性。这些用于设置特定数据集的显示属性。例如，通常这样设置气泡的颜色。

除“label”之外的所有属性都可以指定为数组。如果将这些值设置为数组值，则第一个值适用于数据集中的第一个气泡，第二个值适用于第二个气泡，等等。

|名称|类型|描述
| ---- | ---- | -----------
| `label` | `String` |数据集的标签出现在图例和工具提示中。
| `backgroundColor` | `颜色/颜色[]`|气泡的填充颜色。
| `borderColor` | `颜色/颜色[]`|气泡的边框颜色。
| `borderWidth` | `Number / Number []`|点气泡的宽度以像素为单位。
| `hoverBackgroundColor` | `颜色/颜色[]`|气泡背景颜色悬停。
| `hoverBorderColor` | `颜色/颜色[]`|悬浮时的气泡边框颜色。
| `hoverBorderWidth` | `Number / Number []`|悬停时点的边界宽度。
| `hoverRadius` | `Number / Number []`|悬停时添加到数据半径的附加半径。

##配置选项

气泡图没有唯一的配置选项。要配置所有气泡共有的选项，使用[point element options]（../ configuration / elements / point.md＃point-configuration）。

##默认选项

我们也可以更改气泡图类型的默认值。这样做将使所有创建的气泡图在此之后创建新的默认值。气泡图的默认配置可以在`Chart.defaults.bubble`中访问。

＃＃ 数据结构

对于气泡图，数据集需要包含一组数据点。每个点都必须实现[bubble data object]（＃bubble-data-object）接口。

### Bubble Data Object

气泡图的数据以对象的形式传递。对象必须实现以下界面。重要的是要注意，图表中的radius属性`r`是**不**。它是在画布上绘制的气泡的原始半径（以像素为单位）。

```javascript
{
    // X值
    x：<Number>，

    // Y值
    y：<Number>，

    //气泡的半径这没有缩放。
    r：<Number>
}
```
