

## Drawer（抽屉菜单）
Drawer（抽屉菜单）即通过右侧/左侧滑出来的菜单栏。在 Flutter 里使用的是 [Drawer](https://docs.flutter.io/flutter/material/Drawer-class.html) 组件。

![](/../../image/20180629113531.png)

使用的方式是在 Scaffold 里的 drawer 属性设置。

```js
var imgUrl = 'https://img.zcool.cn/community/0167c05901528c' +
             'a8012145505a6888.jpg@1280w_1l_2o_100sh.jpg';

@override
Widget build(BuildContext context) {
    return new Scaffold(
        appBar: (),
        body: (),
        drawer: new Drawer(
            child: new Container(
                color: const Color(0xfff1f2f3),

                child: new Column(
                    children: <Widget>[
                        new Image.network(this.imgUrl),

                        new Container(
                            padding: new EdgeInsets.all(20.0),
                            child: new Row(
                                children: <Widget>[
                                    new Icon(Icons.home, color: Colors.black87),
                                    new Text('首页'),
                                ],
                            ),
                        )
                    ],
                ),
            ),
        )
    );
}
```

![](/../../image/20180628233507.png)

Drawer 常用属性：
- **child → Widget** - Drawer 内容。
- **elevation → double** - Drawer 阴影效果大小。
- **semanticLabel → String** - Drawer 关闭/打开时的通知信息。

有时候先通过点击 Drawer 里的元素从而关闭 Drawer，那么如何实现？使用 Navigator.pop 可以关闭 Drawer。

```js
new MaterialButton(
    color: Colors.blue,
    textColor: Colors.white,
    child: new Text('点我'),
    onPressed: () {
        Navigator.pop(context);
        // Or Navigator.of(context).pop();
    },
),
```

### 菜单项
菜单项可以自己定义也可以使用 `ListTile` 和 `Divider` 来实现。

```js
new ListTile(
    title: new Text('说话心理学'),
    trailing: new Icon(Icons.chevron_right),
),
new Divider(),
new ListTile(
    title: new Text('从众心理学'),
    trailing: new Icon(Icons.chevron_right),
),
```

![](/../../image/20180629125235.png)
