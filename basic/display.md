## 绘图

SAC中有四个常用的绘图命令，分别是
[plot](/commands/plot.md)、[plot1](/commands/plot1.md)、
[plot2](/commands/plot2.md)、[plotpk](/commands/plotpk.md)。这一节只介绍最基础的
`plot` 命令，其他的命令及更多的绘图功能将在 [SAC 绘图](/graphics) 中说明。

`plot` 命令会在单个图形窗口中显示单个波形：

``` {.bash}
SAC> r cdv.[nez]
SAC> p
Waiting
Waiting
SAC>
```

上面的示例中，首先将三个波形数据读入内存，然后使用 `plot` 命令
绘图，此时焦点位于绘图窗口，且绘图窗口中只显示第一个波形，终端中出现
“Waiting”字样；将焦点切换回终端（Linux下的快捷键是Alt+Tab）。
敲击回车键，绘图窗口中显示第二个波形，终端中出现第二个“Waiting”字样，
焦点位于终端中；再次敲击回车键，窗口中显示第三个波形，焦点位于终端，
由于已经没有更多的波形需要显示，此时终端中显示SAC提示符。

如果内存中还有波形在“Waiting”，而你想要退出plot，不想要再继续查看
后面的波形，可以在终端中键入 `kill`（简写为 `k`），即可
直接退出plot，如下例：

``` {.bash}
SAC> r cdv.[nez]
SAC> p
Waitingk
SAC>
```
