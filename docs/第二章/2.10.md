

## Checkbox（复选框）
[Checkbox](https://docs.flutter.io/flutter/material/Checkbox-class.html) 是一个复选框组件，通常用于设置的选项里。

![no-shadow](/../../image/20180630212157.png)

```js
new Checkbox(
    value: this.check,
    activeColor: Colors.blue,
    onChanged: (bool val) {
        // val 是布尔值
        this.setState(() {
            this.check = !this.check;
        });
    },
),
```

Checkbox 有以下常用属性：
- **activeColor → Color** - 激活时的颜色。
- **onChanged → ValueChanged<bool>** - 改变时触发。
- **tristate → bool** - 如果为 true，那么复选框的值可以是 true，false 或 null。
- **value → bool** - 复选框的值。


### CheckboxListTile
CheckboxListTile 是一个 Checkbox 的上层封装，它的外观是提供类似设置页的选择组件，可设置图标和文字。

```js
new CheckboxListTile(
    secondary: const Icon(Icons.shutter_speed),
    title: const Text('硬件加速'),
    value: this.check,
    onChanged: (bool value) {
        setState(() {
            this.check = !this.check;
        });
    },
),
```

![no-shadow](/../../image/20180630223301.gif)
