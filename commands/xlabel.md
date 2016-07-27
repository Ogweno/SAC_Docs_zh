## xlabel

### 概要

定义X轴标签及属性

### 语法

``` {.bash}
XLABEL [ON|OFF|text] [LOCATION TOP|BOTTOM|RIGHT|LEFT]
    [SIZE TINY|SMALL|MEDIUM|LARGE]
```
``` {.bash}
XLABL [ON|OFF|text] [L T|B|R|L] [S T|S|M|L]
```

### 输入

- `text`: 打开X轴标签选项，设置标签为 `text`。若文本含空格， 需要用引号括起来
- `ON`: 打开X轴标签选项，但不改变标签文本
- `OFF`: 关闭X轴标签选项
- `LOCATION`: 设定X轴标签的位置。可以取 `TOP`、`BOTTOM`、 `RIGHT`、`LEFT`
- `SIZE`: 改变绘图标签的文本尺寸
- `TINY`: 每行132个字符
- `SMALL`: 每行100个字符
- `MEDIUM`: 每行80字符
- `LARGE`: 大尺寸，每行50字符

### 缺省值

``` {.bash}
xlabel off location bottom size small
```

### 说明

若打开X轴标签选项，则绘图时会在图上显示X轴标签。标签的尺寸和位置以及
文本均可以改变。文本质量以及字体可以使用 [gtext](/commands/gtext.md)
命令设置。