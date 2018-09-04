
## Flutter 简介
Flutter 移动应用程序 SDK 是为开发人员提供一种创建快捷、美观的应用程序的新方式，从而摆脱过去那种千篇一律的 app，尝试过 Flutter 的人都会真的爱上它。

Flutter 是一个跨平台的移动应用开发框架，它的构建灵感来自于 React Native。在 React Native 里，会有两个线程，JS 线程处理逻辑，UI 线程处理视图，它们通过 JSBridge 通信。Flutter 不同的是会直接编译成原生代码执行，并不像 React Native 那样，因此 Flutter 的性能会比 React Native 相对要好。

Flutter 有以下特性：
- **快速开发**：支持毫秒级的热重载，修改后，您的应用界面会立即更新。使用丰富的、完全可定制的 widget 在几分钟内构建原生界面。
- **富有表现力和灵活的 UI**：快速发布聚焦于原生体验的功能。分层的架构允许您完全自定义，从而实现难以置信的快速渲染和富有表现力、灵活的设计。
- **原生性能**：Flutter 包含了许多核心的 widget，如滚动、导航、图标和字体等，这些都可以在 iOS 和 Android 上达到原生应用一样的性能。

### 系统架构
Flutter 应用运行在一个用 C++ 写的引擎中，Flutter 应用可以看做是一个游戏 App，代码都是在引擎中运行。

- **Android**：引擎的 C 或 C++ 代码是由 Android NDK 编译的，而框架的主要代码和应用的代码由 Dart compiler 编译成 native code 执行的。

- **iOS**：引擎的 C 或 C++ 代码是由 LLVM 编译的，而所有 Dart 的代码会被 AOT 编译成 native code，整个 App 运行时使用的是机器指令（并不是拦截器）。

![no-shadow](/../../image/20180701221513.png)
![no-shadow](/../../image/20180701221518.png)
![no-shadow](/../../image/20180701221523.png)
![no-shadow](/../../image/20180701221529.png)
![no-shadow](/../../image/20180701221534.png)
