
## ListView（列表）
[ListView](https://docs.flutter.io/flutter/widgets/ListView-class.html) 是最常用的滚条列表，它继承至 CustomScrollView，大多 CustomScrollView 的属性都可用。


使用 ListView 通常会有几个步骤：
- 构建子项内容。
- 构建子项列表。
- 构建 ListView。


构建子项内容和构建子项列表。

```js
var list = ['a', 'b', 'c'];

getList() {
    Iterable<Widget> listTitles = list.map((String item) {
        return new ListTile(
            isThreeLine: true,
            dense: false,
            leading: new CircleAvatar(child: new Text(item)),
            title: new Text('item 的标题'),
            subtitle: new Text('item 的内容'),
            trailing: new Icon(Icons.arrow_right, color: Colors.green),
        );
    });
    return listTitles.toList();
}

```

构建 ListView。

```js
new ListView(
    children: this.getList(),
)
```

![](/../../image/20180701092008.png)


看到这样是因为 ListTile 是一个固定的布局组件。右边是一个头像，左边是信息。

### 自定义子项内容

```js
new ListView(
    children: this.list.map((String item) {
        return new Container(
            padding: const EdgeInsets.all(8.0),
            child: new Row(
                children: <Widget>[
                    new CircleAvatar(
                        backgroundImage: new NetworkImage(this.imgsrc),
                        radius: 30.0,
                    ),
                    new Container(
                        padding: const EdgeInsets.only(left: 8.0),
                        child: new Text('今天吃什么？今天吃什么？今天吃什么？'),
                    ),
                ],
            ),
        );
    }).toList(),
)
```

![](/../../image/20180701093000.png)

因为 ListView 的 children 是一个 Widget 数组，海纳百川，并不一定需要返回相同的格式。


### 使用 builder
使用 builder 可以创建一定数量的列表。

```js
const list = [];
// ...

new ListView.builder(
    itemCount: 40,
    itemBuilder: (BuildContext context, int index) {
        return new Text('子项：' + index.toString());
    }
),
```
