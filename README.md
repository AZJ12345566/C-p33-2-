# C-p33-2-
C语言学习笔记 p33 指针详解(2)
#incldude<stdio.h>
//数组指针-指针
int main()
{
    int* p=NULL;//整形指针-指向整形的指针-可以存放整形的地址
    char* pc-NULL;//pc是字符指针-指向字符的指针-可以存放字符的地址
    //数组指针-指向数组的指针-存放数组的指针
    int arr[10]={0};
    //arr-首元素的地址
    //&arr[0]-首元素地址
    //&arr-数组的地址
    int arr[10]={1,2,3,4,5,6,7,8,9,10};
    int(*p)[10]=&arr;//数组的地址要存起来
    //上面的p就是数组指针
    return 0;
}

int main()
{
    char* arr[5];
    char*(*pa)[5]=&arr;

    int arr2[10]={0};
    int (*pa2)[10]=&arr2;
    return 0;
}//这里pa是指针变量名字，*pa告诉我们他是一个指针，[5]告诉我们pa指向的数组是5个元素，char*告诉我们pa指向的数组元素是char*

int main()
{
    int arr[10]={1,2,3,4,5,6,7,8,9,10};
    int (*pa)[10]=&arr;
    int i=0;
    for(i=0;i<10;i++)
    {
        printf("%d"(*pa)[i]);
    }
    return 0;
}
//可以简化
int main()
{
    int arr[10]={1,2,3,4,5,6,7,8,9,10};
    int* p=arr;
    int i=0;
    for(i=0;i<10;i++)
    {
        printf("%d",*(p+i));
    }
    return 0;
}

//一般数组指针要用在二维数组以上才方便一点

void print1(int arr[3][5],int x,int y)
{
    int i=0;
    int j=0;
    for(i=0;i<x;i++)
    {
        for(j=0;j<y;j++)
        {
            printf("%d",arr[i][j]);
        }
        printf("\n");
    }
}

void print2(int (*p)[5],int x,int y)
{
    int i=0;
    for(i=0;i<x;i++)
    {
        int j=0;
        for(j=0;j<y;j++)
        {
            printf("%d",p[i][j]);
            printf("%d",*(p[i]+j));
            printf("%d",*(*(p+i)+j));
            printf("%d",(*(p+i))[j]);
        }
        printf("\n");
    }
}
int main()
{
    int ar[3][5]={{1,2,3,4,5},{2,3,4,5,6},{3,4,5,6,7}};
    print1(arr,3,5);
    print2(arr,3,5);//
    return 0;
}

int main())
{
    int arr[10]={1,2,3,4,5,6,7,8,9,10};
    int i=0;
    int* p=arr;
    for(i=0;i<10;i++)
    {
        printf("%d",p[i]);
        printf("%d",*(p+i));
        printf("%d",*(arr+i));
        printf("%d",arr[i]);//arr[i]==*(arr+i)==*(p+i)==p[i]
    }//输出全部一样
    return 0;
}

//int (*parr3[10]))[5]-parr3是一个数组，该数组有10个元素，每个元素是一个数组指针，该数组指针指向的数组有5个元素，每个元素是int
