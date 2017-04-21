# 响应式图表(用户可交互)


`Chart.js`提供了一些控制图表大小调整行为的选项。

| 名称 | 类别 | 默认 | 描述
| ---- | ---- | ------- | -----------
| `responsive` | `Boolean` | `true` | 调整图表画布的容器大小
| `responsiveAnimationDuration` | `Number` | `0` | 在调整大小事件后，以毫秒为单位的动画时间到新大小所需的时间
| `maintainAspectRatio` | `Boolean` | `true` |调整大小时，保持原始的画布宽高比`（width / height）`
| `onResize` | `Function` | `null` |发生调整大小时调用。 获取传递两个参数：图表实例和新大小