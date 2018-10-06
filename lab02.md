
# Construct2的初尝试

## 什么是Construct2？

根据Construct2官网上所介绍：“Construct2 is a powerful ground breaking HTML5 game creator designed specifically for 2D games. It allows anyone to build games — no coding required!”即Construct2是一个为2D的HTML5游戏设计的制作软件，并且不需要编程基础。

第一次，我打算制作一个简单的射击游戏，并以此为范例，制作这个教程。

## 一、新建项目

打开Construct2，显示如下页面，点击箭头指的“New Project”来新建项目。再双击“New Empty Project”。

![](https://github.com/loudax/Picture/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20181004162114.png?raw=true)

![](https://github.com/loudax/Picture/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20181005081155.png?raw=true)

## 二、插入背景和其他元素

双击空白处，显示“Insert New Object”，双击“General”中的“Tiled Background”插入背景，双击“Sprite”插入其他元素。

![](https://github.com/loudax/Picture/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20181005083442.png?raw=true)

## 三、增加行为

在右边的"Properties"的"Behaviors"中设置。

![](https://github.com/loudax/Picture/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20181007001048.png?raw=true)

我这次做的游戏中只用到Bullet movement，Bound to layout，Destroy outside layout，Fade这几个行为。

**8 Direction movement**

实现让角色通过方向键操控朝8个方向行动

**Bullet movement**

实现让物件向当前方向运动

**Scroll to**

实现角色行动时，背景跟随角色移动

**Bound to layout**

防止物件离开画布区域

**Destroy outside layout**

实现物件离开画布区域时，将其销毁

**Fade**

实现物件的淡出效果

## 四、事件

以我制作的这个游戏为例，将我希望达成的效果添加进事件里。
1.希望飞机能随鼠标移动而移动。
2.当飞机碰到子弹时，飞机毁灭，出现爆炸效果，子弹也毁灭。
3.当飞机碰到星星时，星星毁灭，分数score+1。
4.随时在TextBox里显示当前分数。
5.每5秒在画布区域出现一颗星星。
6.每1秒在画布区域上边缘随机出现一粒子弹（难度越大，间隔时间越短）。
7.子弹垂直向下运动。

![](https://github.com/loudax/Picture/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20181007003255.png?raw=true)

## 五、运行

点击"Run layout".

![](https://github.com/loudax/Picture/blob/master/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20181007004526.png?raw=true)

我制作的游戏效果如图，虽然没什么创意，但做出来还是挺有成就感的，

![](https://github.com/loudax/Picture/blob/master/%E9%A3%9E%E6%9C%BA.gif?raw=true)





