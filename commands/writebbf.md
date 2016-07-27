## writebbf {#cmd:writebbf}

### 概要

将黑板变量文件写入到磁盘

### 语法

W`RITE`BBF \[file\]

### 输入

file

:   黑板变量文件的文件名

### 缺省值

writebbf bbf

### 说明

该命令让你能够将当前会话的所有黑板变量写入到磁盘文件中，稍后可以使用
[readbbf](/commands/readbbf.html)
命令将黑板变量文件重新读入SAC，该特性允许你保存
某次SAC会话的信息，并用于另一次SAC会话中。你也可以在自己的程序中调用
SAC函数库以访问黑板变量文件中的信息。
