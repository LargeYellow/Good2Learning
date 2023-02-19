# Pytorch 使用

## pytorch基础知识

### 1. 张量Tensor

- 分类：0维张量（标量）、1维张量（向量）、2维张量（矩阵）、3维张量（时间序列）、4维张量（图像）、5维张量（视频）
- 概念：一个数据容器，可以包含数据、字符串等

张量是一种特殊的数据结构，与数组和矩阵非常相似。在PyTorch中，我们使用张量对模型的输入和输出以及模型的参数进行编码。

张量类似于NumPy的`ndarray`，除了张量可以在 GPU 或其他硬件加速器上运行。事实上，张量和NumPy数组通常可以共享相同的底层内存，从而无需复制数据。

#### 1.1 初始化张量

**直接从数据创建，数据类型会被自动判断：**

```python
data = [[1, 2], [3, 4]]
x_data = torch.tensor(data)
print(f"Tensor from Data:\n {x_data} \n")
 
# Tensor from Data:
# tensor([[1, 2],
#         [3, 4]]) 
```

**从Numpy数组创建**

注意返回的张量和Numpy数组共享同一内存。对张量的修改将反映在Numpy数组中，反之亦然。

```python
np_array = np.array(data)
x_np = torch.from_numpy(np_array)
print(f"Tensor from Numpy:\n {x_np} \n")
 
# Tensor from Numpy:
# tensor([[1, 2],
#         [3, 4]], dtype=torch.int32)
```

根据另一个张量创建，新张量保留参数张量的属性（现状、数据类型）

```python
x_ones = torch.ones_like(x_data) # 保留原有张量的形状和数据类型
print(f"Ones Tensor: \n {x_ones} \n")
 
x_rand = torch.rand_like(x_data, dtype=torch.float) # 显式更改张量的数据类型
print(f"Random Tensor: \n {x_rand} \n")
 
# Ones Tensor:
#  tensor([[1, 1],
#         [1, 1]])
#
# Random Tensor:
#  tensor([[0.5890, 0.7234],
#         [0.7145, 0.5141]])
```

## 方法查询

```python
torch.is_tensor(obj)  # 如果obj 是一个pytorch张量，则返回True
torch.numels(input)->int  # 返回input张量中的元素个数
torch.eye(n, m=None, out=None)  # 返回一个对角线位置全为1，其它位置全为0的2维张量，n表示行数，m表示列数。
torch.from_numpy(ndarray) → Tensor # Numpy桥，将numpy.ndarray转换为pytorch的Tensor。返回的张量tensor和numpy的ndarray共享同一内存空间。修改一个会导致另外一个也被修改。返回的张量不能改变大小。
torch.linspace(start, end, steps=100, out=None) → Tensor # 返回一个1维张量，包含在区间start和end上均匀间隔的steps个点。输出1维张量的长度为steps。
torch.ones(*sizes, out=None) → Tensor # 返回一个全为1的张量，形状由可变参数sizes定义。
torch.rand(*sizes, out=None) → Tensor # 返回一个张量，包含了从区间[0,1)的均匀分布中抽取的一组随机数，形状由可变参数sizes定义。
torch.randn(*sizes, out=None) → Tensor # 返回一个张量，包含了从标准正态分布(均值为0，方差为1，即高斯白噪声)中抽取一组随机数，形状由可变参数sizes定义。 
torch.zeros(*sizes, out=None) → Tensor # 返回一个全为标量0的张量，形状由可变参数sizes定义。


torch.Tensor()
torch.tensor()
torch.ones_like()
torch.zeros()

torch.add()
torch.squeeze()
torch.rand_like()
torch.cat((A,B),n)  # 将张量A和张量B按维数n拼接

tensor.numpy()
tensor.size()
tensor.view()
tensor.reshape()
tensor.resize_()

```

