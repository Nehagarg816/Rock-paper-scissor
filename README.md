# Rock-paper-scissor
This is a program for a game Rock Paper Scissor using library of time.h in C programming.


#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    char Name[30];
    static int win = 0;
    static int loose = 0;
    static int drawn = 0;
    int n;
    printf("Rock=0,Paper=1,Scissor=2\n");
    printf("Enter your name:\n");
    scanf("%s", &Name);

    for (int i = 0; i < 3; i++)
    {
        srand(time(NULL));
        int s = rand() % 3;
        printf("PLAYER 1: %s Turn\n", strupr(Name));
        scanf("%d", &n);
        printf("%s:%d\n", Name, n);
        printf("PLAYER 2: Computer Turn\n");
        printf("Computer:%d\n", s);

        if (n == s)
        {
            printf("MATCH DRAWN AND BOTH GET 0 POINTS\n");
            drawn++;
        }
        else if (n == 0 && s == 2 || n == 1 && s == 0 || n == 2 && s == 1)
        {
            printf("%s WIN THE GAME AND GET 1 POINT\n", strupr(Name));
            win++;
        }
        else
        {
            printf("COMPUTER WIN THE GAME AND GET 1 POINT\n");
            loose++;
        }
    }

    printf("\n\n");

    if (win == 1 && loose == 1 && drawn == 1 || drawn == 3)
    {
        printf("MATCH IS DRAWN\n");
        printf("PLEASE TRY AGAIN\n");
    }
    else if (win == 2 || win == 1 && drawn == 2)
    {
        printf("CONGRATS %s WINS THE GAME", strupr(Name));
    }
    else
    {
        printf("OOPS YOU LOOSE THE GAME");
    }

    return 0;
}
