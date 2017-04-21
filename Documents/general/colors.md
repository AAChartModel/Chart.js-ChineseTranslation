# 颜色
当向Chart选项提供颜色时，可以使用多种格式。 您可以将颜色指定为十六进制，RGB或HSL符号中的字符串。 如果需要颜色但未指定颜色，`Chart.js`将使用全局默认颜色。 此颜色存储在`Chart.defaults.global.defaultColor`中。 它最初设置为`rgba（0，0，0，0.1）`。

您也可以传递[CanvasGradient](https://developer.mozilla.org/en-US/docs/Web/API/CanvasGradient)对象。 在传递到图表之前，您将需要创建它，但使用它可以实现一些有趣的效果。

## 模式和渐变
一个替代选项是传递[CanvasPattern](https://developer.mozilla.org/en-US/docs/Web/API/CanvasPattern)或[CanvasGradient](https://developer.mozilla.org/en/docs/Web/API/CanvasGradient)对象，而不是字符串颜色。

例如，如果要从图像中填充图案的数据集，则可以执行以下操作。



```javascript
var img = new Image();
img.src = 'https://example.com/my_image.png';
img.onload = function() {
    var ctx = document.getElementById('canvas').getContext('2d');
    var fillPattern = ctx.createPattern(img, 'repeat');

    var chart = new Chart(ctx, {
        data: {
            labels: ['Item 1', 'Item 2', 'Item 3'],
            datasets: [{
                data: [10, 20, 30],
                backgroundColor: fillPattern
            }]
        }
    })
}
```
使用图形填充数据图形可以帮助具有视力缺陷（例如色盲或局部视觉）的观众[更容易的了解您的数据](http://betweentwobrackets.com/data-graphics-and-colour-vision/)。

使用 [Patternomaly](https://github.com/ashiguruma/patternomaly) 库可以生成填充数据集的模式。


```javascript
var chartData = {
    datasets: [{
        data: [45, 25, 20, 10],
        backgroundColor: [
            pattern.draw('square', '#ff6384'),
            pattern.draw('circle', '#36a2eb'),
            pattern.draw('diamond', '#cc65fe'),
            pattern.draw('triangle', '#ffce56'),
        ]
    }],
    labels: ['Red', 'Blue', 'Purple', 'Yellow']
};
```