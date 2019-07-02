
## Dialog（弹出框）
在 Flutter 里有大大小小的弹出框，例如：AlertDialog、SimpleDialog 等。

![](/../../image/20180701105346.png)

对于弹出框这些都不会直接使用它的组件，而是使用对应的调用函数（showDialog）。



### AlertDialog
AlertDialog 是一个用于向用户传递信息的弹出层。

```js
new MaterialButton(
  color: Colors.blue,
  child: Text('点我'),
  onPressed: () {
    showDialog<Null>(
      context: context,
      barrierDismissible: false,
      builder: (BuildContext context) {
        return AlertDialog(
          title: Text('标题'),
          content: SingleChildScrollView(
            child: ListBody(
              children: [
                Text('内容 1'),
                Text('内容 2'),
              ],
            ),
          ),
          actions: [
            FlatButton(
              child: Text('确定'),
              onPressed: () {
                Navigator.of(context).pop();
              },
            ),
          ],
        );
      },
    ).then((val) {
      print(val);
    });
  },
),
```

![](/../../image/20180701110715.png)


### SimpleDialog
SimpleDialog 是一个用于向用户传递确定信息并提供选项的弹出层。

```js
new MaterialButton(
  color: Colors.blue,
  child: Text('点我'),
  onPressed: () {
    showDialog<Null>(
      context: context,
      builder: (BuildContext context) {
        return SimpleDialog(
          title: Text('选择'),
          children: [
            SimpleDialogOption(
              child: Text('选项 1'),
              onPressed: () {
                Navigator.of(context).pop();
              },
            ),
            SimpleDialogOption(
              child: Text('选项 2'),
              onPressed: () {
                Navigator.of(context).pop();
              },
            ),
          ],
        );
      },
    ).then((val) {
      print(val);
    });
  },
),
```

![](/../../image/20180701111845.png)