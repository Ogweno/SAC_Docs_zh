## SAC设计思想

SAC的设计思想大概可以总结如下:

1.  每个信号被保存到单独的SAC格式数据文件中；信号，或称之为trace，即**单个**台站**单个**仪器**单个**分量记录到的连续时间序列。
2.  SAC格式包含了描述数据特征的头段区和存储信号的数据区，参见 [SAC文件格式](/fileformat) 一章；
3.  将单个或多个SAC文件从磁盘读入内存；
4.  通过各种命令对内存中的数据进行操作；
5.  操作完毕，将内存中的数据写入到磁盘，可以覆盖原SAC文件或写入新文件中。

读取SAC文件时的若干限制：

-   SAC一次性最多处理1000个SAC文件；想要修改这个上限，参考 [修改最大允许的文件数目](/tricks-and-traps/max-allowed-files.md) 一节；
-   单个文件名所允许的最大长度为128字符；
