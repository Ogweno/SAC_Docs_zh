## highpass

### 概要

对数据文件应用一个无限脉冲高通滤波器

### 语法

``` {.bash}
HIGHPASS [BUTTER|BESSEL|C1|C2] [CORNERS v1 v2] [NPOLES n] [PASSES n]
    [TRANBW v] [ATTEN v]
```
``` {.bash}
HP [BU|BE|C1|C2] [C v1 v2] [N n] [P n] [T v] [A v]
```

### 输入

- `BUTTER`: 应用一个Butterworth滤波器
- `BESSEL`: 应用一个Bessel滤波器
- `C1`: 应用一个Chebyshev I型滤波器
- `C2`: 应用一个Chebyshev II滤波器
- `CORNERS v1 v2`: 设定拐角频率分别为v1和v2，即频率通带为v1–v2
- `NPOLES n`: 设置极数为 `n`，可以取1到10之间的整数
- `PASSES n`: 设置通道数为 `n`，可以取1或2
- `TRANBW v`: 设置Chebyshev转换带宽为v
- `ATTEN v`: 设置Chebyshev衰减因子为v

### 缺省值

``` {.bash}
highpass butter corner 0.2 npoles 2 passes 1 tranbw 0.3 atten 30
```

### 说明

参见 [bandpass](/commands/bandpass.md) 的相关说明。

### 示例

应用一个四极Butterworth，拐角频率为 2 Hz：

``` {.bash}
SAC> hp n 4 c 2
```

在此之后如果要应用一个二极双通具有相同频率的Bessel：

``` {.bash}
SAC> hp n 2 be p 2
```

### 头段变量

depmin、depmax、depmen
