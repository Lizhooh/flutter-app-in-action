
## Form（表单）
对于文本输入，可以使用 TextField。如果想清除一组 TextfFiled 的内容，一个个清除也很麻烦。所以，Flutter 提供了一个 Form widget，可以对输入框进行分组，然后进行一些统一的操作。

```js
Form(
  key: GlobalKey<FormState>(),
  onChange: () {

  },
  child: null,
);
```

### 回退时弹窗
有时候想实现，点击导航回退时提示警告 xxx，这时可以使用 From 的 onWillPop 实现。

```js
Form(
  onWillPop: onBackPressed,
  key: GlobalKey<FormState>(),
);

onBackPressed = (e) {
  // ...
}
```