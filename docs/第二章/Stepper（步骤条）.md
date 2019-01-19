

## Stepper（步骤条）
Stepper 是一个步骤条组件。

![](/../../image/20180701163707.png)

```js
new Stepper(
    currentStep: 0,  // <-- 激活的下标
    steps: <Step>[
        new Step(
            title: new Text('第一步'),
            content: new Text('第一步内容'),
            state: StepState.complete,
            isActive: true,
            subtitle: new Text('第一步小标题'),
        ),
        new Step(
            title: new Text('第二步'),
            content: new Text('第二步内容'),
        ),
        new Step(
            title: new Text('第三步'),
            content: new Text('第三步内容'),
        ),
    ],
)
```

![](/../../image/20180701163926.png)

Stepper 有以下常用属性：
- **currentStep → int** - 步骤位置。
- **onStepCancel → VoidCallback** - 点击 cancel 时触发。
- **onStepContinue → VoidCallback** - 点击 continue 时触发。
- **onStepTapped → ValueChanged<int>** - 状态改变时触发。
- **steps → List<Step>** - 步骤内容。
- **type → StepperType** - 摆放方向，默认是垂直的，可以设置为水平的。
