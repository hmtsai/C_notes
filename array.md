# How to pass array to function
* Use []
```c
#include <stdio.h>
void display_1D(int a[], int rows)
{
    int i;
    printf("display_1D\n");
    for (i=0; i<rows; i++)
    {
        printf("%d \n", a[i]);
    }
}
void display_2D(int a[][2], int rows)
{
    int i;
    printf("display_2D\n");
    for (i=0; i<rows; i++)
    {
        printf("%d %d\n", a[i][0], a[i][1]);
    }
}
void display_3D(int a[][3][2], int rows)
{
    int i, j;
    printf("display_3D\n");
    for (i=0; i<rows; i++)
    {
        for (j=0; j<3; j++)
        {
            printf("%d %d\n", a[i][j][0], a[i][j][1]);
        }
        printf("\n");
    }
}

int main()
{
    printf("Hello, World!\n");

    int array_1d[3] = {1, 2, 3};
    int array_2d[3][2] = {{1,2},
                          {3,4},
                          {5,6}};
    int array_3d[2][3][2] = {
                                {{1,2},
                                 {3,4},
                                 {5,6}},
                                 
                                {{7,8},
                                 {9,10},
                                 {11,12}},
                                 
    };
    
    display_1D(array_1d, 3);
    display_2D(array_2d, 3);
    display_3D(array_3d, 2);
    return 0;
}
```
* The Result
```
$gcc -o main *.c
$main
Hello, World!
display_1D
1 
2 
3 
display_2D
1 2
3 4
5 6
display_3D
1 2
3 4
5 6

7 8
9 10
11 12
```
---
* use array pointer, (\*a)[2]

Here 'a' is the array pointer , point to a space with int[2]


```c
void display_2D_pointer(int (*a)[2], int rows)
{
    int i;
    printf("display_2D_pointer\n");
    for (i=0; i<rows; i++)
    {
        printf("%d %d\n", a[i][0], a[i][1]);
    }
}

 display_2D_pointer(array_2d, 3);
```

* Result
```
display_2D_pointer
1 2
3 4
5 6
```
---

* if use `(int *a[2])`, there is no ( ) around \*a.

Here 'a' is just an array of size 2, each element in the array is a integer pointer
```c
void display_array_element(int *a[2])
{
    printf("display_array_element \n");
    printf("a[0] 0x%x a[1] 0x%x\n", a[0], a[1]);
}

    int a;
    int b;
    int *array[2];
    array[0] = &a;
    array[1] = &b;
    
    printf("array[0] 0x%x\n", array[0]);
    printf("array[1] 0x%x\n", array[1]);
    display_array_element(array);
    
```

* Result
```
array[0] 0xa999894c
array[1] 0xa9998948
display_array_element 
a[0] 0xa999894c a[1] 0xa9998948
```
---
