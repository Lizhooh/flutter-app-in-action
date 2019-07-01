
## Button（按钮）
在 Flutter 里有很多的 Button，包括了：MaterialButton、RaisedButton、FloatingActionButton、FlatButton、IconButton、ButtonBar、DropdownButton 等。

一般常用的 Button 是 MaterialButton、IconButton、FloatingActionButton。

![no-shadow](/../../image/20180629215518.png)

### MaterialButton
[MaterialButton](https://docs.flutter.io/flutter/material/MaterialButton-class.html) 是一个 Materia 风格的按钮，特点是默认有背景，有阴影效果。

```js
new MaterialButton(
  color: Colors.blue,
  textColor: Colors.white,
  child: Text('点我'),
  onPressed: () {
      // ...
  },
)
```

![no-shadow](/../../image/20180629220313.png)

一般来说，如果需要点击事件，就要嵌套一个 Button，因为 Container、Text 等组件都没有点击事件。

### RaisedButton
RaisedButton 与 MaterialButton 类似，但是矩阵的。

```js
new RaisedButton(
  child: Text('点我'),
  onPressed: () {},
)
```

### FlatButton
FlatButton 与 MaterialButton 类似，不同的是它是透明背景的。如果一个 Container 想要点击事件时，可以使用 FlatButton 包裹，而不是 MaterialButton。因为 MaterialButton 默认带背景且有阴影，而 FlatButton 默认不带背景。

```js
new FlatButton(
  child: Text('点我'),
  onPressed: () {},
)
```

### IconButton
[IconButton](https://docs.flutter.io/flutter/material/IconButton-class.html) 顾名思义就是 Icon + Button 的复合体，当某个 Icon 需要点击事件时，使用 IconButton 最好不过。

```js
new IconButton(
  icon: Icon(Icons.volume_up),
  tooltip: 'Increase volume by 10%',
  onPressed: () {
      // ...
  },
)
```

其外，还有已经定义好的 Icon Button：CloseButton、BackButton。他们都有导航返回的能力。


### FloatingActionButton
[FloatingActionButton](https://docs.flutter.io/flutter/material/FloatingActionButton-class.html) 是一个浮动在页面右下角的浮动按钮。

```js
new Scaffold(
  // ...
  floatingActionButton: FloatingActionButton(
    onPressed: () {},
    child: Icon(Icons.add_a_photo),
    elevation: 3.0,
    highlightElevation: 2.0,
    backgroundColor: Colors.red,        // 红色
  ),
)
```

在 Scaffold 里使用的时候，它是一个浮动状态的按钮，在其他地方使用，就不会浮动了。

![](/../../image/20180629222404.png)


### ButtonBar
ButtonBar 是一个布局组件，可以让 Button 排列在一行。

```js
new ButtonBar(
  children: <Widget>[
    CloseButton(),
    BackButton(),
  ],
)
```

## InkWell
InkWell 应该不算是按钮吧，都是它能提供的就是 `水波效果`，可以作为容器包裹一切想点击时有水波效果的组件。

```js
InkWell(
  onTap: () { },
  child: Container(
      height: 50,
      child: Text('点我'),
  ),
)
```
