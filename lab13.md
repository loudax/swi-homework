# 贪吃蛇实验报告

实验名称：贪吃蛇编程实验

学号：18342060

姓名：刘心怡

## snake_move.c

```c
#include<stdio.h>

#define SNAKE_MAX_LENGTH 20
#define SNAKE_HEAD 'H'
#define SNAKE_BODY 'X'
#define BLANK_CELL ' '
#define SNAKE_FOOD '$'
#define WALL_CELL '*'

void output(char map[12][12]); 
int move_left(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int move_right(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int move_up(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int move_down(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int countinue_or_not(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int direction,char action);

int main(){
	char map[12][12]={
		"************",
		"*XXXXH     *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"************"};
	int flag = 1,direction = 2, length = 5;
	char action;
	int snake_x[SNAKE_MAX_LENGTH]={5,4,3,2,1},snake_y[SNAKE_MAX_LENGTH]={1,1,1,1,1};
	while(flag){
		scanf("%c", &action);
		switch(action){
			case 'a': 	flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;
						direction = move_left(map,snake_x,snake_y,length);
						output(map);
						break;//a left
			case 'd':	flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;
						direction = move_right(map,snake_x,snake_y,length);
						output(map);
						break;//d right
			case 'w':  	flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;
						direction = move_up(map,snake_x,snake_y,length);
						output(map);
						break;//w up
			case 's':  	flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;
						direction = move_down(map,snake_x,snake_y,length);
						output(map);
						break;//s down
		}
		
	}
	
	printf("GAME OVER!\n");
	
} 

void output(char map[12][12]){
	int i, j;
	for(i=0;i<12;i++){
			for(j=0;j<12;j++){
				printf("%c",  map[i][j]);
			}
			printf("\n");	
		} 
}

int move_left(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]][snake_x[0]-1]='H';
	map[snake_y[0]][snake_x[0]] ='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}   
	snake_x[0]--;
	return 1;
}

int move_right(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]][snake_x[0]+1]='H'; 
	map[snake_y[0]][snake_x[0]] ='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}   
	snake_x[0]++;
	return 2;
}

int move_up(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]-1][snake_x[0]]='H';  
	map[snake_y[0]][snake_x[0]]='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}  
	snake_y[0]--;
	return 3;
}

int move_down(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]+1][snake_x[0]]='H';  
	map[snake_y[0]][snake_x[0]]='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}  
	snake_y[0]++;
	return 4;
}

int countinue_or_not(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int direction,char action){
	if(action=='a'&&direction==2)
		return 0;
	if(action=='d'&&direction==1)
		return 0;
	if(action=='w'&&direction==4)
		return 0;
	if(action=='s'&&direction==3)
		return 0;
	if(action=='a'&&map[snake_y[0]][snake_x[0]-1]=='*')
		return 0;
	if(action=='d'&&map[snake_y[0]][snake_x[0]+1]=='*')
		return 0;
	if(action=='w'&&map[snake_y[0]-1][snake_x[0]]=='*')
		return 0;	
	if(action=='s'&&map[snake_y[0]+1][snake_x[0]]=='*')
		return 0;	
} 
```

## snake_eat.c

```c
#include<stdio.h>
#include<stdlib.h>
#include<time.h>

#define SNAKE_MAX_LENGTH 20
#define SNAKE_HEAD 'H'
#define SNAKE_BODY 'X'
#define BLANK_CELL ' '
#define SNAKE_FOOD '$'
#define WALL_CELL '*'

void output(char map[12][12]); 
int move_left(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int move_right(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int move_up(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int move_down(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length);
int countinue_or_not(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int direction,char action);
void set_food(char map[12][12]);
//int eat_food(char map[12][12]);


int main(){
	char map[12][12]={
		"************",
		"*XXXXH     *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*          *",
		"*   $      *",
		"*          *",
		"************"};
	int flag = 1,direction = 2, length = 5;
	char action;
	int snake_x[SNAKE_MAX_LENGTH]={5,4,3,2,1},snake_y[SNAKE_MAX_LENGTH]={1,1,1,1,1};
	
	output(map);
	
	while(flag){
		
		scanf("%c", &action);
	
		switch(action){
			case 'a': 	flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;	
						direction = move_left(map,snake_x,snake_y,length);
						output(map);
						break;//a left
						
			case 'd':	
						flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;
						direction = move_right(map,snake_x,snake_y,length);
						output(map);
						break;//d right
			case 'w':  	flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;
						direction = move_up(map,snake_x,snake_y,length);
						output(map);
						break;//w up
			case 's':  	flag = countinue_or_not(map,snake_x,snake_y,direction,action);
						if(flag==0)
							break;
						direction = move_down(map,snake_x,snake_y,length);
						output(map);
						break;//s down
		}
		
	}
	
	printf("GAME OVER!\n");
	
} 

void output(char map[12][12]){
	int i, j;
	for(i=0;i<12;i++){
			for(j=0;j<12;j++){
				printf("%c",  map[i][j]);
			}
			printf("\n");	
		} 
}

int move_left(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]][snake_x[0]-1]='H';
	map[snake_y[0]][snake_x[0]] ='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}   
	snake_x[0]--;
	return 1;
}

int move_right(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]][snake_x[0]+1]='H'; 
	map[snake_y[0]][snake_x[0]] ='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}   
	snake_x[0]++;
	return 2;
}

int move_up(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]-1][snake_x[0]]='H';  
	map[snake_y[0]][snake_x[0]]='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}  
	snake_y[0]--;
	return 3;
}

int move_down(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int length){
	int i;
	map[snake_y[0]+1][snake_x[0]]='H';  
	map[snake_y[0]][snake_x[0]]='X';
	map[snake_y[length-1]][snake_x[length-1]]=' ';
	for(i=length-1;i>0;i--){
		snake_x[i] = snake_x[i-1];
		snake_y[i] = snake_y[i-1]; 
	}  
	snake_y[0]++;
	return 4;
}

int countinue_or_not(char map[12][12],int snake_x[SNAKE_MAX_LENGTH],int snake_y[SNAKE_MAX_LENGTH],int direction,char action){
	if(action=='a'&&direction==2)
		return 0;
	if(action=='d'&&direction==1)
		return 0;
	if(action=='w'&&direction==4)
		return 0;
	if(action=='s'&&direction==3)
		return 0;
	if(action=='a'&&map[snake_y[0]][snake_x[0]-1]=='*')
		return 0;
	if(action=='d'&&map[snake_y[0]][snake_x[0]+1]=='*')
		return 0;
	if(action=='w'&&map[snake_y[0]-1][snake_x[0]]=='*')
		return 0;	
	if(action=='a'&&map[snake_y[0]+1][snake_x[0]]=='*')
		return 0;	
	if(action=='a'&&map[snake_y[0]][snake_x[0]-1]=='X')
		return 0;
	if(action=='d'&&map[snake_y[0]][snake_x[0]+1]=='X')
		return 0;
	if(action=='w'&&map[snake_y[0]-1][snake_x[0]]=='X')
		return 0;	
	if(action=='a'&&map[snake_y[0]+1][snake_x[0]]=='X')
		return 0;
} 

void set_food(char map[12][12]){
	int food_x, food_y;
	while(1){
		srand(time(NULL));
		food_x = rand()%10+1;
		food_y = rand()%10+1;
		if(map[food_y][food_x]!='X'&&map[food_y][food_x]!='H'){
			map[food_y][food_x]='$';	
			break;
		}
	}	
}

```