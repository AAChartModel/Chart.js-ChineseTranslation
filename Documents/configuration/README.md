＃配置

该配置用于更改图表的行为。有属性来控制样式，字体，图例等。

##全局配置

这个概念在Chart.js 1.0中引入，以保持配置[DRY]（https://en.wikipedia.org/wiki/Don%27t_repeat_yourself），并允许在图表类型之间全局更改选项，避免了为每个实例或特定图表类型的默认值。

Chart.js将传递给图表的选项对象与使用图表类型默认值的全局配置合并，并适当缩放默认值。这样，您可以按照您在单个图表配置中的特定要求，同时在适用的情况下仍然更改所有图表类型的默认值。全局常规选项在“Chart.defaults.global”中定义。每个图表类型的默认值在该图表类型的文档中讨论。

以下示例将将所有图表的悬停模式设置为“最近”，其中图表类型默认值不会被覆盖，或者在创建时传递给构造函数的选项。

```javascript
Chart.defaults.global.hover.mode ='nearest';

//悬停模式设置为最近，因为它不被覆盖
var chartHoverModeNearest = new Chart（ctx，{
    输入：'line'，
    数据：数据，
}）;

//此图表将具有传入的悬停模式
var chartDifferentHoverMode = new Chart（ctx，{
    输入：'line'，
    数据：数据，
    选项：{
        悬停：{
            //覆盖全局设置
            模式：'index'
        }
    }
}）
```
