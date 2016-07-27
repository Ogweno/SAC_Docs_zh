## bandrej {#cmd:bandrej}

### 概要

应用一个无限脉冲带阻滤波器

### 语法

B`AND`R`EJ` \[BU`TTER`|BE`SSEL`|C1|C2\] \[C`ORNERS` v1 v2\] \[N`POLES`
n\] \[P`ASSES` n\] \[T`RANBW` v\] \[A`TTEN` v\]

### 输入

BUTTER

:   应用一个Butterworth滤波器

BESSEL

:   应用一个Bessel滤波器

C1

:   应用一个Chebyshev I型滤波器

C2

:   应用一个Chebyshev II滤波器

CORNERS v1 v2

:   设定拐角频率分别为v1和v2，即频率通带为v1–v2

NPOLES n

:   设置极数为 `n`，可以取1到10之间的整数

PASSES n

:   设置通道数为 `n`，可以取1或2

TRANBW v

:   设置Chebyshev转换带宽为v

ATTEN v

:   设置Chebyshev衰减因子为v

### 缺省值

bandrej butter corner 0.1 0.4 npoles 2 passes 1 tranbw 0.3 atten 30

### 说明

参见命令 [bandpass](/commands/bandpass.html) 的说明

### 示例

应用一个四极Butterworth滤波器，拐角频率为 和 ：

``` {.bash}
SAC> br n 4 c 2 5
```

在此之后如果要应用一个二极双通具有相同频率的Bessel：

``` {.bash}
SAC> br n 2 be p 2
```

### 头段变量改变

depmin、depmax、depmen
