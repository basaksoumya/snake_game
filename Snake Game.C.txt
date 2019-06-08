#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <windows.h>
void view();
void snakestart();
void food();
char box[31][61];//row,column
void right(int ,int);
void left(int ,int);
void up(int ,int);
void down(int ,int);
void gotoxy(int ,int);
int countx,county;
int length=1,first=0;
int fd_x,fd_y;
long int score=0;
int main()
{
            view();
            snakestart();
            food();
            gotoxy(countx,county);
            while(1)
{
            int choice;
            choice=getch();
            switch(choice)
			{
            	case '6':
                    right(countx,county);
                    break;
                case '4':
                   left(countx,county);
                   break;
                case '8':
                   up(countx,county);
                   break;
                case '2':
                   down(countx,county);
                   break;
            }
}

    getch();
}
void view()
{
    for(int j=0;j<=30;j++){
     for(int i=0;i<=60;i++)
        if(j==0||j==30||i==0||i==60)  printf("%c",box[j][i]='*');
         else     printf("%c",box[j][i]=' ');
     printf("\n");
    }
}
void snakestart(){
    int x=30,y=15;
    gotoxy(x,y);
    countx=x,county=y;
    printf("%c",box[x][y]='o');
}
void food(){
    int x=(rand()%38)+1;
    int y=(rand()%28)+1;
    fd_x=x;
	fd_y=y;
	gotoxy(x,y);
    printf("%c",box[x][y]='F');
    first=1;
}
void right(int x,int y)
{
	int body=length;
	if(x==30&&y==15){
		gotoxy(30,15);
	    box[x][y]=' ';
	    printf("%c",box[x][y]);
	}
    int pre_x;
    do
    {
    	pre_x=x;
    	x++;
    	gotoxy(pre_x,y);
        printf("%c",box[pre_x][y]=' ');
        gotoxy(x,y);
        countx=x,county=y;
        if(x==60||y==30||x==0||y==0)
    	   printf("%c",box[x][y]='*');
    	else
    	   printf("%c",box[x][y]='o');
    	if(x==fd_x&&y==fd_y){
    	    food();
    	    score++;
    	}
    	gotoxy(countx,county);
    	if(x==60||y==30||x==0||y==0){
    		gotoxy(0,31);
    		printf("Game is over\n");
    		printf("Your score is %d\n",score);
    		if(score<10)
    		  printf("You are a noob in this game.\nyou have to pactice a lot.\n");
    		else if(score<20)
    		  printf("You are a average player\n");
    		else
    		  printf("Well!Keep it up\n");
    		box[countx-1][county-1]='*';
    		exit(0);
		}
    }while(getch()=='6');
}
void left(int x,int y)
{
	if(x==30&&y==15){
		gotoxy(30,15);
	    box[x][y]=' ';
	    printf("%c",box[x][y]);
	}
	int pre_x;
    do
    {
        pre_x=x;
    	x--;
    	gotoxy(pre_x,y);
        printf("%c",box[pre_x][y]=' ');
        gotoxy(x,y);
        countx=x,county=y;
    	if(x==60||y==30||x==0||y==0)
    	   printf("%c",box[x][y]='*');
    	else
    	   printf("%c",box[x][y]='o');
    	if(x==fd_x&&y==fd_y){
    	    food();
    	    score++;
    	}
    	if(x==60||y==30||x==0||y==0){
    		gotoxy(0,31);
    		printf("Game is over\n");
    		printf("Your score is %d\n",score);
    		if(score<10)
    		  printf("you are a noob in this game\nyou have to pactice a lot\n");
    		else if(score<20)
    		  printf("you are a average player\n");
    		else
    		  printf("well!Keep it up\n");
    		box[countx-1][county-1]='*';
    		exit(0);
		}
    }while(getch()=='4');
}
void up(int x,int y)
{
	if(x==30&&y==15){
		gotoxy(x,y);
	    printf("%c",box[x][y]=' ');
	}
	int pre_y;
    do
    {
    	pre_y=y;
    	y--;
    	countx=x,county=y;
    	gotoxy(x,pre_y);
        printf("%c",box[x][pre_y]=' ');
        gotoxy(x,y);
        countx=x,county=y;
    	if(x==60||y==30||x==0||y==0)
    	   printf("%c",box[x][y]='*');
    	else
    	   printf("%c",box[x][y]='o');
    	if(x==fd_x&&y==fd_y){
    	    food();
    	    score++;
    	}
    	if(x==60||y==30||x==0||y==0){
    		gotoxy(0,31);
    		printf("Game is over\n");
    		printf("Your score is %d\n",score);
    		if(score<10)
    		  printf("you are a noob in this game\nyou have to pactice a lot\n");
    		else if(score<20)
    		  printf("you are a average player\n");
    		else
    		  printf("well!Keep it up\n");
    		box[countx-1][county-1]='*';
    		exit(0);
		}
    }while(getch()=='8');
}
void down(int x,int y)
{
	if(x==30&&y==15){
		gotoxy(x,y);
	    box[x][y]=' ';
	    printf("%c",box[x][y]);
	}
	int pre_y;
    do
    {
    	pre_y=y;
    	y++;
    	countx=x,county=y;
    	gotoxy(x,pre_y);
        printf("%c",box[x][pre_y]=' ');
        gotoxy(x,y);
        countx=x,county=y;
    	if(x==60||y==30||x==0||y==0)
    	   printf("%c",box[x][y]='*');
    	else
    	   printf("%c",box[x][y]='o');
    	if(x==fd_x&&y==fd_y){
    	    food();
    	    score++;
    	}
    	if(x==60||y==30||x==0||y==0){
    		gotoxy(0,31);
    		printf("Game is over\n");
    		printf("Your score is %d\n",score);
    		if(score<10)
    		  printf("you are a noob in this game\nyou have to pactice a lot\n");
    		else if(score<20)
    		  printf("you are a average player\n");
    		else
    		  printf("well!Keep it up\n");
    		box[countx-1][county-1]='*';
    		exit(0);
		}
    }while(getch()=='2');
}
void gotoxy(int x,int y)
{
    COORD c;
    c.X=x;
    c.Y=y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),c);
}