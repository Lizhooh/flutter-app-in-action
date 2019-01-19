
## Switch（切换）
[Switch](https://docs.flutter.io/flutter/material/Switch-class.html) 是一个切换按钮组件，通常用于设置的选项里。Switch 的原点颜色，横条颜色都可以设置，此外原点可以以图片形式显示。

![no-shadow](/../../image/20180630214538.png)

```js
new Switch(
    value: this.check,
    activeColor: Colors.blue,     // 激活时原点颜色
    onChanged: (bool val) {
        this.setState(() {
            this.check = !this.check;
        });
    },
)
```

Switch 有以下常用属性：
- **activeColor → Color** - 激活时原点的颜色。
- **activeThumbImage → ImageProvider** - 原点还支持图片，激活时的效果。
- **activeTrackColor → Color** - 激活时横条的颜色。
- **inactiveThumbColor → Color** - 非激活时原点的颜色。
- **inactiveThumbImage → ImageProvider** - 非激活原点的图片效果。
- **inactiveTrackColor → Color** - 非激活时横条的颜色。
- **onChanged → ValueChanged<bool>** - 改变时触发。
- **value → bool** - 切换按钮的值。
