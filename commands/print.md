## print {#cmd:print}

### 概要

打印最近的SGF文件

### 语法

PRINT \[printer\]

### 说明

这个命令会打印最近生成的SGF文件，因而在该命令前至少要产生一个SFG文件。
该命令会将SGF文件发送至打印机printer，如果没有指定则使用系统默认打印机。
如果自从登录之后SGF设备一直保持关闭，那么print命令就不会工作。 可以使用
[begindevices](/commands/begindevices.md)
打开SGF设备，使用SGF命令设置SGF设备的属性。
