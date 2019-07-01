
## BackdropFilter（模糊层）
BackdropFilter 是一个用于实现模糊层的组件，可以轻易的实现模糊背景效果，非常炫酷，但是这个部件的代价很高（高斯算法），尽量少用。

通常 BackdropFilter 需要使用 ImageFilter 来产生模糊感，又配合 Stack 实现层叠。

下面示例，使用 Stack 组件用来包裹堆叠视图，在里面有两个 container，第一个是背景网络图片，第二个就是一个 BackdropFilter，实现了背景图片的模糊效果。

```js
var img = 'xxxx';

Stack(
  children: [
    Container(
      // 背景图
      decoration: BoxDecoration(
        image: DecorationImage(
          image: NetworkImage(img),
          fit: BoxFit.cover,
          colorFilter: ColorFilter.mode(
            Colors.black54,
            BlendMode.overlay,
          ),
        ),
      ),
    ),
    Container(
      // 模糊成
      child: BackdropFilter(
        filter: ImageFilter.blur(sigmaX: 10.0, sigmaY: 10.0),
        // 加上透明度
        child: Opacity(
          opacity: 0.6,
          child: Container(
            decoration: BoxDecoration(
              color: Colors.grey.shade900,
            ),
          ),
        ),
      ),
    ),
  ],
);
```

![](../../image/20190701221244.png)
