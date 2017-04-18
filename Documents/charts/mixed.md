混合图表类型

使用`Chart.js`，可以创建两个或多个不同图表类型的组合的混合图表。一个常见的示例是还包括行数据集的条形图。

创建混合图表从初始化基本图表开始。

```javascript
var myChart = new Chart(ctx, {
  type: 'bar',
  data: data,
  options: options
});
```

在这一点上，我们有一个标准条形图。现在我们需要将其中一个数据集转换成行数据集。

```javascript
var mixedChart = new Chart(ctx, {
  type: 'bar',
  data: {
    datasets: [{
          label: 'Bar Dataset',
          data: [10, 20, 30, 40]
        }, {
          label: 'Line Dataset',
          data: [50, 50, 50, 50],

          // Changes this dataset to become a line
          type: 'line'
        }],
    labels: ['January', 'February', 'March', 'April']
  },
  options: options
});
```

在这一点上，我们有一个图表渲染我们想要的。请注意，在这种情况下，折线图的默认选项不会合并。只有默认类型的选项才会被合并。在这种情况下，这意味着条形图的默认选项将被合并，因为这是`type`字段指定的类型。

````javascript
{
  "type": "bar",
  "data": {
    "labels": [
      "January", 
      "February", 
      "March", 
      "April"
    ],
    "datasets": [{
      "label": "Bar Dataset",
      "data": [10, 20, 30, 40],
      "borderColor": "rgb(255, 99, 132)",
      "backgroundColor": "rgba(255, 99, 132, 0.2)"
    }, {
      "label": "Line Dataset",
      "data": [50, 50, 50, 50],
      "type": "line",
      "fill": false,
      "borderColor": "rgb(54, 162, 235)"
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