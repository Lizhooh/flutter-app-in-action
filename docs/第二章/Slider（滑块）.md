
## Slider（滑块）
[Slider](https://docs.flutter.io/flutter/material/Slider-class.html) 是一个滑块组件，可用于数量的选择。

![](/../../image/20180630225727.png)

```js
new Slider(
    value: this.slider,
    max: 100.0,
    min: 0.0,
    activeColor: Colors.blue,
    onChanged: (double val) {
        this.setState(() {
            this.slider = val;
        });
    },
),
```

Slider 各部分的术语是：
- thumb - 用户拖动时水平滑动的形状。
- track - 滑块拇指滑过的线。
- value - 当用户拖动拇指指示所选值时弹出的形状。
- active - 滑块的“活动”一侧是拇指和最小值之间的一侧。
- inactive - 滑块的“非活动”侧是拇指和最大值之间的一侧。

Slider 有以下常用属性：
- **activeColor → Color** - 激活时的颜色。
- **divisions → int** - 离散部门的数量。
- **inactiveColor → Color** - 滑块轨道的非活动部分的颜色。
- **label → String** 滑块处于活动状态时显示在滑块上方的标签。
- **max → double** - 用户可以选择的最大值。
- **min → double** - 用户可以选择的最小值。
- **onChanged → ValueChanged<double>** - 改变时触发。
- **onChangeEnd → ValueChanged<double>** -  改变后触发。
- **onChangeStart → ValueChanged<double>** - 改变前触发。
- **value → double** - 滑块的值。
