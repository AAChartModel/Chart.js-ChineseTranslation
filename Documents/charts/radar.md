# 雷达图
雷达图是显示多个数据点及其变化的方式。

它们通常用于比较两个或多个不同数据集的点。

```javascript
{
    "type": "radar",
    "data": {
        "labels": [
            "Eating", 
            "Drinking", 
            "Sleeping", 
            "Designing",
            "Coding",
            "Cycling",
            "Running"
        ],
        "datasets": [{
            "label": "My First Dataset",
            "data": [65, 59, 90, 81, 56, 55, 40],
            "fill": true,
            "backgroundColor": "rgba(255, 99, 132, 0.2)",
            "borderColor": "rgb(255, 99, 132)",
            "pointBackgroundColor": "rgb(255, 99, 132)",
            "pointBorderColor": "#fff",
            "pointHoverBackgroundColor": "#fff",
            "pointHoverBorderColor": "rgb(255, 99, 132)",
            "fill": true
        }, {
            "label": "My Second Dataset",
            "data": [28, 48, 40, 19, 96, 27, 100],
            "fill": true,
            "backgroundColor": "rgba(54, 162, 235, 0.2)",
            "borderColor": "rgb(54, 162, 235)",
            "pointBackgroundColor": "rgb(54, 162, 235)",
            "pointBorderColor": "#fff",
            "pointHoverBackgroundColor": "#fff",
            "pointHoverBorderColor": "rgb(54, 162, 235)",
            "fill": true
        }]
    },
    "options": {
        "elements": {
            "line": {
                "tension": 0,
                "borderWidth": 3
            }
        }
    }
}
```

## 使用示例
```javascript
var myRadarChart = new Chart(ctx, {
    type: 'radar',
    data: data,
    options: options
});
```

## 数据集属性

雷达图表允许为每个数据集指定多个属性。这些用于设置特定数据集的显示属性。例如，通常以这种方式设置一行的颜色。

所有点*属性都可以指定为数组。如果这些值设置为数组值，则第一个值适用于第一个点，第二个值应用于第二个点，依此类推。

|名称|类型|描述
| ---- | ---- | -----------
| `label`|`String` |数据集的标签出现在图例和工具提示中。
| `backgroundColor`|`Color/Color[]`|填充颜​​色下线。请参阅[Colors](../general/colors.md#colors)
| `borderColor`|`Color/Color[]`|线的颜色。请参阅[颜色](../general/colors.md#colors)
| `borderWidth`|`Number/Number[]`|行的宽度（以像素为单位）。
| `borderDash`|`Number[]`|破折号的长度和间距。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/setLineDash)
| `borderDashOffset`|`Number` |线条破折号偏移。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineDashOffset)
| `borderCapStyle` | `String` |帽子风格的线条。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineCap)
| `borderJoinStyle` | `String` |线接合风格。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineJoin)
| `fill` | `Boolean/String` |如何填写下面的区域。 [更多...](#fill)
| `lineTension`|`Number` |贝塞尔曲线张力线。设置为0以绘制直线。
| `pointBackgroundColor` |`Color/Color[]`|点的填充颜色
| `pointBorderColor` |`Color/Color[]`|点的边框颜色。
| `pointBorderWidth` |`Number/Number []`|点边框的宽度（以像素为单位）。
| `pointRadius` |`Number/Number[]`|点形状的半径。如果设置为0，则不渲染点。
| `pointStyle` |`String/String[]/Image/Image[]`|风格的点。  [更多...](#pointStyle)）
| `pointHitRadius` |`Number/Number[]`|反映鼠标事件的非显示点的像素大小。
| `pointHoverBackgroundColor`|`Color/Color[]`|当悬停时指示背景颜色。
| `pointHoverBorderColor`|`Color/Color[]`|悬停时点边框颜色。
| `pointHoverBorderWidth`|`Number/Number[]`|悬停时点的边界宽度。
| `pointHoverRadius`|`Number/Number[]`|悬停点的半径。

### pointStyle
点的风格。选项是：
* 'circle'
* 'cross'
* 'crossRot'
* 'dash'. 
* 'line'
* 'rect'
* 'rectRounded'
* 'rectRot'
* 'star'
* 'triangle'

如果该选项是图像，则使用[drawImage](https://developer.mozilla.org/en/docs/Web/API/CanvasRenderingContext2D/drawImage)在画布上绘制该图像。

## 配置选项

与其他图表不同，雷达图表中没有图表特定的选项。

## 比例选项

雷达图只支持一个刻度。这个比例的选项在`scale`属性中定义。

```javascript
options = {
    scale: {
        // Hides the scale
        display: false
    }
};
```


## 默认选项

通常要将配置设置应用于所有创建的雷达图表。 全局雷达图设置存储在`Chart.defaults.radar`中。 更改全局选项仅影响更改后创建的图表。 现有图表不变。

## 数据结构

雷达图表的数据集的`data`属性被指定为数组。 数据数组中的每个点对应于x轴上相同索引处的标签。

```javascript
data：[20，10]
```

对于雷达图表，为了提供每个点意味着什么的上下文，我们包括一个围绕图表中每个点显示的字符串数组。

```javascript
data: {
    labels: ['Running', 'Swimming', 'Eating', 'Cycling'],
    datasets: [{
        data: [20, 10, 4, 2]
    }]
}
```
