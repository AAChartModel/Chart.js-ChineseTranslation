# 折线图
线图是绘制线上数据点的一种方式。通常，它用于显示趋势数据或两个数据集的比较。

```javascript
{
    "type": "line",
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
            "borderColor": "rgb(75, 192, 192)",
            "lineTension": 0.1
        }]
    },
    "options": {

    }
```

## 使用示例
```javascript
var myLineChart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: options
});
```

## 数据集属性

折线图允许为每个数据集指定多个属性。这些用于设置特定数据集的显示属性。例如，通常以这种方式设置一行的颜色。

所有点*属性都可以指定为数组。如果这些值设置为数组值，则第一个值适用于第一个点，第二个值应用于第二个点，依此类推。

|名称|类型|描述
| ---- | ---- | -----------
| `label` | `String` |数据集的标签出现在图例和工具提示中。
| `xAxisID` | `String` |打印此数据集的x轴的ID。如果未指定，则默认为第一个找到的x轴的ID
| `yAxisID` | `String` |要绘制此数据集的y轴的ID。如果未指定，则默认为首次找到的y轴的ID。
| `backgroundColor` | `Color/Color[]`|填充颜​​色下线。请参阅[颜色](../general/colors.md#colors)
| `borderColor` | `Color/Color[]`|线的颜色。请参阅[颜色](../general/colors.md#colors)
| `borderWidth` | `Number / Number []`|行的宽度（以像素为单位）。
| `borderDash` | `Number []`|破折号的长度和间距。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/setLineDash)
| `borderDashOffset` | `Number` |线条破折号偏移。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineDashOffset)
| `borderCapStyle` | `String` |帽子风格的线条。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineCap)
| `borderJoinStyle` | `String` |线接合风格。请参阅[MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineJoin)
| `cubicInterpolationMode` | `String` |用于从离散数据点插入平滑曲线的算法。 [更多...](#cubicInterpolationMode)
| `fill` | `Boolean / String` |如何填写下面的区域。 [更多...](#fill)
| `lineTension` | `Number` |贝塞尔曲线张力线。设置为0以绘制直线。如果使用单调三次插值，则忽略此选项。
| `pointBackgroundColor` | `Color/Color[]`|点的填充颜色
| `pointBorderColor` | `Color/Color[]`|点的边框颜色。
| `pointBorderWidth` | `Number / Number []`|点边框的宽度（以像素为单位）。
| `pointRadius` | `Number / Number []`|点形状的半径。如果设置为0，则不渲染点。
| `pointStyle` | `String / String [] / Image / Image []`|风格的点。 [更多...](#pointStyle)
| `pointHitRadius` | `Number / Number []`|反映鼠标事件的非显示点的像素大小。
| `pointHoverBackgroundColor` | `Color/Color[]`|当悬停时指示背景颜色。
| `pointHoverBorderColor` | `Color/Color[]`|悬停时点边框颜色。
| `pointHoverBorderWidth` | `Number / Number []`|悬停时点的边界宽度。
| `pointHoverRadius` | `Number / Number []`|悬停点的半径。
| `showLine` | `Boolean` |如果为 false ，则不为此数据集绘制该行。
| `spanGaps` | `Boolean` |如果为 true ，则将在无数据或零数据的点之间绘制行。如果为 false ，则使用“NaN”数据的点将在行中创建一个中断
| `stepLine` | `Boolean / String` |如果线显示为阶梯线。  [更多...](#stepped-line)

### cubicInterpolationMode
支持以下插补模式：
*'默认'
*'单调'。

“默认”算法使用自定义加权立方插值，为所有类型的数据集生成令人愉快的曲线。

“单调”算法更适合于“y = f（x）”数据集：它保留正在插值的数据集的单调性（或分段单调性），并确保局部极值（如果有的话）保留在输入数据点。

如果保持不变（`undefined`），则使用全局`options.elements.line.cubicInterpolationMode`属性。

＃＃＃ 填
如果是“true”，请填写下面的区域。该行被填充到基线。如果y轴为0，则填充该线。如果轴只有负值，则该行将被填充到最高值。如果轴只有正值，则它被填充到最低值。

字符串值为fi

要填充到特定位置的字符串值是：
*''零'
*“顶”
*“底”

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

### Stepped Line
“stepsLine”支持以下值：
*`false`：无步骤插值（默认）
*`true`：插值之前（eq。'before'之前）
*`'before'`：插值之前的步骤
*`'after'`：逐步插值

如果“stepsLine”值设置为false以外的任何值，则“lineTension”将被忽略。

## 配置选项

折线图定义了以下配置选项。这些选项与全局图表配置选项“Chart.defaults.global”合并，以形成传递到图表的选项。

|名称|类型|默认|描述
| ---- | ---- | ------- | -----------
| `showLines` | `Boolean` | `true` |如果为 false，则不绘制点之间的线。
| `spanGaps` | `Boolean` | `false` |如果为 false，NaN数据会导致行中断。

## 默认选项

通常要将配置设置应用于所有创建的折线图。全局折线图设置存储在“Chart.defaults.line”中。更改全局选项仅影响更改后创建的图表。现有图表不变。

例如，要使用`spanGaps = true'配置所有折线图，您可以：
```javascript
Chart.defaults.line.spanGaps = true;
```

## 数据结构

折线图的数据集的“data”属性可以以两种格式传递。

### 号码[]
```javascript
data：[20，10]
```

当`data`数组是一个数字数组时，x轴通常是一个[category](../axes/cartesian/category.md#CategoryAxis)。使用它们在阵列中的位置将点放置在轴上。

### Point []

```javascript
data: [{
        x: 10,
        y: 20
    }, {
        x: 15,
        y: 10
    }]
```

此替代项用于稀疏数据集，例如[散点图](./scatter.md#scatter-chart)中的数据集。每个数据点都使用包含“x”和“y”属性的对象进行指定。

# 堆积区域图

可以通过更改y轴上的设置来将折线图配置为堆叠区域图，以启用堆叠。堆叠区域图可用于显示一个数据趋势如何由多个较小的部分组成。

```javascript
var stackedLine = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        scales: {
            yAxes: [{
                stacked: true
            }]
        }
    }
});
```

 # 高性能线图

当绘制大量数据时，图表渲染时间可能开始变得相当大。在这种情况下，可以使用以下策略来提高性能。

 ## 数据抽取

取消您的数据将取得最佳效果。当图形上显示的数据很多时，在图形上只显示数百个像素宽的数以万计的数据点是没有意义的。

数据抽取有许多方法，并且算法的选择将取决于您的数据和要实现的结果。例如,[min/max](http://digital.ni.com/public.nsf/allkb/F694FFEEA0ACF282862576020075F784)抽取将保留数据中的峰值，但每个像素最多可能需要4个点。这种类型的抽取对于您需要查看数据峰值的非常嘈杂的信号将会很好地工作。

## 禁用贝塞尔曲线

如果您在图表上绘制线条，则禁用贝塞尔曲线将提高渲染时间，因为绘制直线比贝塞尔曲线更加有效。

要禁用整个图表的贝塞尔曲线：

```javascript
new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        elements: {
            line: {
                tension: 0, // disables bezier curves
            }
        }
    }
});
```

绘制线图

如果你有很多数据点，那么禁止渲染数据集的行并且只绘制点，这样做可以更有效率。这样做意味着画布上的绘制效果会降低，从而提高渲染性能。

禁用行：

```javascript
new Chart(ctx, {
    type: 'line',
    data: {
        datasets: [{
            showLine: false, // disable for a single dataset
        }]
    },
    options: {
        showLines: false, // disable for all datasets
    }
});
```

## 禁用动画

如果您的图表具有较长的渲染时间，则禁用动画是一个好主意。这样做意味着图表只需要在更新期间呈现一次，而不是多次。这将具有减少CPU使用率和提高一般页面性能的效果。

 

## 禁用动画

如果您的图表具有较长的渲染时间，则禁用动画是一个好主意。 这样做意味着图表只需要在更新期间呈现一次，而不是多次。 这将具有减少CPU使用率和提高一般页面性能的效果。

禁用动画

```javascript
new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        animation: {
            duration: 0, // general animation time
        },
        hover: {
            animationDuration: 0, // duration of animations when hovering an item
        },
        responsiveAnimationDuration: 0, // animation duration after a resize
    }
});
```
