# 布局配置

布局配置被传递到`options.layout`命名空间中。 图表布局的全局选项在`Chart.defaults.global.layout`中定义。

| 名称| 类型| 默认| 描述
| ----- | ---- | -------- | -----------
| `padding` | `Number`或`Object` | `0` | 填充图表中添加。 [更多...](＃padding)

## padding
如果该值是一个数字，它将应用于图表的所有方面（`左`，`上`，`右`，`下`）`。 如果这个值是一个对象，`left`属性定义左边的填充。 同样，也可以指定`right`，`top`和`bottom`属性。

假设你想在图表画布的左侧添加`50px`的填充，你可以这样做：

```javascript
let chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        layout: {
            padding: {
                left: 50,
                right: 0,
                top: 0,
                bottom: 0
            }
        }
    }
});
```
