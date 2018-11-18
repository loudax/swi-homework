# python编程实验报告

实验名称：python编程实验

学号：18342060

姓名：刘心怡

## 实验目标

1. 选择2个高等数学上的作业，如泰勒分解、公式化简、解方程等。 （一般搜索不到有价值的答案）

2. 选择2个线性代数上的作业，如求dot、逆矩阵等，最好会解方程。（建议阅读《用Python做科学计算》）

## 实验步骤与结果

1. 高等数学

(1) 求导

![](https://raw.githubusercontent.com/loudax/Picture/master/%E6%B1%82%E5%AF%BC.png)

diff(函数名，变量名)

(2) 积分

![](https://raw.githubusercontent.com/loudax/Picture/master/%E7%A7%AF%E5%88%861.png)

integrate(待求积分的函数，变量名)

2. 线性代数

(1) 转置

![](https://raw.githubusercontent.com/loudax/Picture/master/%E8%BD%AC%E7%BD%AE.png)

矩阵名.T

(2) 乘法

![](https://raw.githubusercontent.com/loudax/Picture/master/dot.png)

dot(矩阵名1,矩阵名2)

(3) 逆

![](https://raw.githubusercontent.com/loudax/Picture/master/%E9%80%86.png)

np.linalg.inv(矩阵名)