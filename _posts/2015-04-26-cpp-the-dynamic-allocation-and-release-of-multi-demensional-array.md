---
layout: post
title: C++：多维数组的动态分配（new）和释放（delete）
author: Jude
category: c++
tags: [new, delete]
---


对于简单的一维数组动态内存分配和释放，相信大家都是知道的，不过还是举个例子吧：

```c++
int *array1D;
//假定数组长度为m
//动态分配空间
array1D = new int [m];
//释放
delete [] array1D;
```
但是，对于多维数组动态分配，大家可能不太熟悉。下面以常见的二维和三维数组为例来说明：

- 二维数组的动态分配和释放

```c++
int **array2D;
//假定数组第一维长度为m， 第二维长度为n
//动态分配空间
array2D = new int *[m];
for( int i=0; i<m; i++ )
{
    array2D[i] = new int [n]  ;
}
//释放
for( int i=0; i<m; i++ )
{
    delete [] arrar2D[i];
}
delete array2D;
```
P.S. 事实上二维数组空间的释放还可以更简单地用：delete [] array2D;

- 三维数组的动态分配和释放

```C++
int ***array3D;
//假定数组第一维为m， 第二维为n， 第三维为h
//动态分配空间
array3D = new int **[m];
for( int i=0; i<m; i++ )
{
    array3D[i] = new int *[n];
    for( int j=0; j<n; j++ )
    {
         array3D[i][j] = new int [h];
    }
}
//释放
for( int i=0; i<m; i++ )
{
    for( int j=0; j<n; j++ )
    {
         delete array3D[i][j];
    }
    delete array3D[i];
}
delete array3D;
```




