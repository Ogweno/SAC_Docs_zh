## 图像格式转换

SAC中的图像可以保存为SGF、PS和PDF格式，有些时候会需要将其转换为其他
图像格式，比如JPG或PNG。

`convert` 是Linux下的一个功能强大的图像格式转换工具。如果你的
系统里没有这个命令，你可以通过安装 `ImageMagick` 来获取该命令。

`convert` 命令的选项众多，这里只说其中几个常用的选项：

-   `-trim` ：切边，即将图像周围多余的白边切除；
-   `-density` *width*`x`*height*：设置图像精度，一般情况下，
    设置width为300即可，height可以不指定。
-   `-rotate` *degree*：图像旋转的角度；

下面给出一个简单的例子：

``` {.console}
    convert -trim -density 300x300 -rotate 90 image.ps image.png
```
