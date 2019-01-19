
## Icon（图标）
[Icon](https://docs.flutter.io/flutter/widgets/Icon-class.html) 是 Flutter 的图标类，它集成了 [Material 风格的图标](https://material.io/icons/)。它有几个衍生的组件：ImageIcon、IconButton 等。

```js
new Icon(
    Icons.add_a_photo,
    size: 20.0,
    color: const Color.fromRGBO(255, 0, 0, 0.7),,
),
```

![](/../../image/20180629222404.png)

如果不清楚图标的名称，可以去这个网站查阅：https://material.io/icons/

通常样什么一个变量是 Icon 时，需要使用 IconData 来声明。

```js
var MyIcon(IconData icon) {
    return new Icon(icon);
}

MyIcon(Icons.add_a_photo);
```