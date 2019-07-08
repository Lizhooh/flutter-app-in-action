
## GridView（网格）
[GridView](https://docs.flutter.io/flutter/widgets/GridView-class.html) 是一个网格布局的列组件。GridView 继承至 CustomScrollView，有 CustomScrollView 的特性。

通常，我们可以利用 GridView 构建这样的界面。

![](/../../image/20180701174739.png)


```js
String imgsrc = 'http://5b0988e595225.cdn.sohucs.com/images' +
            '/20171218/342e43903694448b91698b5ce7623314.jpeg';

List buildGridTileList(int number) {
  List widgetList = new List();

  for (int i = 0; i < number; i++) {
    widgetList.add(Container(
      decoration: BoxDecoration(
        color: Colors.white,
        image: DecorationImage(
          image: NetworkImage(this.imgsrc),
          fit: BoxFit.cover,
        ),
        shape: BoxShape.circle,
        boxShadow: <BoxShadow>[
          BoxShadow(
              offset: Offset(0.0, 1.0),
              blurRadius: 2.0,
              color: const Color(0xffaaaaaa),
          ),
        ],
      ),
    ));
  }
  return widgetList;
}

// GridView 默认滚动方向是垂直的。
new GridView.count(
  padding: const EdgeInsets.all(8.0),
  primary: false,
  crossAxisCount: 3,                  // 横向 Item 的个数
  mainAxisSpacing: 12.0,              // 竖向间距
  crossAxisSpacing: 12.0,             // 横向间距
  childAspectRatio: 1,                // 长比宽比例
  children: buildGridTileList(15),
),
```

![](/../../image/20180701174020.png)

如果不想用 GridView.count 可以使用设置 gridDelegate。

```js
GridView(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 3,                  // 横向 Item 的个数
    mainAxisSpacing: 12.0,              // 竖向间距
    crossAxisSpacing: 12.0,             // 横向间距
    childAspectRatio: 1,                // 长比宽比例
  ),
  children: [
    Text('a'),
    Text('a'),
    Text('a'),
    Text('a'),
    Text('a'),
    Text('a'),
  ],
),
```

吐槽一下，google 的命名真的是全拼啊，这么长的命名。

