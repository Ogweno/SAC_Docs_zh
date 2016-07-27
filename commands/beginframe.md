## beginframe

### 概要

打开frame，用于绘制组合图

### 语法

``` {.bash}
BEGINFRAME
```
``` {.bash}
BF
```

### 说明

一般情况下，在每次使用绘图命令时，SAC会对绘图设备执行刷新操作，以清除
上一个绘图命令绘制的图像，然后再显示本次命令绘制的图像，这样可以保证
多次绘图命令绘制的图像不会重叠在一起。

`beginframe` 命令会关闭绘图设备的自动刷新功能，直到
[endframe](/commands/endframe.md)
命令恢复自动刷新功能为止。在这两个命令中间执行的
所有绘图命令所产生的图像将会叠加在一起，形成组合图。

通过这两个命令，并结合 [xvport](/commands/xvport.md) 和
[yvport](/commands/yvport.md) 定义
每次绘图的viewport，可以很容易地绘制出复杂的组合图。

关于如何绘制组合图以及这几个命令的使用，可以参考 [组合图](/graphics/composite-plots.md)
一节。
