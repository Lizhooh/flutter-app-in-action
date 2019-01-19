
## Container（容器）
[Container](https://docs.flutter.io/flutter/widgets/Container-class.html) 是一个容器组件，在大多数时候，是使用它做一些变形、边距、之类的包裹层。

![](/../../image/20180629113028.png)

```js
new Container(
    width: 200.0,
    height: 200.0,
    margin: const EdgeInsets.all(20.0),
    decoration: new BoxDecoration(
        color: Colors.blue[400],
        borderRadius: new BorderRadius.all(
            const Radius.circular(100.0),
        ),
        boxShadow: <BoxShadow>[
            new BoxShadow(
                spreadRadius: 1.0,
                blurRadius: 5.0,
                offset: const Offset(0.6, 1.2),
                color: Colors.black26,
            )
        ]
    ),
),
```

![no-shadow](/../../image/20180630122101.png)

Container 有以下常用属性：
- **alignment → AlignmentGeometry** - 对子组件（child）的对齐方式。
- **child → Widget** - 子组件。
- **constraints → BoxConstraints** - 对子组件的其他限制条件。
- **decoration → Decoration** - 用于描述子组件。
- **foregroundDecoration → Decoration** - 用于描述子组件前景。
- **margin → EdgeInsetsGeometry** - 外边距。
- **padding → EdgeInsetsGeometry** - 内边距。
- **transform → Matrix4** - 对 Container 的外形进行转换。


### ConstrainedBox
ConstrainedBox 是一个带约束的容器，只有 width，height 的大小约束。

```js
new ConstrainedBox(
    constraints: new BoxConstraints(
        maxHeight: 100.0,
        maxWidth: 100.0,
        minHeight: 50.0,
        minWidth: 50.0
    ),
    child: new Image.network(this.imgsrc),
)
```
