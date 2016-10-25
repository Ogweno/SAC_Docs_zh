## Python中调用SAC

### 简单示例

下面的脚本展示了如何在Python中调用SAC。

[include](0.simple-script.py)

Python中使用 `subprocess` 模块的 `Popen` 方法调用SAC， 通过
`p.communicate()` 将命令 `s.encode()` 传递给SAC。

### 数据转换

首先要将SEED格式的数据转换成SAC格式。

-   假定每个目录下有且只有一个SEED数据
-   `rdseed` 一次只能处理一个SEED数据
-   `rdseed` 的 `-pdf` 选项会提取出SAC波形数据和PZ格式的仪器响应文件

[include](1.rdseed.py)

### 文件合并

SEED文件的波形数据可能会因为多种原因而出现间断，导致同一个通道会解压出来
多个SAC文件，因而需要将属于同一个通道的SAC数据合并起来。

-   此处使用了新版 [merge](/commands/merge.md) 命令的语法，要求SAC版本大于v101.6
-   `merge` 命令还有更多选项可以控制数据合并的细节，见命令的语法介绍
-   合并后的数据，以最早的数据段的文件名命名
-   多余的数据段均被删除，以保证每个通道只有一个SAC文件
-   由于脚本运行速度比SAC运行速度快，因而应先退出SAC再删除多余的数据段

[include](2.merge.py)

### 文件重命名

从SEED解压出的SAC文件名较长，因而对其重命名以简化。

-   SEED解压出的默认文件名格式为 `yyyy.ddd.hh.mm.ss.ffff.NN.SSSSS.LL.CCC.Q.SAC`
-   重命名后的文件名为 `NET.STA.LOC.CHN.SAC`

[include](3.rename.py)

### 添加事件信息

若SEED中不包含事件信息，则解压得到的SAC文件中也不会包含事件信息。因而
需要用户手动添加事件的发震时刻、经纬度、深度和震级信息。

-   输入参数包括：目录名、发震时刻、经度、纬度、深度、震级
-   发震时刻的格式为 `yyyy-mm-ddThh:mm:ss.xxx`，其中 `T` 用于分隔日期和时间

[include](4.eventinfo.py)

### 去仪器响应

使用PZ文件去仪器响应。若数据的时间跨度太长，在该时间跨度内可能仪器响应会
发生变化，因而会存在一个通道有多个PZ文件的情况。目前该脚本在遇到这种情况
时会自动退出。

[include](5.transfer.py)

### 分量旋转

将成对的水平分量旋转到大圆路径。

-   检查三分量是否缺失
-   检查 `delta` 是否相等
-   取三分量中的最大 `b` 和最小 `e` 值作为数据窗口，此 操作要求三分量的
    `kzdate` 和 `kztime` 必须相同，这一点 在添加事件信息时使用
    [synchronize](/commands/synchronize.md) 已经实现
-   未检查分量的 `cmpinc` 和 `cmpaz` 是否符合要求。若不
    符合要求，SAC会报错且不会旋转，写到磁盘中的R和T分量实际上是原数据，
    暂不知如何处理。

[include](6.rotate.py)

### 数据重采样

通常有两种情况下需要对数据进行重采样：

-   原始数据的采样率过高，而实际研究中不需要如此高的采样率，此时，对数据
    做减采样可以大大减少数据量；
-   原始数据中，不同台站的采样率不同，可能会影响到后期的数据处理，因而
    需要让所有数据使用统一的采样率；

下面的Python脚本中使用 [interpolate](/commands/interpolate.md)
命令将所有数据重采样到相同
的采样周期。用户可以在命令行中直接指定要使用的重采样后的采样周期，若命令行
中的采样周期指定为0，则以大多数数据所使用的采样周期作为重采样后的采样周期。

[include](7.resample.py)