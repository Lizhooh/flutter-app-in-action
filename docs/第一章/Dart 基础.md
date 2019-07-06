## Dart 基础
谷歌于 2011 年 10 月 10 日发布了网络编程语言 Dart 的“早期预览版”。谷歌希望利用这款语言，帮助程序开发者克服 JavaScript 语言的缺点。

然而 Typescript 出现之后，Dart 就失去了天然的优势。现在 Flutter 出现，让 Dart 又多了一份生机。

Dart 本身是一个很类似 Typescript 的语言，如果你有 JavaScript/ES6/Typescript 的开发经验，要入门 Dart 只不过是一天的事情。

**目录：**
- [数据类型](#数据类型)
- [函数](#函数)
- [操作符](#操作符)
- [控制流程](#控制流程)
- [类结构](#类结构)
- [泛型](#泛型)
- [模块](#模块)
- [异步编程](#异步编程)
- [JSON 处理](#JSON%20处理)
- [正则表达式](#正则表达式)
- [定时器](#定时器)

## 数据类型
在 Dart 里是强类型的，也有自动推断类型的机制。

在 Dart 里定义变量使用有 var、const、dynamic、Object、类型等方式。对于函数而言，并不需要写 function 关键字，而让它有函数应有的外形即可。


```js
// 导入方式
import 'dart:math';
import 'dart:async';

// 基本类型
var name = 'Voyager I';
var antennaDiameter = 3.7;
const image = {
    'tags': ['Jupiter', 'Saturn', 'Uranus', 'Neptune'],
    'url': '//path/to/saturn.jpg'
};

// 函数类型
String sayHello(var name) {
    return 'Hello $name!';
}

// 箭头函数
var add = (a, b) => a + b;

// 类似 Promise
Future sum(num a, num b) async {
    return await add(a, b);
}

// main 函数
void main() async {
    print(sayHello(name));               // Hello Voyager I!
    print(max(1, 2));                    // 2
    sum(1, 2).then((res) => print(res)); // 3 （类似 Promise）
}

Object name1 = "小明";
dynamic name2 = "老王";
```

dynamic 是任意的意思，它与 var 不同，var 会自动推断类型从而得出一个确定类型，而 dynamic 可以表示任意，相对于 Typescript 中的 any。

Dart 在声明时有以下几个基本类型：number、string、boolean、list、map、rune、symbol。

```js
int x = 1;
double y = 1.1;
num z = 1.2;
String x = 'abc';
enum Color { red, green, blue };        // 枚举类型
const msPerSecond = 1000;
bool flag = false;
var list = [1, 2, 3];
List arr = [1, 2, 3];
List<String> names = ['a', 'b', 'c'];   // 泛型
var constantList = const [1, 2, 3];
var gifts = {
    'first': 'partridge',
    'second': 'turtledoves',
    'fifth': 'golden rings'
};
Map nobleGases = const {
    2: 'helium',
    10: 'neon',
    18: 'argon',
};

print(gifts['first']);
```

特别说明：在 Dart 里，对象是 Map 不能用 `.` 的形式访问，只能用 `[]` 的形式访问。

## 函数
Dart 的函数支持函数声明、函数字面量、箭头函数、函数表达式、匿名函数。

```js
int add(int a, int b) {
    return a + b;
}

// 类型可省略
add(a, b) {
    return a + b;
}

// 箭头函数
var add = (a, b) => a + b;
int add(int a, int b) => a + b;

// 可选参数，使用 [] 限定
int add(int a, int b, [int c = 1, int d = 2]) => a + b + c + d;

// 显示指定参数名称，默认参数
int add({ int a = 1, int b = 2 }) {
    return a + b;
}
add(a: 1, b: 2);

// 回调函数
var list = ['apples', 'bananas', 'oranges'];
list.forEach((item) {
    print('${list.indexOf(item)}: $item');
});

// 回调 + 箭头
list.forEach((item) => print(item));

// 闭包
Function makeAdder(int addBy) {
    return (int i) => addBy + i;
}
```

注意：函数不存在函数提升。

## 操作符
操作符包括了：`expr++`、`expr--`、`()`、`[]`、`.`、`?.` 等，基本和 ES6 一致，除了没有 `===` 的判断。

例外有三个特色的操作：`is`、`as`、`is?`。

`is` 用于判断类型，`as` 用于续言、`is?` 与 `is` 相反。

```js
if (emp is Person) {
    // Type check
    emp.firstName = 'Bob';
}

(emp as Person).firstName = 'Bob';
```

级联符号（..）：允许您在同一个对象上进行一系列操作。除了函数调用之外，还可以访问同一对象上的字段。这通常会为您节省创建临时变量的步骤，并允许您编写更流畅的代码。

```js
var gifts = {
    'first': 'partridge',
    'second': 'turtledoves',
    'fifth': 'golden rings'
};

getGifts() {
    return gifts;
}

// 不使用级联符号
var g = getGifts();
g.first = 1;
g.second = 2;
g.fifth = 3;
// 使用级联符号
getGifts()
    ..first = 1
    ..second = 2
    ..fifth = 3;
```

级联符号对于时引用操作的是非常有用。

## 控制流程
Dart 的控制流程支持：if、if-else、for、while、do-while、switch、try-catch-finally、

```js
if (isRaining()) {
    // ...
} else if (isSnowing()) {
    // ...
} else {
    // ...
}

var message = new StringBuffer('Dart is fun');
for (var i = 0; i < 5; i++) {
    message.write('!');
}

var collection = [0, 1, 2];
for (var x in collection) {
    print(x); // 0 1 2
}
```

## 类结构
Dart 的类支持继承、静态方法、接口、构造函数、重载操作符、抽象类、接口类、 mixins等。

Dart 的类不支持什么 public、private 这些。

```js
class X {
    num x, y;
    X(x, y) {
        this.x = x;
        this.y = y;
    }
    void say() {
        print(this.x + this.y);
    }
}

class Point extends X {
    num x;
    num y;

    final int k = 1; // 无法被实例修改值

    static const int initialCapacity = 16; // 静态常量

    // 静态方法
    static add() {
        // ...
    }

    // 构造函数，用 :super(arg) 调用父类的构造函数
    // 等效 => Point(this.x, this.y): super(x, y);
    Point(num x, num y): super(x, y) {
        super.say(); // 调用父类的方法
        this.x = x;
        this.y = y;
    }
    // 命名构造函数（觉得构造函数长的丑，也可以命名哦）
    // var p = new Point.origin();
    Point.origin() {
        x = 0;
        y = 0;
    }

    // getter、setter 函数
    get xx => this.x;
    set xx(v) => this.x = xx;

    // 重写父类的方法，其实不佳 @override 也可以
    @override
    void say() {
        // ···
    }
}
```

Dart 还支持重载操作符。

```js
// 重载操作符
class Vector {
    final int x, y;

    const Vector(this.x, this.y);

    /// Overrides + (a + b).
    Vector operator +(Vector v) {
        return new Vector(x + v.x, y + v.y);
    }

    /// Overrides - (a - b).
    Vector operator -(Vector v) {
        return new Vector(x - v.x, y - v.y);
    }
}
```

Dart 中的实现接口类。

```js
class Impostor implements Person {
    get _name => '';
    String greet(String who) => 'Hi $who. Do you know who I am?';
}
```

Dart 能支持 mixins，使用 with 关键字。

```js
class Musician extends Performer with Musical {
    // ···
}
```

## 泛型
Dart 支持泛型哦。

```js
var names = <String>['Seth', 'Kathy', 'Lars'];
var pages = <String, String>{
    'index.html': 'Homepage',
    'robots.txt': 'Hints for web robots',
    'humans.txt': 'We are people, not machines'
};

var names = new List<String>();
names.addAll(['Seth', 'Kathy', 'Lars']);
names.add(42); // Error
print(names is List<String>); // true

// 泛型函数
T first<T>(List<T> ts) {
    T tmp = ts[0];
    return tmp;
}

// 泛型类
abstract class Cache<T> {
    T getByKey(String key);
    void setByKey(String key, T value);
}
```

## 模块
Dart 的模块导入。

```js
// 全部导入，并且是全局变量
import 'dart:math';
max(1, 2);

// 别名
import 'dart:math' as math;
math.max(1, 2);

// 只导入部分
import 'dart:math' show min;
min(1, 2);

// 懒加载，类似 ES6 的 import()
import 'dart:math' deferred as math;
Future greet() async {
    await math.max(1, 2);
}
```

导出模块，创建一个 myMath.dart 文件。

```js
int max(int a, int b) {
    return a > b ? a : b;
}

int _min(int a, int b) {
    return a < b ? a : b;
}
```

Dart 的导出默认是带下划线为私有，其他为公有。

```js
import './myMath.dart' as math;

math.max(1, 2);
```

## 异步编程
在 ES6 与异步相关的就是 Promise、async、await。而在 Dart 则是 Future、async、await。

Dart库充满了返回 Future 或 Stream 对象的函数。这些功能是异步的：它们在设置可能耗时的操作（例如 I/O）之后返回，而不等待该操作完成。
在 async 和 await 关键字支持异步编程，让你写异步代码看起来类似于同步代码。

使用 async/await 之前需要引入 dart:async 模块。

```js
import 'dart:async';

Future<String> lookUpVersion() async => '1.0.0';

Future main() async {
    await for (var request in requestServer) {
        handleRequest(request);
    }
}
```

也支持 then，catchError 等。

```js
void getIPAddress() {
    final url = 'https://httpbin.org/ip';
    HttpRequest.request(url).then((value) {
        print(json.decode(value.responseText)['origin']);
    }).catchError((error) => print(error));
}

// 也可以这样写
Future<String> getIPAddress() async {
    final url = 'https://httpbin.org/ip';
    var request = await HttpRequest.request(url);
    String ip = json.decode(request.responseText)['origin'];
    return ip;
}
```

## JSON 处理
json 在 JavaScript 里是一个非常有优势的处理，因为 json 本身延至于 JavaScript。

在 Dart 里处理 json 有两个 API 可用：`encode`（序列化） 和 `decode`（反序列化）。

```js
// 把对象转为 json 字符串
var jsonstr = json.encode([1, 2, { "a": null }]);

// 把 json 字符串转为对象
var decoded = json.decode('["foo", { "bar": 499 }]');
```

## 正则表达式
正则使用的是 RegExp 对象。

```js
RegExp exp = new RegExp(r"(\w+)");

// 返回正则表达式匹配项的可迭代对象
exp.allMatches("abc def ghi");

// 搜索并返回第一个匹配项，没有则返回null
exp.firstMatch("");

// 正则表达式是否找到匹配项
exp.hasMatch("as");

// 从第几个字符开始匹配正则表达式
exp.matchAsPrefix("ab cd", 3);

// 返回正则表达式的第一个匹配字符串
exp.stringMatch("abc de");

// 返回正则表达式的字符串表示
exp.toString();
```

## 定时器
因为定时器在前端里用得比较多，因此单独讲这部分。

定时器使用 Timer 实现，类似 js 的 setTimeout。

```js
import 'dart:async';

timer = new Timer(const Duration(milliseconds: 1500), () {
    // ... 1500ms 后执行内
});
```

也可以使用 **延迟操作**，返回是 Promise 哦。

```js
// 等待 2000ms
await new Future.delayed(const Duration(milliseconds: 2000));

// 或者
new Future.delayed(const Duration(milliseconds: 2000)).then(() {
    // ...
});
```