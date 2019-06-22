
## Widget 框架
Flutter Widget 采用现代响应式框架构建，这是从 React 中获得的灵感，中心思想是用 Widget 构建 UI。

在 Flutter 里一切的组件都是一个 **Widget**，当 Widget 的状态发生变化时，Widget 会重新构建 UI，Flutter 会对比前后变化的不同， 以确定底层渲染树从一个状态转换到下一个状态所需的最小更改。这种概念非常类似于 React 中的 VDOM 以及 Diff 算法，的确 Flutter 是从中借鉴的。同时 Flutter 的数据流也是单向绑定的。

![no-shadow](/../../image/20180627095752.jpg)


```js
class App extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return new Center(
            child: new Text('Hello, world!'),
        );
    }
}
```

在整个应用的初始化，只需要把 Widget 传给 runApp 即可。

```js
import 'package:flutter/material.dart';

void main() {
    runApp(new App());
}
```

### 生命周期
在 `StatefulWidget` 调用 createState 之后，框架将新的状态对象插入树中，然后调用状态对象的 initState。 子类化 State 可以重写initState，以完成仅需要执行一次的工作。 例如，您可以重写 initState 以配置动画或订阅 platform services。initState 的实现中需要调用 super.initState。

当一个状态对象不再需要时，框架调用状态对象的 dispose。 您可以覆盖该 dispose 方法来执行清理工作。例如，您可以覆盖 dispose 取消定时器或取消订阅 platform services。dispose 典型的实现是直接调用 super.dispose。

![no-shadow](/../../image/20180629115839.png)


```js
import 'package:flutter/material.dart';

class LifecycleAppPage extends StatefulWidget {
    @override
    State<StatefulWidget> createState() {
        return new _LifecycleAppPageState('构造函数');
    }
}

class _LifecycleAppPageState extends State<LifecycleAppPage> with WidgetsBindingObserver {
    String str;

    int count = 0;

    _LifecycleAppPageState(this.str);

    @override
    void initState() {
        print(str);
        print('initState');
        super.initState();
        WidgetsBinding.instance.addObserver(this);
    }

    @override
    void didChangeDependencies() {
        print('didChangeDependencies');
        super.didChangeDependencies();
    }

    @override
    void didUpdateWidget(LifecycleAppPage oldWidget) {
        print('didUpdateWidget');
        super.didUpdateWidget(oldWidget);
    }

    @override
    void deactivate() {
        print('deactivate');
        super.deactivate();
    }

    @override
    void dispose() {
        print('dispose');
        WidgetsBinding.instance.removeObserver(this);
        super.dispose();
    }

    @override
    void didChangeAppLifecycleState(AppLifecycleState state) {
        switch (state) {
        case AppLifecycleState.inactive:
            print('AppLifecycleState.inactive');
            break;
        case AppLifecycleState.paused:
            print('AppLifecycleState.paused');
            break;
        case AppLifecycleState.resumed:
            print('AppLifecycleState.resumed');
            break;
        case AppLifecycleState.suspending:
            print('AppLifecycleState.suspending');
            break;
        }

        super.didChangeAppLifecycleState(state);
    }

    @override
    Widget build(BuildContext context) {
        print('build');
        return new Scaffold(
        appBar: new AppBar(
            title: new Text('学习'),
            centerTitle: true,
        ),
        body: new OrientationBuilder(
            builder: (context, orientation) {
            return new Center(
                child: new Text(
                '当前计数值：$count',
                style: new TextStyle(
                    color: orientation == Orientation.portrait
                        ? Colors.blue
                        : Colors.red),
                ),
            );
            },
        ),
        floatingActionButton: new FloatingActionButton(
            child: new Text('click'),
            onPressed: () {
                setState(() {
                    count++;
                });
            }),
        );
    }
}

class LifecyclePage extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return new Scaffold(
            body: new LifecycleAppPage(),
        );
    }
}
```

![no-shadow](/../../image/20190622182637.png)