点亮 LED
==========


点灯程序作为学习所有开发板的第一个程序，就像学所有编程语言都是先学 hello world 一样，具有着神圣的意义


总所周知， 点亮一个 LED 需要一个电源， 一个电阻， 一个 LED 灯泡，
在 Dan Dock 开发板上， 有三个 LED， 线路如下：

![](./assets/LED.png)


比如我们希望红灯点亮， 即 `LED_R` 连接的这个 LED， 图中可以看到 LED 的正极已经连接了 3.3V 电源， 所以我们只要让 LED_R 为低电平 LED 即可点亮。

在写程序前，我们需要知道， MaixPy 所使用的硬件 K210 的片上外设（比如GPIO、I2C等）对应的引脚是可以任意设置的，STM32 片上外设和引脚对应关系已经固定了， 只有部分引脚可以复用， 相比之下 K210 自由度更大。
> 比如 I2C 可以使用 Pin11 和 Pin12, 也可以改成其它任意引脚

我们控制 LED 需要使用到 GPIO

程序如下：

```python

from Maix import GPIO

fm.register(board_info.LED_R, fm.fpioa.GPIO0)

led_r=GPIO(GPIO.GPIO0,GPIO.OUT)
led_r.value(0)
```

我们只需要将这些代码一行行依次敲到终端里面键盘按确认来执行即可

其中， 我们先从包 `Maix` 导入了 `GPIO` 这个类；

前面说了　Ｋ210 的引脚可以任意设置，　所以我们使用`fm`(fpioa manager)这个内置的对象来注册芯片的外设和引脚的对应关系，　这里　`fm.fpioa.GPIO0` 是　Ｋ210 的一个 GPIO 外设（`注意区分 GPIO（外设） 和引脚（实实在在的硬件引脚）的区别` ）， 所以把 `fm.fpioa.GPIO0` 注册到了 引脚 `board_info.LED_R`；

这里的 `board_info` 是一个板子信息的类， 可以在串口终端输入 `board_info.` 然后按 `TAB` 按键可以看到所有成员，主要是各个引脚值


然后定义一个 `GPIO` 对象， 具体参数看 `GPIO` 模块的文档， 在左边侧边栏查找。

使用 `led_r.value(0)` 或者 `led_r.value(1)` 来设置高低电平即可


到这里已经可以点灯了， 如果了解 Python 语法的小伙伴可以尝试 写个 for 循环来实现 LED 闪烁～





