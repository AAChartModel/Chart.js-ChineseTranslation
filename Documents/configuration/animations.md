＃动画

Chart.js开箱即用动画图表。提供了许多选项来配置动画的外观以及花费的时间

##动画配置

以下动画选项可用。全局选项在“Chart.defaults.global.animation”中定义。

|名称|类型|默认|描述
| ----- | ---- | -------- | -----------
| `duration` | `Number` | `1000` |动画所需的毫秒数。
| `easing` | `String` | ``easeOutQuart'` |缓解功能使用。 [更多...]（＃宽松）
| `onProgress` | `功能`| `null` |回调调用动画的每一步。 [更多...]（＃animation-callbacks）
| `onComplete` | `功能`| `null` |回调在动画结束时调用。 [更多...]（＃animation-callbacks）

缓解
 可用选项有：
*“线性”
*`'easeInQuad'`
*`'easeOutQuad'`
*`'easeInOutQuad'`
*``easeInCubic``
*“easeOutCubic”
*`'easeInOutCubic'`
*`'easeInQuart'`
*`'easeOutQuart``
*`'easeInOutQuart'`
*`'easeInQuint``
*``easeOutQuint``
*``easeInOutQuint``
*`'easeInSine'`
*“easeOutSine”
*“easeInOutSine”
*“easeInExpo”
*“easeOutExpo”
*`'easeInOutExpo'`
*`'easeInCirc'`
*`'easeOutCirc'`
*`'easeInOutCirc'`
*“easyInElastic”
*“easeOutElastic”
*“easeInOutElastic”
*“easeInBack”
*“easeOutBack”
*`'easeInOutBack'`
*“easeInBounce”
*``easeOutBounce``
*`'easeInOutBounce'`

参见[Robert Penner的宽松方程式]（http://robertpenner.com/easing/）。

##动画回调

`onProgress`和`onComplete`回调对于将外部绘制同步到图表动画是非常有用的。回调传递一个`Chart.Animation`实例：

```javascript
{
    //图表对象
    图：图表，

    //当前动画帧号
    currentStep：Number，

    //动画帧数
    numSteps：数字，

    //动画轻松使用
    宽松：字符串，

    //渲染图表的函数
    渲染：功能，

    //用户回调
    onAnimationProgress：功能，

    //用户回调
    onAnimationComplete：功能
}
```

以下示例在图表动画期间填充进度条。
```javascript
var chart = new Chart（ctx，{
    输入：'line'，
    数据：数据，
    选项：{
        动画： {
            onProgress：function（animation）{
                progress.value = animation.animationObject.currentStep / animation.animationObject.numSteps;
            }
        }
    }
}）;
```

这些回调的另一个例子可以在[Github]（https://github.com/chartjs/Chart.js/blob/master/samples/animation/progress-bar.html）中找到：该示例显示一个进度条，显示动画有多远。
