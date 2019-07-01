

## Image（图片）

[Image](https://docs.flutter.io/flutter/widgets/Image-class.html) 是一个用于展示图片的组件。支持 JPEG、PNG、GIF、Animated GIF、WebP、Animated WebP、BMP 和 WBMP 等格式。

Image 有许多的静态函数：
- **Image.asset** - 用于从资源目录的显示图片。
- **Image.network** - 用于从网络上显示图片。
- **Image.file** - 用于从文件里显示图片。
- **Image.memory** - 用于从内存里（Uint8List）显示图片。

```js
// 资源图片
Image.asset('imgs/logo.jpeg'),
//网络图片
Image.network('https://flutter.io/images/homepage/header-illustration.png'),
// 本地文件图片
Image.file(File("/Users/gs/Downloads/1.jpeg")),
// Uint8List图片
Image.memory(bytes),
//使用ImageProvider加载图片
Image(image: NetworkImage("https://flutter.io/images/homepage/screenshot-2.png"))
```

Image 有以下常用属性：
- **alignment → AlignmentGeometry** - 图像边界内对齐图像。
- **centerSlice → Rect** - 九片图像的中心切片。
- **color → Color** - 该颜色与每个图像像素混合colorBlendMode。
- **colorBlendMode → BlendMode** - 用于 color 与此图像结合使用。
- **fit → BoxFit** - 图像在布局中分配的空间。
- **gaplessPlayback → bool** - 当图像提供者发生变化时，是继续显示旧图像（true）还是暂时不显示（false）。
- **image → ImageProvider** - 要显示的图像。
- **matchTextDirection → bool** - 是否在图像的方向上绘制图像 TextDirection。
- **repeat → ImageRepeat** - 未充分容器时，是否重复图片。
- **height → double** - 图像的高度。
- **width → double** - 图像的宽度。

### 圆角图片
Image 是不支持圆角和阴影的，目前可以通过使用 CircleAvatar 和 Container 实现。

```js
var img = 'https://b-ssl.duitang.com/uploads/item/' +
        '201602/15/20160215235057_EU3tS.thumb.700_0.jpeg';

CircleAvatar(
  backgroundImage: NetworkImage(url),
  radius: 100.0,      // --> 半径越大，图片越大
),
```

![no-shadow](/../../image/20180630001326.png)

使用 Container 实现，其原理是把图片放在 decoration 里，而不是 child 里，因为把图片放在 child 里并设置 borderRadius 时会出现一个图片穿透的问题，Container 还没有 overflow 属性。

```js
Container(
  width: 200.0,
  height: 200.0,
  margin: const EdgeInsets.all(20.0),
  decoration: BoxDecoration(
    color: Colors.white,
    image: DecorationImage(
      image: NetworkImage(this.imgsrc),
      fit: BoxFit.cover,
    ),
    shape: BoxShape.circle,
  ),
),
```

上面实现的都是一个圆形图片，下面的实现一个真正的圆角图片。

```js
Container(
  width: 200.0,
  height: 200.0,
  margin: const EdgeInsets.all(20.0),
  decoration: BoxDecoration(
    color: Colors.white,
    image: DecorationImage(
      image: NetworkImage(this.imgsrc),
      fit: BoxFit.cover
    ),
    shape: BoxShape.rectangle,            // <-- 这里需要设置为 rectangle
    borderRadius: BorderRadius.all(
      const Radius.circular(20.0),        // <-- rectangle 时，BorderRadius 才有效
    ),
  ),
),
```

![no-shadow](/../../image/20180630122957.png)

### 内存图片
在使用网络图片或者是资源图片时会出现短暂的闪图效果（加载时间导致），有时候为了避免这个问题，需要使用内存图片（也叫缓存图片），它先通过预下载，随后直接从内存里读取。

MemoryImage 类可以完成这件事情。

```js
import 'package:flutter/material.dart';
import 'package:flutter/services.dart' show rootBundle;
import 'dart:typed_data';

class MemoryImageDemo extends StatefulWidget {
  _MemoryImageDemoState createState() => _MemoryImageDemoState();
}

class _MemoryImageDemoState extends State<MemoryImageDemo> {
  Uint8List bytes;

  void initState() {
    super.initState();
    // 加载图片
    rootBundle.load('assets/images/food01.jpeg').then((data) {
      if (!mounted) return;
      setState(() {
          // 读取字节码
          bytes = data.buffer.asUint8List();
      });
    });
  }

  @override
  Widget build(BuildContext context) {
    final decoration =  BoxDecoration(
      image: bytes == null ? null : DecorationImage(
        image: MemoryImage(bytes, scale: 1.0),
      ),
    );
    return Container(
      width: 300.0,
      height: 300.0,
      decoration: decoration,
    );
  }
}
```