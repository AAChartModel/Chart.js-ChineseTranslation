# Chart.js

[！[Chart.js on Slack](https://img.shields.io/badge/slack-Chart.js-blue.svg)](https://chart-js-automation.herokuapp.com/)

## 安装

您可以从[GitHub版本](https://github.com/chartjs/Chart.js/releases/latest) 下载最新版本的`Chart.js`，或使用 [Chart.js CDN](https：// cdnjs .com / libraries / Chart.js) 。详细的安装说明可以在[安装](./getting-started / installation.md)页面找到。

## 创建图表

很容易开始使用`Chart.js`。所需要的是脚本包含在您的页面中以及单个`<canvas>`节点来呈现图表。

在此示例中，我们为单个数据集创建条形图，并在我们的页面中呈现。您可以在[使用文档](./getting-started/usage.md) 中查看使用`Chart.js`的所有方法

```html
<canvas id =“myChart”width =“400”height =“400”> </ canvas>
<script>
var ctx = document.getElementById（“myChart”）。getContext（'2d'）;
var myChart = new Chart（ctx，{
    键入：'bar'，
    资料：{
        标签：[“红色”，“蓝色”，“黄色”，“绿色”，“紫色”，“橙色”]，
        数据集：[{
            标签：'＃of Votes'，
            数据：[12，19，3，5，2，3]
            背景颜色： [
                'rgba（255，99，132，0.2）'，
                'rgba（54，162，235，0.2）'，
                'rgba（255，206，86，0.2）'，
                'rgba（75，192，192，0.2）'，
                'rgba（153，102，255，0.2）'，
                'rgba（255，159，64，0.2）'
            ]，
            borderColor：[
                'rgba（255,99,132,1）'，
                'rgba（54，162，235，1）'，
                'rgba（255，206，86，1）'，
                'rgba（75，192，192，1）'，
                'rgba（153，102，255，1）'，
                'rgba（255，159，64，1）'
            ]，
            borderWidth：1
        }]
    }，
    选项：{
        比例：{
            yAxes：[{
                滴答：{
                    beginAtZero：true
                }
            }]
        }
    }
}）;
</ script>
```

## 贡献

在向项目提交问题或提出请求之前，请先点击[贡献指南](https://github.com/chartjs/Chart.js/blob/master/CONTRIBUTING.md)。

对于使用Chart.js的支持，请使用Stack Overflow上的[`chartjs`标签](http://stackoverflow.com/questions/tagged/chartjs)发布问题。

## 执照

Chart.js可以在[MIT许可证](http://opensource.org/licenses/MIT)下找到。
