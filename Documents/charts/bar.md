#条形图
条形图提供了一种显示以垂直长条表示的数据值的方式。有时用于显示代表某一趋势的数据，并且可同时并排比较多个数据集。

```javascript
{
"type": "bar",
"data": {
"labels": [
"January", 
"February", 
"March", 
"April", 
"May", 
"June", 
"July"
],
"datasets": [{
"label": "My First Dataset",
"data": [65, 59, 80, 81, 56, 55, 40],
"fill": false,
"backgroundColor": [
"rgba(255, 99, 132, 0.2)",
"rgba(255, 159, 64, 0.2)",
"rgba(255, 205, 86, 0.2)",
"rgba(75, 192, 192, 0.2)",
"rgba(54, 162, 235, 0.2)",
"rgba(153, 102, 255, 0.2)",
"rgba(201, 203, 207, 0.2)"
],
"borderColor": [
"rgb(255, 99, 132)",
"rgb(255, 159, 64)",
"rgb(255, 205, 86)",
"rgb(75, 192, 192)",
"rgb(54, 162, 235)",
"rgb(153, 102, 255)",
"rgb(201, 203, 207)"
],
"borderWidth": 1
}]
},
"options": {
"scales": {
"yAxes": [{
"ticks": {
"beginAtZero": true
}
}]
}
}
}
```

##使用示例
```javascript
var myBarChart = new Chart(ctx, {
type: 'bar',
data: data,
options: options
});
```

##数据集属性
条形图允许为每个数据集指定多个属性。这些属性用于设置特定数据集的显示效果。例如，通常这样设置条形图中长条的颜色。

一些属性可以指定为数组。如果这些值设置为数组值，则第一个值适用于条形图中第一个长条，第二个值应用于条形图中第二个长条，以此类推。

|名称|类型|描述
| ---- | ---- | -----------
| `label` | `String` |数据集的标签出现在图例和浮动提示框中。
| `xAxisID` | `String` |打印此数据集的x轴的ID。如果未指定，则默认为第一个找到的x轴的ID
| `yAxisID` | `String` |要绘制此数据集的y轴的ID。如果未指定，则默认为首次找到的y轴的ID。
| `backgroundColor` | `Color/Color[]`|条形图的填充颜色。请参阅[颜色]（../ general / colors.md＃colors）
| `borderColor` | `Color/Color[]`|条形图轮廓描边的颜色。请参阅[颜色]（../ general / colors.md＃colors）
| `borderWidth` | `Number / Number []`|条的轮廓描边宽度（以像素为单位）。
| `borderSkipped` | `String` |哪个边缘跳过绘制边框。 [更多...]（＃borderSkipped）
| `hoverBackgroundColor` | `Color/Color[]`|悬停时条形图的填充颜色。
| `hoverBorderColor` | `Color/Color[]`|悬停时条形图的轮廓描边颜色。
| `hoverBorderWidth` | `Number / Number []`|悬停时条形图轮廓描边宽度。

### borderSkipped
此设置用于避免在填充底部绘制条形笔触。一般来说，除了创建从条形图导出的图表类型之外，不需要更改。

选项是：
* 'bottom'
* 'left'
* 'top'
* 'right'

##配置选项

条形图定义了以下配置选项。这些选项与全局图表配置选项“Chart.defaults.global”合并，以形成传递到图表的选项。

|名称|类型|默认|描述
| ---- | ---- | ------- | -----------
| `barPercentage` | `Number` | `0.9` |每个栏的可用宽度的百分比（0-1）应在类别百分比内。 1.0将占据整个类别的宽度，并将条形图放在彼此旁边。 [更多...]（＃bar-chart-barpercentage-vs-categorypercentage）
| `categoryPercentage` | `Number` | `0.8` |用于设置条形图中长条的每个数据点的可用宽度的百分比（0-1）（小数据集的网格线之间的间距）。 [更多...]（＃bar-chart-barpercentage-vs-categorypercentage）
| `barThickness` | `Number` | |手动设置每个栏的宽度（以像素为单位）。如果未设置，则使用“barPercentage”和“categoryPercentage”自动调整条形图;
| `maxBarThickness` | `Number` | |设置此项以确保自动调整的尺寸的尺寸不会大于此厚度。仅当barThickness未设置（启用自动调整大小）时才起作用。
| `gridLines.offsetGridLines` | `Boolean` | `true` |如果为true，则特定数据点的条形线落在网格线之间。如果为false，网格线将沿着条形图的中间。 [更多...]（＃offsetGridLines）

### offsetGridLines
如果为true，则特定数据点的条形线落在网格线之间。如果为false，网格线将沿着条形图的中间。这在实际开发环境中不太可能需要改变。它存在更多的方式通过配置存在重用轴代码

