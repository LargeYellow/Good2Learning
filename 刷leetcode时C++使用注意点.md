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




## 结构体的使用

C++中结构体（struct）是一种自定义的数据类型，可以包含多个不同类型的成员变量，类似于类（class）。下面是一个示例代码，演示了如何定义和使用结构体：

```c++
#include <iostream>
#include <string>
using namespace std;

struct Student { // 定义一个名为Student的结构体
    string name;
    int age;
    float score;
};

int main() {
    Student s1; // 定义一个Student类型的变量s1
    s1.name = "Tom";
    s1.age = 18;
    s1.score = 95.5;
    cout << "Name: " << s1.name << endl;
    cout << "Age: " << s1.age << endl;
    cout << "Score: " << s1.score << endl;

    Student s2 = {"Jerry", 20, 90.5}; // 定义并初始化一个Student类型的变量s2
    cout << "Name: " << s2.name << endl;
    cout << "Age: " << s2.age << endl;
    cout << "Score: " << s2.score << endl;

    return 0;
}
```

在这个示例中，我们首先定义了一个名为Student的结构体，包含了三个成员变量：name、age和score。然后在main函数中，我们定义了一个Student类型的变量s1，为它的成员变量赋值，然后输出每个成员变量的值。接着我们定义了另一个Student类型的变量s2，并在定义时进行了初始化，然后同样输出每个成员变量的值。

需要注意的是，在定义结构体类型变量时，可以使用结构体名作为类型名。结构体的成员变量可以像普通变量一样使用，使用“结构体名.成员名”的方式访问。也可以使用“结构体变量名.成员名”的方式访问。

结构体还可以包含函数成员，类似于类中的成员函数。可以使用“结构体名.函数名”的方式调用结构体中的函数成员。

## 单向链表的创建

```c++
struct ListNode {
    int val;
    ListNode *next;
    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
    };
```

这个结构体定义了一个链表的节点类型，包含三个成员变量：val、next和三个构造函数。

- 成员变量val表示当前节点的值，是一个整型数。
- 成员变量next是一个指针类型，指向下一个节点的指针。因为这是一个单向链表，所以每个节点只需要保存它的下一个节点的指针。
- 构造函数分别对应没有参数、一个参数和两个参数的情况。它们的作用是用来创建链表节点的，可以根据需要传入节点的值和下一个节点的指针。

具体来说：

- 默认构造函数ListNode()创建一个val和next都为默认值的链表节点。
- 构造函数ListNode(int x)创建一个val为x，next为nullptr的链表节点。
- 构造函数ListNode(int x, ListNode *next)创建一个val为x，next为指向next所指节点的指针的链表节点。

这种结构体的创建方式常用于链表的实现。它定义了链表的节点类型，方便链表的创建、遍历和操作。例如，在链表的创建过程中，可以使用这个结构体类型定义节点，然后使用节点之间的指针来连接它们，从而构建整个链表。在链表的遍历和操作过程中，也可以使用这个结构体类型来表示链表的节点，从而进行各种操作。

要初始化链表并往里面存值，可以使用上面定义的`ListNode`结构体类型，以及该结构体中定义的构造函数。通常来说，我们会使用一个指向链表头节点的指针来表示整个链表，然后依次创建每个节点并将它们按顺序连接起来，从而构建整个链表。

下面是一个简单的示例代码，演示了如何创建一个包含3个节点的链表，其中每个节点的值依次为1、2和3：

```c++
ListNode *head = new ListNode(1); // 创建头节点，值为1
ListNode *node1 = new ListNode(2); // 创建第一个节点，值为2
ListNode *node2 = new ListNode(3); // 创建第二个节点，值为3

head->next = node1; // 将头节点的next指针指向第一个节点
node1->next = node2; // 将第一个节点的next指针指向第二个节点
node2->next = nullptr; // 将第二个节点的next指针设为nullptr，表示链表结束
```

