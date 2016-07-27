## addstack

### 概要

向迭加文件列表中加入新文件

### 语法

``` {.bash}
ADDSTACK filename [WEIGHT v] [DISTANCE v] [BEGINTIME v] [ENDTIME v]
    [DELAY v [SECONDS|POINTS]] [INCREMENT v [SECONDS|POINTS]]
    [NORMAL|REVERSE]
```
``` {.bash}
AS filename [W v] [DI v] [BE v] [END v] [DE v [S|P]] [I v [S|P]] [N|R]
```

### 输入

- `filename`: 要加入迭加文件列表中的文件
- `WEIGHT v`: 当前文件的权重因子。v的取值范围为0到1，在迭加之前会首先对文件的每个值乘以该权重因子再做迭加。
- `DISTANCE v`: 该文件所对应的震中距，单位为 。用于计算动态时间延迟
- `BEGINTIME v`: 事件开始的时间
- `ENDTIME`: 事件结束时间
- `DELAY v SECONDS|POINTS`: 该文件的静态时间延迟，单位为秒或数据点数
- `INCREMENT v SECONDS|POINTS`: 该文件的静态时间延迟增量，单位为秒或数据点数。在每次执行incrementstack命令时，静态时间延迟会增加一个常数。
- `NORMAL|REVERSED`: 文件拥有正/负极性

### 缺省值

DELAY和INCREMENT选型的缺省单位为SECONDS

### 说明

每个迭加列表中的文件，都有7个属性，分别为：

1.  权重因子；
2.  台站到震中的距离；
3.  事件开始时间；
4.  事件结束时间；
5.  静态时间延迟；
6.  静态时间延迟增量；
7.  数据极性；

可以用 [globalstack](/sss/globalstack.md)
命令为这些迭加属性设置全局值。当一个文件通过
[addstack](/sss/addstack.md)
命令加入到迭加文件列表中时，若未指定属性值则使用全局属性值。
[changestack](/sss/changestack.md)
可以用于在文件已经加入迭加文件列表后修改迭加属性值。

### 示例

``` {.bash}
SAC/SSS> gs delay 1.0 inc 0.03
SAC/SSS> as filea delay 2.0
SAC/SSS> as fileb delay 3.0 inc 0.01 rev
SAC/SSS> as filec
SAC/SSS> as filed w 0.5
```

第一个命令修改了时间延迟和时间延迟增量的全局属性值，其他全局属性则使用缺省值。

-   filea：除时间延迟外其他属性均与全局属性相同；
-   fileb：除时间延迟、时间延迟增量、信号极性外，其余属性均与全局属性相同；
-   filec：所有属性与全局熟悉相同；
-   filed：除权重因子外，其他所有属性与全局属性相同；

接下来对信号进行迭加：

``` {.bash}
SAC/SSS> sumstack
```

该命令会讲迭加文件列表中的四个文件filea、fileb、filec和filed进行迭加，时间延迟分别为2.0、3.0、1.0和1.0。文件filec的极性反转。文件filed在迭加时的权重是其他文件权重的一半。

``` {.bash}
SAC/SSS> incrementstack
SAC/SSS> changestack filec normal
SAC/SSS> sumstack
```

此次迭加，各个文件使用2.03、3.01、1.03和1.03的延迟。文件filec现在为正极性。

``` {.bash}
SAC/SSS> deletestack filed
SAC/SSS> incrementstack
SAC/SSS> sumstack
```

第三次迭加讲只对文件filea、fileb、filec进行，时间延迟分别为2.06、3.02、1.06。

### 限制

迭加文件列表中文件数目的最大限制与SAC所能读取的文件数目一致，即最多1000个。
