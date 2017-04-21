# 交互方式
通过悬停或工具提示配置与图形的交互时，可以使用多种不同的模式。

这些模式将在下面详细说明，以及它们与`intersect`设置的结合方式。
 

## 点
查找与点相交的所有项目

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'point'
        }
    }
})
```

## 最近的
获取最接近点的项目。 最近的项目是根据与图表项目中心的距离（点,长条）确定的。 如果2个以上的物品距离相同，则使用最小面积的物品。 如果`intersect`为`true`，则仅当鼠标位置与图形中的项目相交时才会触发。 这对于组合图非常有用，其中点隐藏在条形图的某一个长条后面。
 

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'nearest'
        }
    }
})
```

## single (deprecated)
找到与点相交并返回的第一个项。 行为像`最近`模式，`intersect = true`。

## label (deprecated)
See `'index'` mode

## index
查找相同索引项。 如果`intersect`设置为`true`，则第一个相交项用于确定数据中的索引。 如果`intersect`设置为`false`，则使用最近的项来确定索引。
 

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'index'
        }
    }
})
```

## x-axis (deprecated)
像`'index'`模式一样，`intersect = false`。
 
##  数据集
查找同一数据集中的项目。 如果`intersect`设置为`true`，则第一个相交项用于确定数据中的索引。 如果`intersect`为`false`，则使用最近的项来确定索引。


```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'dataset'
        }
    }
})
```

## x
根据位置的`X`坐标返回所有相交的项目。 对于垂直游标实现将是有用的。 请注意，这仅适用于笛卡尔图表
 

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'x'
        }
    }
})
```

## y
返回基于位置的`Y`坐标相交的所有项目。 这对于水平光标实现将是有用的。 请注意，这仅适用于笛卡尔图表。
 

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'y'
        }
    }
})
```