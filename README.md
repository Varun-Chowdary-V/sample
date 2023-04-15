# sample
Demonstrating git commands
git clone: Used to copy remote repo to local
git pull: It is used to update local content with that of github


#include<stdio.h>
#define size 3
void printBoard(char a[size][size]){
    printf("-----------------\n");
    for(int i=0;i<size;i++){
        if(i==0){
            printf("|   | 1 | 2 | 3 |\n");
        }
        for(int j=0;j<size;j++){
            if(j==0){
                printf("| %d ",i+1);
            }
            printf("| %c ",a[i][j]);
        }
        printf("|\n");
    }
    printf("-----------------\n");
}
int play(int player,char players[2][30],int a[size][size]){
    int winner=-1,pos,val,posx,posy,gameover=-1;
    char ch;
    printf("Now it's %s's turn\n",players[player]);
    printf("Enter your position (Like 3th row 1st column as 31)\n");
    scanf("%d",&pos);
    if(player==0){
        ch='O';
    }
    else{
        ch='X';
    }
    posx=pos/10;
    posy=pos%10;
    printf("You have inserted %c in %dth row and %dth column position\n",ch,posx,posy);
    a[posx-1][posy-1]=ch;
    printBoard(a);
    if(a[0][0]==a[1][1] && a[1][1]==a[2][2]){
        gameover=1;
        winner=player;
    }
    else if(a[2][0]==a[1][1] && a[1][1]==a[0][2]){
        gameover=1;
        winner=player;
    }
    else if(a[0][0]==a[0][1] && a[0][1]==a[0][2]){
        gameover=1;
        winner=player;
    }
    else if(a[1][0]==a[1][1] && a[1][1]==a[1][2]){
        gameover=1;
        winner=player;
    }
    else if(a[2][0]==a[2][1] && a[2][1]==a[2][2]){
        gameover=1;
        winner=player;
    }
    else if(a[0][0]==a[1][0] && a[1][0]==a[2][0]){
        gameover=1;
        winner=player;
    }
    else if(a[0][1]==a[1][1] && a[1][1]==a[2][1]){
        gameover=1;
        winner=player;
    }
    else if(a[0][2]==a[1][2] && a[1][2]==a[2][2]){
        gameover=1;
        winner=player;
    }
    return winner;
}
void main() {
    char a[size][size];
    int n,gameover=-1,pos,val,posx,posy;
    char players[2][30],ch;
    int winner;
    for(int i=0;i<size;i++)
        for(int j=0;j<size;  j++)
            a[i][j]="+";
    printf("Enter names of two the players\n");
    for(int i=0;i<2;i++){
        scanf("%s",players[i]);
    }
    printf("Are you Ready\n");
    printf("Lets start the game\n");
    printBoard(a);
    while(gameover==-1){
        for(int i=0;i<2&&gameover==-1;i++){
            gameover=play(i,players,a);
            printBoard(a);
            if(gameover==i){
                printf("Hurray! %s wins\n",players[i]);
                printf("Thanks for playing\n");
            }
        }
    }
}
