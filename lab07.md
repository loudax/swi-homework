# 机器语言实验报告

实验名称：机器语言实验

学号：18342060

姓名：刘心怡

# 实验目标

理解冯·诺伊曼计算机的结构

理解机器指令的构成

理解机器指令执行周期

用汇编编写简单程序

# 实验步骤与结果

## Program 1

输入指令。

![](https://raw.githubusercontent.com/loudax/Picture/master/program1.png)

点击"Binary"将指令转换为二进制形式。

![](https://raw.githubusercontent.com/loudax/Picture/master/program1%20binary.png)

点击"Symbolic"将指令转换回汇编语言形式。点击"STEP",进行第一步，执行指令00 LOD #3。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM1%2000.png)

点击"STEP",进行第二步，执行指令02 STO W。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM1%2002.png)

点击"STEP",进行第三步，执行指令04 LOD #7。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM1%2004.png)

点击"STEP",进行第四步，执行指令06 STO X。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM1%2006.png)

点击"STEP",进行第五步，执行指令08 ADD W。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM1%2008.png)

点击"STEP",进行第六步，执行指令10 STO Y。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM1%2010.png)

点击"STEP",进行第七步，执行指令12 HLT,程序结束。

本程序实现3+7的加法。

## Program 2

输入指令，将X的初值设置为3。

![](https://raw.githubusercontent.com/loudax/Picture/master/program2.png)

点击"Binary"将指令转换为二进制形式。

![](https://raw.githubusercontent.com/loudax/Picture/master/program2%20binary.png)

点击"Symbolic"将指令转换回汇编语言形式。点击"STEP",进行第一步，执行指令00 LOD X。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM2%2000.png)

点击"STEP",进行第二步，执行指令02 SUB #1。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM2%2002.png)

点击"STEP",进行第三步，执行指令04 JMZ 10,因为ACC中的数值不等于0，所以不会跳往指令10。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM2%2004.png)

点击"STEP",进行第四步，执行指令06 STO X。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM2%2006.png)

点击"STEP",进行第五步，执行指令08 JMP 0,跳往指令00，PC清零。library

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM2%2008.png)

不断循环直到执行指令04时，ACC中的值被减到0，跳往指令10 HLT，程序结束。

![](https://raw.githubusercontent.com/loudax/Picture/master/PROGRAM2%2010.png)

本程序实现：X初始值为3，每次减1，直到X变为0。


# 实验小结

## Program 1

**1. PC，IR 寄存器的作用。**

PC: 计数，指令完成后就立即增加2。

IR：储存当前执行的指令。

**2. ACC 寄存器的全称与作用。**

ACC：Accumulator

作用：存放操作数或运算结果。

**3. 用“LOD #3”指令的执行过程，解释Fetch-Execute周期。**

在RAM中提取指令00：LOD #3 (Fetch instruction)。将该指令寄存在IR中，将指令传到decoder进行解码(Decode instruction)。通过MUX将操作数3传到ALU，然后寄存到ACC，完成这个指令(Execute instruction)，最后PC增加2。

**4. 用“ADD W” 指令的执行过程，解释Fetch-Execute周期。**

同样地，在RAM中提取指令08：ADD W (Fetch instruction)。将该指令寄存在IR中，将指令传到decoder进行解码(Decode instruction)。将ACC中储存的7传到ALU，然后从RAM中获得W的值通过MUX传到ALU(Get data)。完成计算后，答案寄存到ACC中，完成这个指令(Execute instruction)，最后PC增加2。

**5. “LOD #3” 与 “ADD W” 指令的执行在Fetch-Execute周期级别，有什么不同。**

ADD W，需要调用W的值进行计算，所以多了Get data这一步。

**6. 写出指令 “LOD #7” 的二进制形式，按指令结构，解释每部分的含义。**

00010100 00000111

前三位无意义。第四位是寻址模式，如果是1表示操作数是数值，如果是0表示操作数是该地址的数据。第五到八位是操作码，0100表示LOD操作。根据第四位寻址模式是1，第九到十六位指被操作的数值，00000111表示十进制的7。

**7. 解释 RAM 的地址。**

指令的地址第一位是0，数据的地址第一位是1。后七位表示RAM中一个位置。根据地址来提取指令和数据。

**8. 该机器CPU是几位的？（按累加器的位数）**

8位。

**9. 写出该程序对应的 C语言表达。**

```c
int main(){
    int w=3;
    int x=7;
    int y=w+x;
    return 0;
}
```

## Program 2

**输入程序Program 2，运行并回答问题：**

**1. 用一句话总结程序的功能**

x的初始值为3，每次减1，直到减到0，程序结束

**2. 写出对应的 c 语言程序**

```c
int main(){
    int i=3;
    while(i!=0){
        i--;
    }
    return 0;
}
```

**修改该程序，用机器语言实现 10+9+8+..1 ，输出结果存放于内存 Y**

**1. 写出 c 语言的计算过程**

```c
int main(){
    int sum=0;
    int i=10;
    while(i!=0){
        sum=sum+i;
        i--;
    }
    return 0;
}
```

**2. 写出机器语言的计算过程**

W初值为10。

00 LOD X

02 ADD W

04 STO X

06 LOD W

08 SUB #1

10 JMZ 16

12 STO W

14 JMP 00

16 HLT

***3. 用自己的语言，简单总结高级语言与机器语言的区别与联系。**

区别：高级语言更易于我们理解，而机器语言全由01组成，我们理解起来相当困难，但对于计算机，它们只能理解机器语言。所以需要编译器，将我们写出来的高级语言转换成机器可以执行的机器语言。

联系：两者实现的功能是一样的。高级语言的实现终究还是要在机器语言的基础上完成。

实验目标的完成：

理解冯·诺伊曼计算机的结构

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Von_Neumann_architecture.svg/420px-Von_Neumann_architecture.svg.png)

理解机器指令的构成

前三位无意义。第四位是寻址模式，如果是1表示操作数是数值，如果是0表示操作数是该地址的数据。第五到八位是操作码。第九到十六位指被操作的数值或地址。

理解机器指令执行周期

main memory>>fetch instruction>>decode instruction>>registers>>(get data>>)execute instruction>>main memory

用汇编编写简单程序

见实验步骤与结果。
