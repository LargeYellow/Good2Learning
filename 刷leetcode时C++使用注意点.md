# 刷leetcode时C++使用注意点

## 如何创建不定长度的数组

在C++中，规定创建数组为如下格式：

```
数据类型 数组名[常量表达式]
```

如果数组长度不确定，即不能用这种方式创建数组

***解决方法1：new动态分配存储空间***

new存放时存入首地址并申请动态空间，从而将不定长度的数组存入。

格式： 数据类型 *数组名 = new 数据类型[动态长度]

```C++
int n；
int *a=new int[n];  //注意定义的是指针
 
//之后便可按数组方式调用  例如：输入输出
for(int i=0;i<n;i++)
{
    cin>>a[i];
    cout<<a[i];
}
```

注意：复杂程序中往往在部分结束时要释放存储空间，使用new创建动态空间，需用delete专门释放new的空间，new不会由系统默认释放。

```c++
delete a;  //释放单个对象
delete [] a;  //释放对象数组
```

***解决方法2：vector申明动态数组***

vector向量也可声明动态数组，在头文件<vector>中

格式：vector<数据类型> 数组名(动态长度)；

```c++
#include<vector>
 
int n;
cin>>n;
vector<int> a(n);
//之后便可按数组方式调用  例如：输入输出
for(int i=0;i<n;i++)
{
    cin>>a[i];
    cout<<a[i];
}
```

优点：vector不仅可以做常规的数组操作，还可以进行特殊的操作，例如：

```c++
a.push_back(b)  //将b接至数组末尾
a.begin()  //数组起始
a.erase(m)  //擦除第m个元素
a.insert(m,b)  //将b插入a[m]的位置
```

## 创建一维、二维vector

1. 创建一维vector

   ```C++
   vector<int> a(4,2); //将含有4个数据的一维动态数组初始为2
   ```

2. 创建二维vector

   ```c++
   vector<vector<int>> v1(r, vector<int>(c));  //创建一个r行，c列的vector
   vector<vector<int>> v2(r, vector<int>(c, 0)); //创建一个r行，c列，初始值为0的vector
   ```

   