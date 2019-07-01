
## Radio（单选框）
[Radio](https://docs.flutter.io/flutter/material/Radio-class.html) 是一个复选框组件，通常用于设置的选项里。

![no-shadow](/../../image/20180630213144.png)

```js
Radio(
  groupValue: this.radio,
  activeColor: Colors.blue,
  value: 'aaa',
  onChanged: (String val) {
    // val 与 value 的类型对应
    this.setState(() {
      this.radio = val;  // aaa
    });
  },
),
```

这里的 value 是当前 Radio 的值，groupValue 是组的值，如果 groupValue == value 则 Radio 被选中。

Radio 有以下常用属性：
- **activeColor → Color** - 激活时的颜色。
- **groupValue → T** - 选择组的值。
- **onChanged → ValueChanged<T>** - 改变时触发。
- **value → T** - 单选的值。
