＃标题

图表标题定义要在图表顶部绘制的文本。

##标题配置
标题配置被传递到`options.title`命名空间。图表标题的全局选项在“Chart.defaults.global.title”中定义。

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `display` | `Boolean` | `false` |是显示的标题
| `position` | `String` | `'top'` |标题的位置[更多...]（＃位置）
| `fontSize` | `Number` | `12` |字体大小
| `fontFamily` | `String` | '''Helvetica Neue'，'Helvetica'，'Arial'，sans-serif“`|字体系列为标题文本。
| `fontColor` |颜色| `'＃666'` |字体颜色
| `fontStyle` | `String` | `'bold'` |字体样式
| `padding` | `Number` | `10` |在标题文本上方和下方添加的像素数。
| `text` | `String` | “”“标题文字ti显示

###职位
可能的标题位置值为：
*“顶”
*`'左''
*“底”
*“对”

##使用示例

以下示例将在创建的图表上创建“自定义图表标题”的标题。

```javascript
var chart = new Chart（ctx，{
    输入：'line'，
    数据：数据，
    选项：{
        标题：{
            显示：真，
            文字：“自定义图表标题”
        }
    }
}）
```
