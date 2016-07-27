## changestack {#sss:changestack}

### 概要

修改当前迭加文件列表中的文件属性

### 语法

C`HANGE`S`TACK` filename|filenumber \[W`EIGHT` v\] \[DI`STANCE` v\]
\[BE`GINTIME` v\] \[END`TIME` v\] \[DE`LAY` v S`ECONDS`|P`OINTS`\]
\[I`NCREMENT` v S`ECONDS`|P`OINTS`\] \[N`ORMAL`|R`EVERSED`\]

### 输入

filename

:   迭加文件列表中的文件名

filenumber

:   迭加文件列表中的文件号

WEIGHT v

:   当前文件的权重因子。v的取值范围为0到1，在迭加之前会首先对文件的每个值乘以该权重因子再做迭加。

DISTANCE v

:   该文件所对应的震中距，单位为 。用于计算动态时间延迟

BEGINTIME v

:   事件开始的时间

ENDTIME

:   事件结束时间

DELAY v SECONDS|POINTS

:   该文件的静态时间延迟，单位为秒或数据点数

INCREMENT v SECONDS|POINTS

:   该文件的静态时间延迟增量，单位为秒或数据点数。在每次执行incrementstack命令时，静态时间延迟会增加一个常数。

NORMAL|REVERSED

:   文件拥有正/负极性

### 说明

该命令允许你修改修改迭加文件列表中任意文件的任意属性。详情参考
nameref-sss-addstack 命令。
