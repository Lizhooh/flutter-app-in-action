
## BottomSheet（底部滑出）
[BottomSheet](https://docs.flutter.io/flutter/material/BottomSheet-class.html) 是一个底部滑出的组件。

![](/../../image/20180701103412.png)

```js
new BottomSheet(
    onClosing: () {},
    builder: (BuildContext context) {
        return new Text('aaa');
    },
),
```

通常很少直接使用 BottomSheet 而是使用 [showModalBottomSheet](https://docs.flutter.io/flutter/material/showModalBottomSheet.html)。直接时候的时候看到的知识 builder 里的内容。

```js
Future<T> showModalBottomSheet <T>({
    @required BuildContext context,
    @required WidgetBuilder builder
});
```

看一个示例。

```js
new MaterialButton(
    color: Colors.blue,
    child: new Text('点我'),
    onPressed: () {
        showModalBottomSheet(
            context: context,
            builder: (BuildContext context) {
                return new Container(
                    height: 300.0,
                    child: new Image.network(this.imgurl),
                );
            },
        ).then((val) {
            print(val);
        });
    },
),
```

![](/../../image/20180701104224.png)

在 builder 是可以自定义任何界面内容的，海纳百川。