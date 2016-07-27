## globalstack

### 概要

设置全局迭加属性

### 语法

``` {.bash}
GLOBALSTACK [WEIGHT v] [DISTANCE v] [DELAY v [SECONDS|POINTS]]
    [INCREMENT v [SECONDS|POINTS] [NORMAL|REVERSED]
```
``` {.bash}
GS [W v] [DI v] [DE v [S|P]] [I v [S|P] [N|R]
```

### 输入

- `WEIGHT v`: 全局权重因子，取值为0至1；
- `DISTANCE v`: 全局震中距，单位为 ；
- `DELAY v SECONDS|POINTS`: 全局静时间延迟，单位为 或数据点数；
- `INCREMENT v SECONDS|POINTS`: 全局静时间延迟的增量，单位为 或数据点数；
- `NORMAL|REVERSED`: 正/负极性；

### 说明

该命令用于定义全局迭加属性，这些全局迭加属性用于迭加文件列表中的每个文件。可以使用
[addstack](/sss/addstack.md)命令为某个文件单独设定迭加属性。
