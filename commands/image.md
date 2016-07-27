## image {#cmd:image}

### 概要

利用内存中的数据文件绘制彩色图

### 语法

IMAGE \[COLOR|GREY\] \[BINARY|FULL\]

### 输入

COLOR|GREY

:   绘制彩图或者灰度图

BINARY|FULL

:   绘图时所有正值是一个颜色，所有负值是另一种颜色，
    或者根据数据值不同变换颜色

### 缺省值

image color full

### 说明

该命令允许用户用SAC三维数据绘制彩图或灰度图。

三维数据可以用
[spectrogram](/commands/spectrogram.md)、[sonogram](/commands/sonogram.md)
或 [bbfk](/commands/bbfk.md)
命令产生，也可以自己生成SAC格式的三维数据。可以使用
[xlim](/commands/xlim.md) 和 [ylim](/commands/ylim.md)
以控制要显示的绘图效果，也可以 使用其他命令对数据做振幅上的操作。

### 示例

以SAC v101.5c自带的contourdata为例：

``` {.bash}
SAC> r contourdata
SAC> image
```

![image示意图](image){width="90.00000%"}

### 头段变量

需要：iftype （设为“IXYZ”）、nxsize、nysize

使用：xminimum、xmaximum、yminimum、ymaximum
