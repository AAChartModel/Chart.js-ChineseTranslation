# 浮动提示框

##浮动提示框配置

浮动提示框配置被传递到`options.tooltips`命名空间。图表浮动提示框的全局选项在“Chart.defaults.global.tooltips”中定义。

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `enabled` | `Boolean` | `true` |启用浮动提示框
| `custom` | `功能`| `null` |请参阅[自定义浮动提示框]（＃自定义浮动提示框）部分。
| `mode` | `String` | “最近”设置浮动提示框中出现的元素。 [more ...]（../ general / interactions / modes.md＃interaction-modes）。
| `intersect` | `Boolean` | `true` |如果为true，则浮动提示框模式仅在鼠标位置与元素相交时才适用。如果为false，该模式将随时应用。
| `position` | `String` | `'average'`|定位浮动提示框的模式。 [更多...]（＃位置模式）
| `callbacks` | `Object` | |参见[callbacks部分]（＃tooltip-callbacks）
| `itemSort` | `功能`| |排序浮动提示框项。 [更多...]（＃sort-callback）
| `filter` | `功能`| |过滤浮动提示框项。 [more ...]（＃filter-callback）
| `backgroundColor` |颜色| ``rgba（0,0,0,0.8）'`|背景颜色的浮动提示框。
| `titleFontFamily` | `String` | '''Helvetica Neue'，'Helvetica'，'Arial'，sans-serif“`|标题字体
| `titleFontSize` | `Number` | `12` |标题字体大小
| `titleFontStyle` | `String` | `'bold'` |标题字体样式
| `titleFontColor` |颜色| ``＃fff'` |标题字体颜色
| `titleSpacing` | `Number` | `2` |间距添加到每个标题行的顶部和底部。
| `titleMarginBottom` | `Number` | `6` |标题部分的底部添加保证金。
| `bodyFontFamily` | `String` | '''Helvetica Neue'，'Helvetica'，'Arial'，sans-serif“`|身体线字体
| `bodyFontSize` | `Number` | `12` |身体字体大小
| `bodyFontStyle` | `String` | ``正常'`|身体字型
| `bodyFontColor` |颜色| ``＃fff'` |正文字体颜色
| `bodySpacing` | `Number` | `2` |间距添加到每个浮动提示框项的顶部和底部。
| `footerFontFamily` | `String` | '''Helvetica Neue'，'Helvetica'，'Arial'，sans-serif“`|页脚字体
| `footerFontSize` | `Number` | `12` |页脚字体大小
| `footerFontStyle` | `String` | `'bold'` |页脚字型
| `footerFontColor` |颜色| ``＃fff'` |页脚字体颜色
| `footerSpacing` | `Number` | `2` |间距增加到每一条直线的顶部和底部。
| “footerMarginTop”| `Number` | `6` |绘制页脚之前添加的边距。
| `xPadding` | `Number` | `6` |填充在浮动提示框的左侧和右侧添加。
| `yPadding` | `Number` | `6` |填充以添加浮动提示框的顶部和底部。
| `caretPadding` | `Number` | `2` |额外距离将浮动提示框箭头的末端移开浮动提示框点。
| `caretSize` | `Number` | `5` |大小，以px为单位的浮动提示框箭头。
| `cornerRadius` | `Number` | `6` |浮动提示框角曲线半径。
| `multiKeyBackground` |颜色| ``＃fff'` |当多个项目位于浮动提示框中时，颜色会在彩色框后面绘制
| `displayColors` | `Boolean` | `true` |如果为真，则浮动提示框中会显示颜色框
| `borderColor` |颜色| ``rgba（0,0,0,0）'`|边框颜色
| `borderWidth` | `Number` | `0` |边界大小

###位置模式
 可能的模式有：
* '平均'
*'最近'

“平均”模式将浮动提示框放在浮动提示框中显示的项目的平均位置。 'nearest'将把浮动提示框放在离事件位置最近的元素的位置。

可以通过向Chart.Tooltip.positioners映射添加函数来定义新模式。

###排序回调

允许对[浮动提示框项目]进行排序（＃chart-configuration-tooltip-item-interface）。必须至少实现一个可以传递给[Array.prototype.sort]（https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort）的函数。此函数也可以接受传递给图表的数据对象的第三个参数。

###过滤回调

允许过滤[浮动提示框项目]（＃chart-configuration-tooltip-item-interface）。必须至少实现一个可以传递给[Array.prototype.filter]（https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/filter）的函数。此函数也可以接受传递给图表的数据对象的第二个参数。

##浮动提示框回调

浮动提示框标签配置使用`callbacks`键嵌套在浮动提示框配置下方。浮动提示框具有以下提供文本的回调。对于所有函数，“this”将是从Chart.Tooltip构造函数创建的浮动提示框对象。

使用相同的参数调用所有函数：a [tooltip item]（＃chart-configuration-tooltip-item-interface）和传递给图表的数据对象。所有函数必须返回字符串或字符串数​​组。字符串的数组被视为多行文本。

|名称|参数|描述
| ---- | --------- | -----------
| `beforeTitle` | `Array [tooltipItem]，data` |返回标题前要呈现的文字。
| `title` | `Array [tooltipItem]，data` |返回要作为浮动提示框的标题呈现的文本。
| `afterTitle` | `Array [tooltipItem]，data` |返回标题后呈现的文本。
| `beforeBody` | `Array [tooltipItem]，data` |返回在body部分之前呈现的文本。
| `beforeLabel` | `tooltipItem，data` |返回在单个标签之前呈现的文本。这将为浮动提示框中的每个项目调用。
| `label` | `tooltipItem，data` |返回在浮动提示框中为单个项目呈现的文本。
| `labelColor` | `tooltipItem，chart` |返回要为浮动提示框项目呈现的颜色。 [更多...]（＃label-color-callback）
| `afterLabel` | `tooltipItem，data` |返回在单个标签之后呈现的文本。
| `afterBody` | `Array [tooltipItem]，data` |返回在body部分后渲染的文本
| `beforeFooter` | `Array [tooltipItem]，data` |返回在页脚部分之前呈现的文本。
| `footer` | `Array [tooltipItem]，data` |返回文本以呈现为浮动提示框的页脚。
| `afterFooter` | `Array [tooltipItem]，data` |在页脚部分后面渲染的文字

###标签颜色回调

例如，要为浮动提示框中的每个项目返回一个红色框，您可以执行以下操作：
```javascript
var chart = new Chart（ctx，{
    输入：'line'，
    数据：数据，
    选项：{
        浮动提示框：{
            回调：{
                labelColor：function（tooltipItem，chart）{
                    返回{
                        borderColor：'rgb（255，0，0）'，
                        backgroundColor：'rgb（255，0，0）'
                    }
                }
            }
        }
    }
}）;
```


###浮动提示框项目界面

传递给浮动提示框回调的浮动提示框项实现以下界面。

```javascript
{
    // X浮动提示框的值作为字符串
    xLabel：String，

    //浮动提示框的Y值作为字符串
    yLabel：String，

    //项目来源的数据集的索引
    datasetIndex：Number，

    //数据集中此数据项的索引
    索引号：

    //匹配点的X位置
    x：数字，

    // Y位置的匹配点
    y：数字，
}
```
##浮动提示框回调

浮动提示框标签配置使用`callbacks`键嵌套在浮动提示框配置下方。浮动提示框具有以下提供文本的回调。对于所有函数，“this”将是从Chart.Tooltip构造函数创建的浮动提示框对象。

使用相同的参数调用所有函数：a [tooltip item]（＃chart-configuration-tooltip-item-interface）和传递给图表的数据对象。所有函数必须返回字符串或字符串数​​组。字符串的数组被视为多行文本。

|名称|参数|描述
| ---- | --------- | -----------
| `beforeTitle` | `Array [tooltipItem]，data` |返回标题前要呈现的文字。
| `title` | `Array [tooltipItem]，data` |返回要作为浮动提示框的标题呈现的文本。
| `afterTitle` | `Array [tooltipItem]，data` |返回标题后呈现的文本。
| `beforeBody` | `Array [tooltipItem]，data` |返回在body部分之前呈现的文本。
| `beforeLabel` | `tooltipItem，data` |返回在单个标签之前呈现的文本。这将为浮动提示框中的每个项目调用。
| `label` | `tooltipItem，data` |返回在浮动提示框中为单个项目呈现的文本。
| `labelColor` | `tooltipItem，chart` |返回要为浮动提示框项目呈现的颜色。 [更多...]（＃label-color-callback）
| `afterLabel` | `tooltipItem，data` |返回在单个标签之后呈现的文本。
| `afterBody` | `Array [tooltipItem]，data` |返回在body部分后渲染的文本
| `beforeFooter` | `Array [tooltipItem]，data` |返回在页脚部分之前呈现的文本。
| `footer` | `Array [tooltipItem]，data` |返回文本以呈现为浮动提示框的页脚。
| `afterFooter` | `Array [tooltipItem]，data` |在页脚部分后面渲染的文字

###标签颜色回调

例如，要为浮动提示框中的每个项目返回一个红色框，您可以执行以下操作：
```javascript
var chart = new Chart（ctx，{
    输入：'line'，
    数据：数据，
    选项：{
        浮动提示框：{
            回调：{
                labelColor：function（tooltipItem，chart）{
                    返回{
                        borderColor：'rgb（255，0，0）'，
                        backgroundColor：'rgb（255，0，0）'
                    }
                }
            }
        }
    }
}）;
```


###浮动提示框项目界面

传递给浮动提示框回调的浮动提示框项实现以下界面。

```javascript
{
    // X浮动提示框的值作为字符串
    xLabel：String，

    //浮动提示框的Y值作为字符串
    yLabel：String，

    //项目来源的数据集的索引
    datasetIndex：Number，

    //数据集中此数据项的索引
    索引号：

    //匹配点的X位置
    x：数字，

    // Y位置的匹配点
    y：数字，
}
```...```
有关如何开始的示例，请参阅`samples / tooltips / line-customTooltips.html`。

##浮动提示框模型
浮动提示框模型包含可用于呈现浮动提示框的参数。

```javascript
{
    //我们在浮动提示框中呈现的项目。请参阅浮动提示框项目界面部分
    dataPoints：TooltipItem []，

    //定位
    xPadding：数字，
    yPadding：数量，
    xAlign：String，
    yAlign：String，

    // X和Y属性是浮动提示框的左上角
    x：数字，
    y：数字，
    width：Number，
    身高：数量，
    //浮动提示框指向的位置
    caretX：数量，
    carety：数字，

    // 身体
    //需要呈现的正文行
    //每个pbject包含3个参数
    // before：String [] //行之前的文本行与颜色正方形
    // lines：String []，//要渲染的文本行作为带有正方形的主要项目
    // after：String []，//在主行后面渲染的文本行
    body：Object []，
    //出现在标题之后但在正文之前的文本行
    beforeBody：String []，
    //出现在正文后面的文本行
    afterBody：String []，
    bodyFontColor：颜色，
    _bodyFontFamily：String，
    _bodyFontStyle：String，
    _bodyAlign：String，
    bodyFontSize：Number，
    bodySpacing：Number，

    //标题
    //形成标题的文本行
    title：String []，
    titleFontColor：Color，
    _titleFontFamily：String，
    _titleFontStyle：String，
    titleFontSize：Number，
    _titleAlign：String，
    titleSpacing：Number，
    titleMarginBottom：Number，

    //页脚
    //形成页脚的文本行
    footer：String []，
    footerFontColor：颜色，
    _footerFontFamily：String，
    _footerFontStyle：String，
    footerFontSize：Number，
    _footerAlign：String，
    footerSpacing：Number，
    footerMarginTop：Number，

    //外观
    caretSize：数字，
    cornerRadius：Number，
    backgroundColor：颜色，

    //为body []中的每个项目呈现颜色。这是浮动提示框中的正方形的颜色
    labelColors：Color []，

    // 0 opacity是一个隐藏的浮动提示框
    不透明度：数字，
    legendColorBackground：颜色，
    displayColors：Boolean，
}
```
