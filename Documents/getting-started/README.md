# Getting Started

开始使用`chart.js`!

首先,需要在我们的页面中有一个画布元素`<canvas>`.

```html
<canvas id="myChart"></canvas>
```
在拥有一个可供使用的画布元素`<canvas>`之后,我们需要在页面中包含`chart.js`。
 
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.4.0/Chart.min.js" />
```
好了,现在我们终于可以正式创建一个图表了。在页面中插入 JavaScript 内容:
```javascript
var ctx = document.getElementById('myChart').getContext('2d');
var chart = new Chart(ctx, {
    // The type of chart we want to create
    type: 'line',

    // 数据集的数据
    data: {
        labels: ["January", "February", "March", "April", "May", "June", "July"],
        datasets: [{
            label: "My First dataset",
            backgroundColor: 'rgb(255, 99, 132)',
            borderColor: 'rgb(255, 99, 132)',
            data: [0, 10, 5, 2, 20, 30, 45],
        }]
    },

    // 在这里设置图表的配置选项
    options: {}
});
```

 `Chart.js`很容易使用！在这里，您可以探索许多图表配置选项，可以帮助您使用缩放，浮动提示框，标签，颜色，自定义事件动作等自定义图表的样式和行为。
 

有很多Chart.js的例子可以在  `Chart.js.zip`中的文件夹`/samples`中找到, 这些文件依附于 [release](https://github.com/chartjs/Chart.js/releases).