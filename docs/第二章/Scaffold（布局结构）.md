
## Scaffold（布局结构）
Scaffold 实现了基本的 Material Design 布局结构。在 Material 设计中定义的单个界面上的各种布局元素，在 Scaffold 中都支持。

Scaffold 有下面几个主要属性：
- **appBar** - 显示在界面顶部的一个 AppBar。
- **body** - 当前界面所显示的主要内容 Widget。
- **floatingActionButton** - Material 设计中所定义的 FAB，界面的主要功能按钮。
- **persistentFooterButtons** - 固定在下方显示的按钮，比如对话框下方的确定、取消按钮。
- **drawer** - 抽屉菜单控件。
- **backgroundColor** - 内容的背景颜色，默认使用的是 ThemeData.scaffoldBackgroundColor 的值。
- **bottomNavigationBar** -  显示在页面底部的导航栏。
- **resizeToAvoidBottomPadding** - 类似于 Android 中的 android:windowSoftInputMode='adjustResize'，控制界面内容 body 是否重新布局来避免底部被覆盖了，比如当键盘显示的时候，重新布局避免被键盘盖住内容。默认值为 true。

```js
@override
Widget build(BuildContext context) {
    return new Scaffold(
        appBar: new AppBar(
            title: new Text('应用'),
        ),
        body: new Center(
            child: new Text('Hello'),
        ),
    );
}
```