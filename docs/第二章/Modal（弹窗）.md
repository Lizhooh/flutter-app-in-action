
## Modal（弹窗）
Flutter 没有提供专用的弹窗容器组件，但是我们在实际开发时会经常用到一些全屏的弹窗效果。

在 Flutter 里提供了 `showModalBottomSheet`，`showDialog`，`Overlay` 这些弹出方法。

### showModalBottomSheet
showModalBottomSheet 是具有底部滑出的弹窗方法，可以通过自定义其 builder 实现内容的布局。

```js
onPressed: () {
  showModalBottomSheet(
    context: context,
    builder: (BuildContext context) {
      return Column(
        mainAxisSize: MainAxisSize.min,
        children: <Widget>[
          Text('abc'),
          Text('abc'),
        ],
      );
    }
  );
},
```

### showDialog
showDialog 是从中间弹出的弹窗方法，可以通过自定义其 builder 实现内容的布局。

```js
showDialog(
  context: context,
  builder: (BuildContext context) {
    return Column(
      mainAxisSize: MainAxisSize.min,
      children: <Widget>[
        Text('abc'),
        Text('abc'),
      ],
    );
  },
);
```

### Overlay
Overlay 的用法比较奇妙，Overlay 这个组件提供了动态的在 Flutter 的渲染树上插入布局的特性，因此可以利用 Overlay 实现 Modal 的效果。

使用 Overlay 创建的内容会覆盖当前页面的内容，也就是在最顶层哦，Overlay 的使用方法如下：

```js
// 创建一个 OverlayState，需要 context 哦
var overlayState = Overlay.of(context);

// 创建一个 overlayEntry
var overlayEntry = new OverlayEntry(
  builder: (BuildContext context) {
    // 这里就是放置弹窗的内容
    return (
        // ...
    );
  }
);

// 将 overlayEntry 插入到 root 的节点下
overlayState.insert(overlayEntry);

// 在关闭的时候，删除即可
overlayEntry?.remove();
```