# 集成

`Chart.js`可以与纯 JavaScript 集成或与不同的模块加载器集成,下面的例子显示了如何在不同的系统中加载 `chart.js`。
## ES6 模块

```javascript
import Chart from 'chart.js'
var myChart = new Chart(ctx, {...})
```

## Script 标签

```html
<script src="path/to/Chartjs/dist/Chart.js"></script>
<script>
var myChart = new Chart(ctx, {...})
</script>
```

## 常见的 JS

```javascript
var Chart = require('chart.js')
var myChart = new Chart(ctx, {...})
```

## Require JS

```javascript
require(['path/to/Chartjs/src/chartjs.js'], function(Chart){
    var myChart = new Chart(ctx, {...})
})
```