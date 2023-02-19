# C++常用函数

## algorithm

常用成员函数
1111111
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