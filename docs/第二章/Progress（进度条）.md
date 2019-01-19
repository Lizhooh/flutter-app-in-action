
## Progress（进度条）
在 Flutter 使用 LinearProgressIndicator 表示进度条组件。

```js
// 条形进度条
new LinearProgressIndicator(
    backgroundColor: Colors.blue,
    // value: 0.2,
    valueColor: new AlwaysStoppedAnimation<Color>(Colors.red),
),
new Container(padding: const EdgeInsets.all(20.0)),

// 圆形进度条
new CircularProgressIndicator(
    strokeWidth: 4.0,
    backgroundColor: Colors.blue,
    // value: 0.2,
    valueColor: new AlwaysStoppedAnimation<Color>(Colors.red),
),
```

如果 value 为 null 或空，则显示一个动画，否则显示一个定值。Progress 的值只能设置 0 ~ 1.0，如果大于 1，则表示已经结束。

![](/../../image/20180701165408.gif)
