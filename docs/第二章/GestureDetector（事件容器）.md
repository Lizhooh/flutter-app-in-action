
## GestureDetector（事件容器）
在 Flutter 里点击是通过 Button 触发的，但是有时候并不是点击按钮这么简单，可能是点击图片或 Icon，虽然有 Container 容器组件，但是 Container 并不提供 onTab 事件，因此想要有点击事件，就得包裹一个 GestureDetector（事件容器）。

下面的代码，将 GestureDetector 包裹 Image，因此点击 Image 时能够触发 onTab 事件。

```js
appBar: AppBar(
  elevation: 0,
  leading: GestureDetector(
    onTap: back,
    child: Image.asset('images/icon_arrow_back_black.png'),
  ),
),
```

