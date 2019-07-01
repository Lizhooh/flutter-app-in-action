
## DatePicker（日期）
[DatePicker](https://docs.flutter.io/flutter/material/showDatePicker.html) 是一个日期组件，提供时间和日期的选择。

在 Flutter 里没有对应的组件，而是提供两个函数：showDatePicker() 和 showTimePicker()。

```js
Future<DateTime> showDatePicker ({
  @required BuildContext context, // 上下文
  @required DateTime initialDate, // 初始日期
  @required DateTime firstDate,   // 日期范围，开始
  @required DateTime lastDate,    // 日期范围，结尾
  SelectableDayPredicate selectableDayPredicate,
  DatePickerMode initialDatePickerMode: DatePickerMode.day,
  Locale locale,                  // 国际化
  TextDirection textDirection,
});

Future<TimeOfDay> showTimePicker({
  @required BuildContext context,
  @required TimeOfDay initialTime,
});
```

![](/../../image/20180630231135.png)

```js
new MaterialButton(
  child: Text('选择日期'),
  onPressed: () {
    // 调用函数打开
    showDatePicker(
      context: context,
      initialDate: DateTime.now(),
      firstDate: DateTime.now().subtract(Duration(days: 30)), // 减 30 天
      lastDate: DateTime.now().add(Duration(days: 30)),       // 加 30 天
    ).then((DateTime val) {
      print(val);   // 2018-07-12 00:00:00.000
    }).catchError((err) {
      print(err);
    });
  },
),
```

![](/../../image/20180630232440.png)

showDatePicker 打开的面板样式是系统自带的，在不同版本的 Android 上会有不同的体现，在比较低版本的 Android 上，样式比较难看，6.0 以上会好一点。


```js
new MaterialButton(
  child: Text('选择时间'),
  onPressed: () {
    showTimePicker(
      context: context,
      initialTime: TimeOfDay.now(),
    ).then((val) {
      print(val);
    }).catchError((err) {
      print(err);
    });
  },
)
```

showTimePicker 打开的面板样式是系统自带的，在不同版本的 Android 上会有不同的体现，在比较低版本的 Android 上，样式比较难看，6.0 以上会好一点。


![](/../../image/20180630234031.png)


注意了，DatePicker 默认是英文说明的，就算手机设置为中文。如果需要是中文说明，则需要自己做 **国际化** 处理。

国际化处理请看 **<span style="color: #f45">第三章 · 进阶篇 - 国际化</span>**。