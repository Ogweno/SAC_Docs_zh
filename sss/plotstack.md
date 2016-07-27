## plotstack

### 概要

绘制迭加文件列表中的文件

### 语法

``` {.bash}
PLOTSTACK [SUM ON|OFF] [PERPLOT ON|OFF|n] [WEIGHT ON|OFF] [POLARITY ON|OFF]
```
``` {.bash}
PS [S ON|OFF] [P ON|OFF|n] [W ON|OFF] [P ON|OFF]
```

### 输入

- `SUM ON|OFF`: 若打开该选项，则首先绘制迭加后的波形再绘制迭加文件列表中的文件；若关闭该选项，则只回执迭加文件列表中的文件
- `PERPLOT ON|OFF`: 若打开该选择，则每次只绘制固定数目的文件；若关闭该选项，则一次绘制迭加列表中的全部文件
- `PERPLOT n`: 打开PERPLOT选项，并设置每次绘制n个文件
- `WEIGHT ON|OFF`: 打开/关闭文件权重选项
- `POLARITY ON|OFF`: 打开/关闭文件极性选项

### 缺省值

``` {.bash}
plotstack sum on perplot off weight on polarity on
```

### 说明

该命令绘制迭加文件列表中的文件，所有的文件首先根据静/动延迟进行时移，
该命令可以控制绘制文件时是否考虑权重因子和极性。

该命令的用法与 [plot1](/commands/plot1.md) 类似，在每个子图的左上角会显示文件名
以及其他非默认的属性值。