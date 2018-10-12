# CMY与CMYK

## CMY

**简介**

![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c7/%E9%A1%8F%E8%89%B2%E6%B8%9B%E6%B3%95.svg/400px-%E9%A1%8F%E8%89%B2%E6%B8%9B%E6%B3%95.svg.png)

CMY是和RGB相对的。RGB是红（Red）、绿（Green）和蓝（Blue）三种颜色的简写，是相加混色模式，颜色的取值范围为0-255，RGB常用于计算机显示方面。CMY是青（Cyan）、洋红（Magenta）和黄（Yellow）三种颜色的简写，是相减混色模式，这种方法产生的颜色被称为相减色，CMY常用于纸张彩色打印方面。


**CMY与RGB转换**

大多数将颜料沉淀于纸上的设备，如彩色打印机和复制机，都需要CMY数据输入，或在内部将RGB转化为CMY。转换公式为：

C=255-R

M=255-G

Y=255-B

相应的，从255减去C、M、Y的值，也可以得到RGB值。

## CMYK

![](https://upload.wikimedia.org/wikipedia/commons/b/b2/CMYK_color_swatches.png)

**简介**

CMYK也称作印刷色彩模式，顾名思义就是用来印刷的。它和RGB相比有一个很大的不同：RGB模式是一种发光的色彩模式，你在一间黑暗的房间内仍然可以看见屏幕上的内容；
CMYK是一种依靠反光的色彩模式，它需要有外界光源，如果你在黑暗房间内是无法阅读报纸的。

**CMY与CMYK的关系**

现实中由于生产技术的限制，油墨纯度往往不尽人意，混合出的黑色不够浓郁，因此在印刷术中，常常加一种真正的黑色（black ink），这种模型称为CMYK模型，广泛应用于印刷术。

**CMYK与RGB之间的转换**

R = 255*(100-C)*(100-K)/10000

G = 255*(100-M)*(100-K)/10000

B = 255*(100-Y)*(100-K)/10000
