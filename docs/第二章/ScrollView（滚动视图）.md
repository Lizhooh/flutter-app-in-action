
## ScrollView（滚动视图）
[ScrollView](https://docs.flutter.io/flutter/widgets/ScrollView-class.html) 是一个带有滚动的视图组件。

ScrollView 由三部分组成：
- Scrollable - 它监听各种用户手势并实现滚动的交互设计。
- Viewport - 它通过在滚动视图内仅显示一部分小部件来实现滚动的可视化设计。
- Slider - 它们是可以组合以创建各种滚动效果的小部件，如列表，网格和扩展标题。

ScrollView 有以下常用属性：
- **cacheExtent → double** - 视口在可见区域之前和之后有一个区域，用于缓存用户滚动时即将可见的项目。
- **controller → ScrollController** - 一个可用于控制滚动视图滚动到的位置的对象。
- **physics → ScrollPhysics** - 滚动视图应如何响应用户输入。
- **primary → bool** - 是否是与父级关联的主滚动视图。
- **reverse → bool** - 滚动视图是否在阅读方向上滚动。
- **scrollDirection → Axis** - 滚动视图滚动的轴。
- **shrinkWrap → bool** - 应该根据正在查看的内容确定滚动视图的范围。

注：ScrollView 是一个抽象类，通常使用 CustomScrollView。

```js
new CustomScrollView(
    shrinkWrap: true,
    // 内容
    slivers: <Widget>[
        new SliverPadding(
            padding: const EdgeInsets.all(20.0),
            sliver: new SliverList(
                delegate: new SliverChildListDelegate(
                    <Widget>[
                        const Text('A'),
                        const Text('B'),
                        const Text('C'),
                        const Text('D'),
                    ],
                ),
            ),
        ),
    ],
)
```

### SliverAppBar
SliverAppBar 可以实现背景，标题，顶部导航栏联动，渐隐渐出动画。

