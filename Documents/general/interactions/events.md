# 图表事件

以下属性定义图表如何与事件交互:

| 名称 | 类别 | 默认 | 描述
| ---- | ---- | ------- | -----------
| `events` | `String[]` | `["mousemove", "mouseout", "click", "touchstart", "touchmove", "touchend"]` | 事件选项定义了图表应该监听的工具提示和悬停的浏览器事件。  [more...](#event-option)
| `onHover` | `Function` | `null` |当任何事件触发时调用。 在图表的上下文中调用，并传递事件和一系列活动元素（条，点等）。
| `onClick` | `Function` | `null` |如果事件的类型为`mouseup`或`click`，则调用该函数。 在图表的上下文中调用，并传递事件和一系列活动元素

## 事件选项
例如，要让图表只响应点击事件，您可以这样做

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        //这个图表不会响应mousemove等
        events: ['click']
    }
});
```
