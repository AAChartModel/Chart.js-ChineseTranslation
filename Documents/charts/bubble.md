# 气泡图

气泡图用于显示一组三维数据。气泡图中气泡的位置由前两个维度(水平坐标 x 和垂直坐标 y )确定, 气泡的大小由第三个维度 r 来确定。

```javascript
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
```

## 使用示例

```javascript
//气泡图
var myBubbleChart = new Chart(ctx,{
    type: 'bubble',//设置图形类别为气泡图
    data: data, //设置图形数据
    options: options//设置图形属性配置选项
});
```

##数据集属性

气泡图允许为每个数据集指定多个属性。这些用于设置特定数据集的显示属性。例如，通常这样设置气泡的颜色。

除“label”之外的所有属性都可以指定为数组。如果将这些值设置为数组值，则第一个值适用于数据集中的第一个气泡，第二个值适用于第二个气泡，以此类推。

|名称|类型|描述
| ---- | ---- | -----------
| `label` | `String` |数据集的标签出现在图例和浮动提示框中。
| `backgroundColor` | `Color/Color[]`|气泡的填充颜色。
| `borderColor` | `Color/Color[]`|气泡的轮廓描边颜色。
| `borderWidth` | `Number / Number []`|气泡的轮廓描边的宽度(以像素为单位)。
| `hoverBackgroundColor` | `Color/Color[]`|悬停时的气泡背景颜色。
| `hoverBorderColor` | `Color/Color[]`|悬停时的气泡边框颜色。
| `hoverBorderWidth` | `Number / Number []`|悬停时点的边界宽度。
| `hoverRadius` | `Number / Number []`|悬停时添加到数据半径的附加半径。

## 配置选项

气泡图没有唯一的配置选项。要配置所有气泡共有的选项，使用[point element options]（../ configuration / elements / point.md＃point-configuration）。

## 默认选项

我们也可以更改气泡图类型的默认值。这样做将使所有创建的气泡图在此之后创建新的默认值。气泡图的默认配置可以在`Chart.defaults.bubble`中访问。

## 数据结构

对于气泡图，数据集需要包含一组数据点。每个点都必须实现[bubble data object]（＃bubble-data-object）接口。

### Bubble Data Object

气泡图的数据以对象的形式传递。对象必须实现以下界面。重要的是要注意，图表中的radius属性`r`是**不可缩放的**。它表示在气泡图上对应的气泡的原始半径（以像素为单位）。

```javascript
{
    // X轴坐标的值
    x：<Number>，

    // Y轴坐标的值
    y：<Number>，

    //气泡的半径大小(不可缩放)。
    r：<Number>
}
```
