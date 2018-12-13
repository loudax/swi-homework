# 贪吃蛇实验报告

实验名称：智能蛇编程实验

学号：18342060

姓名：刘心怡 

由普通贪吃蛇到智能蛇，只需要用一个where_to_go的函数决定该往哪里走来替代手动键入‘a’‘s’‘d’‘w’来决定方向。函数代码如下。 

```c
char where_to_go(int head_x,int head_y,int food_position[2],int direction){
	if(direction == 1){
		if(head_x==food_position[0]){
			if(head_y>food_position[1])
				return 'w';
			else
				return 's';
		}
		else{
			if(head_x>food_position[0])
				return 'a';
			else{
				if(head_y>food_position[1])
					return 'w';
				else
					return 's';
			} 
		    
		}	
	}
	if(direction == 2){
		if(head_x==food_position[0]){
			if(head_y>food_position[1])
				return 'w';
			else
				return 's';
		}
		else{
			if(head_x<food_position[0])
				return 'd';
			else{
				if(head_y>food_position[1])
					return 'w';
				else
					return 's';
			} 
		    
		}	
	}
	if(direction == 3){
		if(head_y==food_position[1]){
			if(head_x>food_position[0])
				return 'a';
			else
				return 'd';
		}
		else{
			if(head_y>food_position[1])
				return 'w';
			else{
				if(head_x<food_position[0])
					return 'd';
				else
					return 'a';
			} 
		    
		}	
	}
	if(direction == 4){
		if(head_y==food_position[1]){
			if(head_x>food_position[0])
				return 'a';
			else
				return 'd';
		}
		else{
			if(head_y<food_position[1])
				return 's';
			else{
				if(head_x<food_position[0])
					return 'd';
				else
					return 'a';
			} 
		    
		}	
	}
}
```

我看到网上关于智能蛇的代码有更好的更简便的方法，但碍于水平不够，我并没有看懂……于是写了一个很麻烦的函数，把蛇头的四个方向都进行了假设，也实现了判断往哪个方向走的功能。

另一个麻烦接踵而至，linux上的操作令人头大。虽然有了2班学委的指导，成功安装上了配置好的虚拟机，但还是遇到了两个问题。

1. 学委给的教程中，在terminal里输入的是cd /home/desktop，但我在操作中发现，输入之后毫无反应，尝试多次后才发现应该输入cd /home/sysu/Desktop

2. 编译过程中一直报错，后来发现是注释的问题，把所有注释删掉之后就可以了。

运行效果如图：

![](https://raw.githubusercontent.com/loudax/Picture/master/%E6%99%BA%E8%83%BD%E8%9B%87.gif)

运行完毕后发现了一个问题，我的智能蛇还不够智能，它只能判断怎么走可以很快地接近食物，但没有判断这么走会不会撞到自己的蛇身。接下来会完善这一点。

思考：一个长度为5的障碍物能困死该自动跑的蛇吗？

我认为是会的。