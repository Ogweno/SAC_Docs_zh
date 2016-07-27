## trace

### 概要

追踪黑板变量和头段变量

### 语法

``` {.bash}
TRACE [ON|OFF] name [name ...]
```

### 输入

- `ON|OFF`: 打开/关闭变量追踪选项
- `name`: 要追踪的黑板变量或/和头段变量名。对于头段变量，其格式为
    `filename,hdrname`，其中 `filename` 是要追踪的SAC文件名
    或文件号，`hdrname` 是SAC头段变量名

### 缺省值

``` {.bash}
trace on
```

### 说明

该命令用于在SAC执行过程中追踪SAC黑板变量或/和头段变量的值，主要用于调试
大型或复杂的宏文件。当变量追踪选项被打开时，将显示变量的当前值。若变量
追踪选项处于打开状态，则每次执行命令时将对变量值进行检查，若变量的值
发生改变则将其新值打印到终端。当变量追踪选项被关闭时，也会显示变量的当
前值。

### 示例

追踪黑板变量TEMP1和文件MYFILE的头段变量 `T0`：

``` {.bash}
SAC> trace on temp1 myfile,t0
  TRACE  (on) TEMP1 = 1.45623
  TRACE  (on) MYFILE,T0 = UNDEFINED
```

在执行命令时，SAC会检查变量值是否发生改变。若发生改变则将相关信息显示出来。
假设在完成一些计算之后改变了TEMP1，并定义了 `T0` 的值，则SAC将
显示如下信息：

``` {.bash}
  TRACE (mod) TEMP1 = 2.34293
  TRACE (mod) MYFILE,T0 = 10.3451
```

稍后的处理中TEMP1可能再次改变：

``` {.bash}
  TRACE (mod) TEMP1 = 1.93242
```

当跟踪选项被关闭时，SAC最后一次显示变量当前值：

``` {.bash}
SAC> trace off temp1 myfile,t0
  TRACE (off) TEMP1 = 1.93242
  TRACE (off) MYFILE,T0 = 10.3451
```