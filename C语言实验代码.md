## C语言实验代码

``` c
\#include<stdio.h>

\#include<stdlib.h>

void findpath(int x, int y);

void printpath();

int judgepath(int x, int y);

int r, j;

int maze[10][10], path[10][10] = { 0 };

int count = 0;

void findpath(int x, int y)

{

  if (x == r - 1 && y == j - 1) {

​    path[x][y] = 1;

​    count++;

​    printpath();

​    path[x][y] = 0;

  }

  else if (judgepath(x, y)) {

​    path[x][y] = 1;

​    findpath(x - 1, y);

​    findpath(x + 1, y);

​    findpath(x, y - 1);

​    findpath(x, y + 1);

​    path[x][y] = 0;

  }

}

void printpath()

{

  int r1, j1;

  printf("%d\n", count);

  for(r1=0;r1<r;r1++)

​    for (j1 = 0; j1 < j; j1++) {

​      printf("%d", path[r1][j1]);

​      if (j1 != j - 1) printf(" ");

​      else printf("\n");

​    }

}

int judgepath(int x, int y)

{

  return (x >= 0 && x <= r - 1 && y >= 0 && y <= j - 1 && maze[x][y] == 1 && path[x][y]==0);

}

int main()

{

  int r1, j1;

  scanf("%d %d", &r, &j);

  for (r1 = 0; r1 < r; r1++)

​    for (j1 = 0; j1 < j; j1++) scanf("%d", &maze[r1][j1]);

  findpath(0,0);

  

  return 0;

}
```



