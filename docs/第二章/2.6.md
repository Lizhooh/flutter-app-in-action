
## TextField（文本输入）
[TextField](https://docs.flutter.io/flutter/material/TextField-class.html) 是一个文本输入组件，类似 Web 上的 Input。

![](/../../image/20180629165318.png)

```js
new TextField(
    decoration: const InputDecoration(
        hintText: '帐号/邮箱',
        contentPadding: const EdgeInsets.all(10.0),
    ),
    // 当 value 改变的时候，触发
    onChanged: (val) {
        print(val);
    }
),
```

TextField 有以下常用属性：
- **autocorrect → bool** - 是否启用自动更正。
- **autofocus → bool** - 是否是自动获取焦点。
- **controller → TextEditingController** - 控制正在编辑的文本。
- **decoration → InputDecoration** - TextField 的外形描述。
- **enabled → bool** - 是否禁用。
- **focusNode → FocusNode** - 是否具有键盘焦点。
- **inputFormatters → List<TextInputFormatter>** - 可选的，输入验证和格式化。
- **keyboardType → TextInputType** - 用于编辑文本的键盘类型。
- **maxLength → int** - 文本最大的字符串长度。
- **maxLengthEnforced → bool** - 如果为true，则防止字段允许超过 maxLength 字符。
- **maxLines → int** - 文本最大行数，默认为 1。多行时应该设置为  > 1。
- **obscureText → bool** - 是否是隐藏文本（密码形式）。
- **onChanged → ValueChanged<String>** - 当 value 改变时触发。
- **onSubmitted → ValueChanged<String>** - 当用户点击键盘的提交时触发。
- **style → TextStyle** - 文本样式，颜色，字体等。
- **textAlign → TextAlign** - 设置文本对齐方式。


![](/../../image/20180629171046.png)

### 双向数据绑定
通常需要把 TextField 的数据绑定到组件的状态里，那么在 Flutter 里如何实现呢？那就是使用 controller。

```js
new TextField(
    controller: new TextEditingController(text: this.id),
    decoration: const InputDecoration(
        hintText: '帐号/邮箱',
        contentPadding: const EdgeInsets.all(10.0),
    ),
    onChanged: (val) {
        this.setState(() {
            this.id = val;
        });
    },
),
```

