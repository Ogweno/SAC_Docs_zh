## begindevices

### 概要

启动某个图像设备

### 语法

``` {.bash}
BEGINDEVICES SGF|XWINDOWS
```
``` {.bash}
BD S|X
```

### 输入

- `SGF`: SAC图像文件设备
- `XWINDOWS`: X Window 窗口显示系统

### 说明

该命令用于启动一种图像设备，之后的所有绘图都会被传送到该设备中，直到
再次执行 `begindevices` 启动其它图像设备或
[enddevices](/commands/enddevices.md) 结束该图像设备为止。

SAC默认使用 `xwindows` 图像设备。具体用法见 [图像保存](/graphics/save-image.md)
一节的示例。
