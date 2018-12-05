# 贪吃蛇

1.snake_move.c

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <conio.h>
#include <string.h>
#include <time.h>
int main(){
    char map[12][13]=
    {"************",
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
    "************"} ; 
   int m;
    for(m = 0;m<12;++m){
        printf("%s\n",map[m]);
    }
    int length = 5;
    int snakey[400] = {1,1,1,1,1};
    int snakex[400] = {5,4,3,2,1};

    for( ;length != 0;){        
        char dir = _getch();            
        if(dir == 'W' || dir == 'w'){
            int m;
                for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
        -- snakey[0];
        ++ length;
        continue;
        
     }   
    
    if(dir == 'S' || dir =='s'){
            int m;
        for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
            ++ snakey[0];
            length++;
               continue;
    } 
    if(dir == 'A' || dir == 'a'){
            int m;   
            for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
            -- snakex[0];
            ++ length;
                continue;
    }
    if(dir == 'D' || dir == 'd'){
            int m;
        for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
        ++ snakex[0];
        ++ length;
        continue;
    }
}
for(m = 0;m<12;++m){
            printf("%s\n",map[m]); 
        }       
}



2.snake_eat.c

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <conio.h>
#include <string.h>
#include <time.h>

void getfood(char map[][13]){
    next:
    srand((unsigned)time(NULL));
    int i, j;
    i = rand() % 8 + 1;
    j = rand() % 8 + 1;
    if(map[i][j] == 'H'|| map[i][j] == 'X')
        goto next;
    map[i][j] = '$';
}
int main(){
    char map[12][13]=
    {"************",
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
    "************"} ; 
getfood(map);
    int m;
    for(m = 0;m<12;++m){
        printf("%s\n",map[m]);
    }
    int length = 5;
    int snakey[400] = {1,1,1,1,1};
    int snakex[400] = {5,4,3,2,1};

    for( ;length != 0;){        
        char dir = _getch();            
        if(dir == 'W' || dir == 'w'){
            int m;
            if(map[snakey[0]-1][snakex[0]] == '$'){
                map[snakey[0]-1][snakex[0]] = 'H';
                map[snakey[0]][snakex[0]] = 'X';
                for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
        -- snakey[0];
        ++ length;
        getfood(map);
        continue;   
    }
    if(map[snakey[0]-1][snakex[0]] == '*' || map[snakey[0]-1][snakex[0]] == 'X'){       
        break;
    }
            for(m = 0;m < length - 1;++ m){
                map[snakey[0]-1][snakex[0]] = 'H';
                map[snakey[m]][snakex[m]] = map[snakey[m+1]][snakex[m+1]];                                  
            }
            map[snakey[m]][snakex[m]] = ' ' ;
            map[snakey[m-1]][snakex[m-1]] ='X'; 
            for(m = 0;m < length - 1;++ m){
                snakex[length - m -1] = snakex[length - m -2];
                snakey[length - m -1] = snakey[length - m -2];  
            }               
            -- snakey[0];       
}

        if(dir == 'S' || dir =='s'){
            int m;
    if(map[snakey[0]+1][snakex[0]] == '$'){
        map[snakey[0]+1][snakex[0]] = 'H';
        map[snakey[0]][snakex[0]] = 'X';
        for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
            ++ snakey[0];
            length++;
            getfood(map);           
            continue;       
    }
    if(map[snakey[0]+1][snakex[0]] == '*' || map[snakey[0]+1][snakex[0]] == 'X'){
        break;
    }
            for(m = 0;m < length - 1;++ m){
                map[snakey[0]+1][snakex[0]] = 'H';
                map[snakey[m]][snakex[m]] = map[snakey[m+1]][snakex[m+1]];                                      
            }
            map[snakey[m]][snakex[m]] = ' ' ;
            map[snakey[m-1]][snakex[m-1]] ='X';             
            for(m = 0;m < length - 1;++ m){
                snakex[length - m -1] = snakex[length - m -2];
                snakey[length - m -1] = snakey[length - m -2];
            }           
            ++ snakey[0];           
        }
        if(dir == 'A' || dir == 'a'){
            int m;
            if(map[snakey[0]][snakex[0]-1] == '$'){
                map[snakey[0]][snakex[0]-1] = 'H';
                map[snakey[0]][snakex[0]] = 'X';
            for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
            -- snakex[0];
            ++ length;
            getfood(map);
            continue;       
    }
    if(map[snakey[0]][snakex[0]-1] == '*' || map[snakey[0]][snakex[0]-1] == 'X'){
        length = 0;
        break;
    }
            for(m = 0;m < length - 1;++ m){
                map[snakey[0]][snakex[0]-1] = 'H';
                map[snakey[m]][snakex[m]] = map[snakey[m+1]][snakex[m+1]];                          
            }
            map[snakey[m]][snakex[m]] = ' ' ;
            map[snakey[m-1]][snakex[m-1]] ='X'; 
            for(m = 0;m < length - 1;++ m){
                snakex[length - m -1] = snakex[length - m -2];
                snakey[length - m -1] = snakey[length - m -2];  
            }                               
            -- snakex[0];           
        }
        if(dir == 'D' || dir == 'd'){
            int m;
    if(map[snakey[0]][snakex[0]+1] == '$'){
        map[snakey[0]][snakex[0]+1] = 'H';
        map[snakey[0]][snakex[0]] = 'X';
        for(m = 0;m < length;++ m){
                snakex[length - m] = snakex[length - m -1];
                snakey[length - m] = snakey[length - m -1];                     
            }           
        ++ snakex[0];
        ++ length;
        getfood(map);
        continue;
    }
    if(map[snakey[0]][snakex[0]+1] == '*' || map[snakey[0]][snakex[0]+1] == 'X'){
        length = 0;
        break;
    }
            for(m = 0;m < length - 1;++ m){
                map[snakey[0]][snakex[0]+1] = 'H';
                map[snakey[m]][snakex[m]] = map[snakey[m+1]][snakex[m+1]];                                  
            }   
            map[snakey[m]][snakex[m]] = ' ' ;
            map[snakey[m-1]][snakex[m-1]] ='X';
            for(m = 0;m < length - 1;++ m){
                snakex[length - m -1] = snakex[length - m -2];
                snakey[length - m -1] = snakey[length - m -2];  
            }           
            ++ snakex[0];                       
        }
        system("cls");
        for(m = 0;m<12;++m){
            printf("%s\n",map[m]); 
        }       
    }
    printf("GAME OVER!");
} 
