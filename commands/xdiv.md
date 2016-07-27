## xdiv

### 概要

控制x轴的刻度间隔

### 语法

``` {.bash}
XDIV [NICE|INCREMENT v|NUMBER n] [POWER ON|OFF]
```
``` {.bash}
XDIV [NI|I v|NU n] [P ON|OFF]
```

### 输入

- `NICE`: 由SAC自动选择合适的刻度间隔
- `INCREMENT v`: 设置刻度间隔增量为v
- `NUMBER n`: 设置刻度的总数目数为n
- `POWER ON`: 打开幂指数选项，SAC以幂指数形式给出刻度值
- `POWER OFF`: 关闭幂选项

### 缺省值

``` {.bash}
xdiv nice power on
```

### 说明

该命令控制X轴的刻度间隔。多数时候默认的 `nice` 间隔即可满足需求。 SAC的
`nice` 刻度间隔是根据坐标轴的最小最大值、坐标轴的长度以及
当前坐标轴文本尺寸来决定的。

也可以使用 `INCREMENT` 选项强制刻度间隔为一个定值，或者使用 `NUMBER`
选项设置刻度间隔的数目。
