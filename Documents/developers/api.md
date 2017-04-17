＃图表原型方法

对于每个图表，在共享的“ChartType”上有一组全局原型方法，您可能会发现它们很有用。这些都可以在使用Chart.js创建的所有图表上可用，但是对于示例，我们使用我们所做的折线图。

```javascript
// 例如：
var myLineChart = new Chart（ctx，config）;
```

## .destroy（）

使用它来销毁创建的任何图表实例。这将清除Chart.js中存储到图表对象的任何引用以及Chart.js附加的任何关联的事件侦听器。
在画布重新用于新图表之前，必须先调用它。

```javascript
//销毁特定的图表实例
myLineChart.destroy（）;
```

##.update（duration，lazy）

触发图表的更新。这可以在更新数据对象后安全地调用。这将更新所有比例，图例，然后重新渲染图表。

```javascript
//持续时间是重绘动画的时间，以毫秒为单位
// lazy是一个布尔值。如果是真的，动画可以被其他动画打断
myLineChart.data.datasets [0] .data [2] = 50; //将第一个数据集的“March”值更新为50
myLineChart.update（）; //呼叫更新现在将3月的位置从90移动到50。
```

> **注意：**替换数据引用（例如`myLineChart.data = {datasets：[...]}`只起始于2.6版**，在此之前，可以通过替换整个数据对象以下解决方法：`myLineChart.config.data = {datasets：[...]}`。

＃＃ 。重启（）

在初始动画之前将图表重置为状态。然后可以使用`update`触发新的动画。

```javascript
myLineChart.reset（）;
```

## .render（持续时间，懒惰）

触发重绘所有图表元素。请注意，这不会更新新数据的元素。在这种情况下使用`.update（）`。
```javascript
//持续时间是重绘动画的时间，以毫秒为单位
// lazy是一个布尔值。如果是真的，动画可以被其他动画打断
myLineChart.render（duration，lazy）;
```

＃＃ 。停止（）

使用它来停止任何当前的动画循环。这将在任何当前动画帧期间暂停图表。调用`.render（）`来重新动画。

```javascript
//停止其当前帧的图表动画循环
myLineChart.stop（）;
// =>为可链接性返回'this'
```

## .resize（）

使用此手动手动调整canvas元素的大小。每次调整画布容器的大小时都会运行此操作，但是如果更改画布节点容器元素的大小，则可以手动调用此方法。

```javascript
//调整大小并重新绘制以填充其容器元素
myLineChart.resize（）;
// =>为可链接性返回'this'
```

## .clear（）

将清除图表画布。在动画帧之间广泛使用，但您可能会发现它很有用。

```javascript
//将清除绘制myLineChart的画布
myLineChart.clear（）;
// =>为可链接性返回'this'
```

## .toBase64Image（）

这将在当前状态下返回图表的基本64位编码字符串。

```javascript
myLineChart.toBase64Image（）;
// =>返回画布上图像的png数据url
```

## .generateLegend（）

返回该图表的图例的HTML字符串。图例从选项中的“legendCallback”生成。

```javascript
myLineChart.generateLegend（）;
// =>返回此图表的图例的HTML字符串
```

## .getElementAtEvent（e）

传递事件的参数或jQuery事件的Chart实例上调用`getElementAtEvent（event）`将会返回事件位置的单个元素。如果范围内有多个项目，则只返回第一个。从此方法返回的值是具有单个参数的数组。一个数组用于在`get * AtEvent`方法之间保持一致的API。

```javascript
myLineChart.getElementAtEvent（e）;
// =>返回事件点的第一个元素。
```

## .getElementsAtEvent（e）

查找事件点下的元素，然后返回相同数据索引处的所有元素。这在内部用于“标签”模式突出显示。

传递事件参数或jQuery事件的Chart实例上调用`getElementsAtEvent（event）`将返回与该事件相同位置的点元素。

```javascript
canvas.onclick = function（evt）{
    var activePoints = myLineChart.getElementsAtEvent（evt）;
    // => activePoints是画布上与点击事件位置相同的点数组。
};
```

此功能对于实现基于DOM的工具提示或触发应用程序中的自定义行为可能很有用。

## .getDatasetAtEvent（e）

查找事件点下的元素，然后返回该数据集中的所有元素。这在'数据集'模式突出显示中被内部使用

```javascript
myLineChart.getDatasetAtEvent（e）;
// =>返回一个元素数组
```

## .getDatasetMeta（index）

查找与当前索引匹配的数据集并返回该元数据。该返回的数据具有用于构建图表的所有元数据。

元数据的“data”属性将包含有关每个点，矩形等的信息，具体取决于图表类型。

[Chart.js测试]（https://github.com/chartjs/Chart.js/tree/master/test）中提供了大量使用示例。

```javascript
var meta = myChart.getDatasetMeta（0）;
var x = meta.data [0] ._ model.x
```
