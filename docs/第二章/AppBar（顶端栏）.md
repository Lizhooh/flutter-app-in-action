
## AppBar（顶端栏）
[AppBar](https://docs.flutter.io/flutter/material/AppBar-class.html) 是一个顶端栏，对应着 Android 的 Toolbar。

![no-shadow](/../../image/20180629155102.png)

AppBar 有以下常用属性：
- **leading → Widget** - 在标题前面显示的一个控件，在首页通常显示应用的 logo；在其他界面通常显示为返回按钮。
- **title → Widget** -  Toolbar 中主要内容，通常显示为当前界面的标题文字。
- **actions → List<Widget>** - 一个 Widget 列表，代表 Toolbar 中所显示的菜单，对于常用的菜单，通常使用 IconButton 来表示；对于不常用的菜单通常使用 PopupMenuButton 来显示为三个点，点击后弹出二级菜单。
- **bottom → PreferredSizeWidget** - 一个 AppBarBottomWidget 对象，通常是 TabBar。用来在 Toolbar 标题下面显示一个 Tab 导航栏。
- **elevation → double** - 控件的 z 坐标顺序，默认值为 4，对于可滚动的 SliverAppBar，当 SliverAppBar 和内容同级的时候，该值为 0， 当内容滚动 SliverAppBar 变为 Toolbar 的时候，修改 elevation 的值。
- **flexibleSpace → Widget** - 一个显示在 AppBar 下方的控件，高度和 AppBar 高度一样，可以实现一些特殊的效果，该属性通常在 SliverAppBar 中使用。
- **backgroundColor → Color** - Appbar 的颜色，默认值为 ThemeData.primaryColor。改值通常和下面的三个属性一起使用。
- **brightness → Brightness** - Appbar 的亮度，有白色和黑色两种主题，默认值为 ThemeData.primaryColorBrightness。
- **iconTheme → IconThemeData** - Appbar 上图标的颜色、透明度、和尺寸信息。默认值为 ThemeData.primaryIconTheme。
- **textTheme → TextTheme** -  Appbar 上的文字样式。
- **centerTitle → bool** -  标题是否居中显示，默认值根据不同的操作系统，显示方式不一样。
- **toolbarOpacity → double**

![](/../../image/20180629154401.png)

```js
// 返回每个隐藏的菜单项
SelectView(IconData icon, String text, String id) {
    return new PopupMenuItem<String>(
        value: id,
        child: new Row(
            mainAxisAlignment: MainAxisAlignment.spaceEvenly,
            children: <Widget>[
                new Icon(icon, color: Colors.blue),
                new Text(text),
            ],
        )
    );
}

appBar: new AppBar(
    title: new Text('首页'),
    leading: new Icon(Icons.home),
    backgroundColor: Colors.blue,
    centerTitle: true,
    actions: <Widget>[
        // 非隐藏的菜单
        new IconButton(
            icon: new Icon(Icons.add_alarm),
            tooltip: 'Add Alarm',
            onPressed: () {}
        ),
        // 隐藏的菜单
        new PopupMenuButton<String>(
            itemBuilder: (BuildContext context) => <PopupMenuItem<String>>[
                this.SelectView(Icons.message, '发起群聊', 'A'),
                this.SelectView(Icons.group_add, '添加服务', 'B'),
                this.SelectView(Icons.cast_connected, '扫一扫码', 'C'),
            ],
            onSelected: (String action) {
                // 点击选项的时候
                switch (action) {
                    case 'A': break;
                    case 'B': break;
                    case 'C': break;
                }
            },
        ),
    ],
),
```

![](/../../image/20180629154709.png)


### showMenu 指定位置
PopupMenu 默认的弹框位置都是在右上角，且会挡住标题栏，如果有需要在其他位置弹框就需要借助 showMenu，主要通过 position 属性定位弹框位置。

```js
onTap: () async {
  final result = await showMenu(
    context: context,
    position: RelativeRect.fromLTRB(100.0, 200.0, 100.0, 100.0),
    items: <PopupMenuItem<String>>[
      new PopupMenuItem<String>( value: 'value01', child: new Text('Item One')),
      new PopupMenuItem<String>( value: 'value02', child: new Text('Item Two')),
      new PopupMenuItem<String>( value: 'value03', child: new Text('Item Three')),
      new PopupMenuItem<String>( value: 'value04', child: new Text('I am Item Four'))
    ] );
},
```

![](/../../image/20190119174105.png)
