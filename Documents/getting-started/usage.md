# 用法
`Chart.js`可以与ES6模块，纯JavaScript和模块加载程序一起使用。

 

## 创建图表

要创建图表，我们需要实例化`Chart`类。在实例化一个`chart`类时，我们需要传递我们想要绘制图表的`画布的节点`，`jQuery实例`,又或者`2d的上下文`。示例如下:

```html
<canvas id="myChart" width="400" height="400"></canvas>
```

```javascript
// 可以使用以下表达式中的任意一个
var ctx = document.getElementById("myChart");
var ctx = document.getElementById("myChart").getContext("2d");
var ctx = $("#myChart");
var ctx = "myChart";
```
一旦拥有元素或上下文，就可以实例化一个预定义的图表类型，或创建自己的图表。

以下示例实例化一个条形图，显示不同颜色的投票数，y轴从0开始。
 
```html
<canvas id="myChart" width="400" height="400"></canvas>
<script>
var ctx = document.getElementById("myChart");
var myChart = new Chart(ctx, {
    type: 'bar',
    data: {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [{
            label: '# of Votes',
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
                'rgba(255, 99, 132, 0.2)',
                'rgba(54, 162, 235, 0.2)',
                'rgba(255, 206, 86, 0.2)',
                'rgba(75, 192, 192, 0.2)',
                'rgba(153, 102, 255, 0.2)',
                'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
                'rgba(255,99,132,1)',
                'rgba(54, 162, 235, 1)',
                'rgba(255, 206, 86, 1)',
                'rgba(75, 192, 192, 1)',
                'rgba(153, 102, 255, 1)',
                'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
        }]
    },
    options: {
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero:true
                }
            }]
        }
    }
});
</script>
```