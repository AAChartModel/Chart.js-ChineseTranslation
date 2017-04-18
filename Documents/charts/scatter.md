＃散点图

在 chart.js 中,散点图是基于折线图,是在折线图基础上的一个变体。要使用散点图，要显示的数据必须为带有 x 轴和 y 轴坐标点的字典对象。下面的代码示例创建了一个带有三个点的散点图:

```javascript
var scatterChart = new Chart(ctx, {
    type: 'scatter',
    data: {
        datasets: [{
            label: 'Scatter Dataset',
            data: [{
                x: -10,
                y: 0
            }, {
                x: 0,
                y: 10
            }, {
                x: 10,
                y: 5
            }]
        }]
    },
    options: {
        scales: {
            xAxes: [{
                type: 'linear',
                position: 'bottom'
            }]
        }
    }
});```

##数据集属性
散点图支持与[折线图](./line.md#dataset-properties)相同的所有的属性配置.

＃＃ 数据结构

与可以用两种不同格式来设置data数据的折线图不同，散点图仅支持带有 x 轴和 y 轴坐标点的格式的数据。 示例如下:

```javascript
data: [{
        x: 10,
        y: 20
    }, {
        x: 15,
        y: 10
    }]
```
