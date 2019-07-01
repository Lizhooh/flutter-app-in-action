
## PageView（滑动视图）
[PageView](https://docs.flutter.io/flutter/widgets/PageView-class.html) 是一个滑动视图列表，它也是继承至 CustomScrollView 的。

在 PageView 里有三个构造函数：
- PageView - 创建一个可滚动列表。
- PageView.builder - 创建一个滚动列表，指定数量。
- PageView.custom - 创建一个可滚动的列表，自定义子项。

```js
PageView.custom(
  childrenDelegate: SliverChildBuilderDelegate(
    (context, index) {
      return Center(
        child: Text('$index', style: TextStyle(fontSize: 64.0)),
      );
    },
    childCount: 10,
  ),
)
```

![](/../../image/20180701190831.gif)

PageView 有以下常用属性：
- **childrenDelegate → SliverChildDelegate** - 子项列表。
- **controller → PageController** - 控制台。
- **onPageChanged → ValueChanged<int>** - 索引改变时触发。
- **pageSnapping → bool** - 设置为 false 以禁用页面捕捉，对自定义滚动行为很有用。
- **physics → ScrollPhysics** - 页面视图如何响应用户输入，即滚动的动画表现。
- **reverse → bool** - 是否反方向。
- **scrollDirection → Axis** - 视图滚动的方向。
