# C++常用函数

## algorithm

常用成员函数
### swap

用于交换两个变量的值，常用于交换数组中的两个数。

```c++
int main(){
	string s1 = "aaa", s2 = "bbb", s3 = "ccc";
	swap(s1,s2);
	cout << s1 << endl << s2; // s1 = "bbb", s2 = "aaa"
	return 0;
} 
```

### min,max

返回两个数中间的小的那个（大的那个）

```c++
int main(){
	string s1 = "aaa", s2 = "bbb", s3 = "ccc";
	string s4 = min(s1,s2);
	cout << s4; // aaa
	return 0;
} 
```

### max_element()与min_element()

**max_element（）与min_element（）**分别用来求最大元素和最小元素的**位置**。

接收参数：容器的首尾地址（迭代器）（可以是一个区间）

返回：最值元素的**地址**（迭代器），需要减去序列头以转换为下标

```c++
1) vector
vector<int> n;
int maxPosition = max_element(n.begin(),n.end()) - n.begin(); //最大值下标
int minPosition = min_element(n.begin(),n.end()) - n.begin();//最小值下标

2）普通数组
int a[]={1,2,3,4};
int maxPosition = max_element(a,a+2) - a; //最大值下标

int minPosition = min_element(a,a+2) - a;//最小值下标
```

### \*max_element()与\*min_element()

\*max_element（）与\*min_element（）分别用来求最大元素和最小元素的值。

接收参数：容器的首尾地址（迭代器）（可以是一个区间）

返回：最值元素的值

```c++
1) vector
vector<int> n;
int maxValue = *max_element(n.begin(),n.end()); //最大值
int minValue = *min_element(n.begin(),n.end());//最小值

2）普通数组
int a[]={1,2,3,4};
int maxValue = *max_element(a,a+2); //最大值
int minValue = *min_element(a,a+2); //最小值
```

## numeric

常用成员函数

### accumulate

- 函数共有四个参数，其中前三个为必须，第四个为非必需。
- 若不指定第四个参数，则默认对范围内的元素进行累加操作

```c++
accumulate(起始迭代器, 结束迭代器, 初始值, 自定义操作函数)
```

计算数组中的所有元素和

```c++
#include <iostream>
#include <vector>
#include <numeric>
using namespace std;

int main() {
    vector<int> arr{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    int sum = accumulate(arr.begin(), arr.end(), 0); // 初值0 + (1 + 2 + 3 + 4 +... + 10)
    cout << sum << endl;	// 输出55
    return 0;
}
```

## 其它



