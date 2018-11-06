# 介绍小游戏及其软件设计

## 游戏策划

**Gameplay**

飞机碰到橙色飞弹则爆炸，玩家通过鼠标控制飞机躲避橙色飞弹。每隔五秒随机出现星星，飞机触及星星则分数+1。

**Game Sprites**

1. 飞机

鼠标操控，遇到飞弹则爆炸，游戏结束。遇到星星则分数+1。

2. 飞弹

每隔1秒随机匀速从界面上边沿垂直向下飞。遇到飞机，飞机爆炸，游戏结束。

3. 星星

每隔5秒随机出现在界面里。遇到飞机，分数+1，星星消失。

4. 爆炸

当飞机与飞弹碰撞时出现。

## 游戏设计

| 飞机 |
|:----- |
|图片:![](https://raw.githubusercontent.com/loudax/Picture/master/%E9%99%86%E7%A9%BA%E6%88%98%E4%BA%89%E5%A1%94%E9%98%B2%E7%B1%BB%E6%B8%B8%E6%88%8F%E8%B5%84%E6%BA%90-%E4%BA%8C%E6%88%98%E6%97%B6%E6%9C%9F-10_%E7%88%B1%E7%BB%99%E7%BD%91_aigei_com.png)|
|位置:随鼠标移动|
|飞弹 → 触碰到飞弹后销毁自己，出现爆炸特效，游戏结束|
|星星 → 触碰到星星，星星消失，分数+1|
|爆炸 → 触碰飞弹后出现|

|飞弹|
|:----- |
|图片:![](https://raw.githubusercontent.com/loudax/Picture/master/2D%E9%A3%9E%E6%9C%BA%E7%B4%A0%E6%9D%90-%E9%A3%9E%E8%A1%8C%E7%89%A9-%E5%AD%90%E5%BC%B9%E6%A9%99%E8%89%B20003(bullet_ora_%E7%88%B1%E7%BB%99%E7%BD%91_aigei_com.png))|
|位置：每隔一秒随机出现在界面上边缘，然后垂直向界面下边缘匀速运动|
|飞机 → 触碰到飞机后，飞弹自行销毁，出现爆炸特效，游戏结束|
|爆炸 → 触碰到飞机后出现|

|星星|
|:-----|
|图片：![](https://raw.githubusercontent.com/loudax/Picture/master/%E5%8A%A8%E7%89%A9%E8%B7%91%E9%85%B7%E6%B8%B8%E6%88%8F%E3%80%8A%E5%BF%AB%E4%B9%90%E5%A5%94%E8%B7%912%E3%80%8B%E5%85%A8%E5%A5%97%E7%B4%A0%E6%9D%90-%E6%98%9F%E6%98%9F1(stars1)_%E7%88%B1%E7%BB%99%E7%BD%91_aigei_com.png)|
|位置：每隔五秒随机出现在界面上任何一个位置|
|飞机 → 触碰到飞机，星星消失，分数+1|

|爆炸|
|:-----|
|图片：![](https://raw.githubusercontent.com/loudax/Picture/master/explode.png)|
|位置：出现在飞机与飞弹触碰的地方|
|飞机 → 飞机触碰到飞弹后出现爆炸特效，游戏结束|

## 游戏效果

![](https://raw.githubusercontent.com/loudax/Picture/master/%E9%A3%9E%E6%9C%BA.gif)