## addf {#cmd:addf}

### 概要

将一组数据加到内存中的另一组数据中

### 语法

ADDF \[N`EWHDR` \[ON|OFF\]\] filelist

### 输入

NEWHDR ON|OFF

:   指定新生成的文件使用哪个文件的头段。`OFF`
    表示使用内存中原文件的头段区，`ON` 表示使用filelist中文件的
    头段区。缺省值为 `OFF`

filelist

:   SAC二进制文件列表

### 说明

简单地说，该命令要做的就是C=A+B，其中A是已读入内存的文件，B是磁盘中要加到A的文件，C是
文件加法的生成物。该命令会将磁盘中的一组文件，与内存中的另一组文件分别相加。若内存中的
文件数多于filelsit中文件数，则filelist的最后一个文件将加到内存中余下的文件中；
若filelist中的文件数多于内存中的文件数，则filelist中多余的文件将被忽略。

要相加的两个文件必须满足如下条件才能执行加法操作：

-   为等间隔时间序列文件

-   有相同的采样间隔 `delta`

-   有相同的数据点数 `npts`

-   文件开始时间有相同的绝对时刻

若两个待相加的文件的时刻不完全匹配，则会给出警告，但相加操作会继续执行。若采样间隔或数据
点数不匹配，默认情况下SAC会认为这是致命（`fatal`）错误，直接报错退出。可以通过
[binoperr](/commands/binoperr.html)
命令将采样间隔或数据点数的不匹配设置为忽略（`ignore`）、
警告（`warning`）或致命（`fatal`）。

在将不匹配设置为 `ignore` 或 `warning` 的前提下，SAC会忽略采样
周期的不匹配，直接对数据做加法，不论是否使用了 `newhdr on`
选项，都使用第一个
数据文件的采样周期作为生成数据的采样周期；对于数据点数不匹配的情况，则取最小的数据点数作为
最终结果文件的数据点数。

### 示例

将一个文件加到其他三个文件中：

``` {.bash}
SAC> r file1 file2 file3
SAC> addf file4
```

将两个文件分别加到另两个文件中：

``` {.bash}
SAC> r file1 file2
SAC> addf file3 file4
```

### 头段变量

depmin、depmax、depmen、npts、delta
