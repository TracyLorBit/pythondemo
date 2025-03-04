# Python学习笔记 - 第五章：列表和元组

## 1. 列表(List)基础

列表是Python中最常用的数据结构，可以存储多个有序的元素：

```python
# 创建列表
fruits = ["苹果", "香蕉", "橙子"]
numbers = [1, 2, 3, 4, 5]
mixed = ["hello", 42, 3.14, True]
empty_list = []

print(fruits)    # ['苹果', '香蕉', '橙子']
print(len(fruits))  # 3 (列表长度)
```

## 2. 列表访问和索引

```python
fruits = ["苹果", "香蕉", "橙子", "葡萄"]

# 正向索引 (从0开始)
print(fruits[0])   # 苹果 (第一个元素)
print(fruits[1])   # 香蕉
print(fruits[3])   # 葡萄 (最后一个元素)

# 负向索引 (从-1开始)
print(fruits[-1])  # 葡萄 (最后一个元素)
print(fruits[-2])  # 橙子 (倒数第二个)

# 切片操作
print(fruits[1:3])    # ['香蕉', '橙子'] (索引1到2)
print(fruits[:2])     # ['苹果', '香蕉'] (开头到索引1)
print(fruits[2:])     # ['橙子', '葡萄'] (索引2到结尾)
print(fruits[-2:])    # ['橙子', '葡萄'] (最后两个)
print(fruits[::2])    # ['苹果', '橙子'] (步长为2)
print(fruits[::-1])   # ['葡萄', '橙子', '香蕉', '苹果'] (反转)
```

## 3. 列表修改

```python
fruits = ["苹果", "香蕉", "橙子"]

# 修改单个元素
fruits[1] = "芒果"
print(fruits)  # ['苹果', '芒果', '橙子']

# 修改多个元素
fruits[0:2] = ["西瓜", "草莓"]
print(fruits)  # ['西瓜', '草莓', '橙子']
```

## 4. 列表方法

### 添加元素
```python
fruits = ["苹果", "香蕉"]

# append() - 在末尾添加单个元素
fruits.append("橙子")
print(fruits)  # ['苹果', '香蕉', '橙子']

# insert() - 在指定位置插入元素
fruits.insert(1, "芒果")
print(fruits)  # ['苹果', '芒果', '香蕉', '橙子']

# extend() - 添加多个元素
fruits.extend(["葡萄", "桃子"])
print(fruits)  # ['苹果', '芒果', '香蕉', '橙子', '葡萄', '桃子']
```

### 删除元素
```python
fruits = ["苹果", "香蕉", "橙子", "香蕉"]

# remove() - 删除第一个匹配的元素
fruits.remove("香蕉")
print(fruits)  # ['苹果', '橙子', '香蕉']

# pop() - 删除并返回指定位置的元素
last_fruit = fruits.pop()      # 删除最后一个
print(last_fruit)              # 香蕉
print(fruits)                  # ['苹果', '橙子']

first_fruit = fruits.pop(0)    # 删除第一个
print(first_fruit)             # 苹果

# clear() - 清空列表
fruits.clear()
print(fruits)  # []

# del 语句 - 删除元素或整个列表
numbers = [1, 2, 3, 4, 5]
del numbers[2]    # 删除索引2的元素
print(numbers)    # [1, 2, 4, 5]

del numbers[1:3]  # 删除索引1到2的元素
print(numbers)    # [1, 5]
```

### 查找和统计
```python
numbers = [1, 3, 5, 3, 7, 3, 9]

# count() - 统计元素出现次数
print(numbers.count(3))  # 3

# index() - 查找元素第一次出现的位置
print(numbers.index(5))  # 2

# in 操作符 - 检查元素是否存在
print(5 in numbers)      # True
print(10 in numbers)     # False
```

### 排序和反转
```python
numbers = [3, 1, 4, 1, 5, 9, 2]

# sort() - 原地排序
numbers.sort()
print(numbers)  # [1, 1, 2, 3, 4, 5, 9]

# 降序排序
numbers.sort(reverse=True)
print(numbers)  # [9, 5, 4, 3, 2, 1, 1]

# sorted() - 返回新的排序列表
original = [3, 1, 4, 1, 5]
sorted_list = sorted(original)
print(original)     # [3, 1, 4, 1, 5] (原列表不变)
print(sorted_list)  # [1, 1, 3, 4, 5]

# reverse() - 反转列表
numbers = [1, 2, 3, 4, 5]
numbers.reverse()
print(numbers)  # [5, 4, 3, 2, 1]
```

## 5. 元组(Tuple)基础

元组与列表类似，但是不可变(immutable)：

```python
# 创建元组
coordinates = (3, 5)
colors = ("红", "绿", "蓝")
single_item = (42,)  # 单元素元组需要逗号
empty_tuple = ()

# 不使用括号也可以创建元组
point = 10, 20
print(point)  # (10, 20)
print(type(point))  # <class 'tuple'>
```

## 6. 元组操作

```python
colors = ("红", "绿", "蓝", "黄")

# 访问元素 (与列表相同)
print(colors[0])    # 红
print(colors[-1])   # 黄
print(colors[1:3])  # ('绿', '蓝')

# 元组方法
print(colors.count("红"))  # 1
print(colors.index("蓝"))  # 2

# 元组解包
point = (3, 5)
x, y = point
print(f"x = {x}, y = {y}")  # x = 3, y = 5

# 多个变量赋值
name, age, city = ("张三", 25, "北京")
print(f"{name}, {age}岁, 来自{city}")
```

## 7. 列表 vs 元组

| 特性 | 列表 | 元组 |
|------|------|------|
| 可变性 | 可变 | 不可变 |
| 语法 | `[1, 2, 3]` | `(1, 2, 3)` |
| 性能 | 较慢 | 较快 |
| 用途 | 数据会变化 | 数据固定 |

```python
# 列表适合：购物清单、学生成绩等可变数据
shopping_list = ["牛奶", "面包", "鸡蛋"]
shopping_list.append("苹果")  # 可以添加

# 元组适合：坐标、RGB颜色值等固定数据
rgb_color = (255, 128, 0)
# rgb_color[0] = 200  # 错误！元组不可修改
```

## 8. 实用技巧

### 列表复制
```python
original = [1, 2, 3]

# 浅拷贝
copy1 = original.copy()
copy2 = original[:]
copy3 = list(original)

# 证明是不同的列表
copy1.append(4)
print(original)  # [1, 2, 3] (原列表不变)
print(copy1)     # [1, 2, 3, 4]
```

### 列表合并
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# 使用 + 操作符
combined = list1 + list2
print(combined)  # [1, 2, 3, 4, 5, 6]

# 使用 * 操作符重复
repeated = [0] * 5
print(repeated)  # [0, 0, 0, 0, 0]
```

### 二维列表
```python
# 创建二维列表
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# 访问元素
print(matrix[1][2])  # 6 (第2行第3列)

# 遍历二维列表
for row in matrix:
    for item in row:
        print(item, end=" ")
    print()
```

## 练习题

1. 创建一个包含5个学生成绩的列表，计算平均分
2. 从列表中删除所有的重复元素
3. 将两个排序好的列表合并成一个排序列表
4. 使用元组存储学生信息(姓名, 年龄, 成绩)，并按成绩排序
5. 实现一个简单的购物车功能(添加、删除、查看商品)

## 答案示例

```python
# 1. 计算平均分
scores = [85, 92, 78, 96, 88]
average = sum(scores) / len(scores)
print(f"平均分: {average:.2f}")

# 2. 删除重复元素
numbers = [1, 2, 2, 3, 4, 4, 5]
unique_numbers = list(set(numbers))  # 使用set去重
print(unique_numbers)

# 或者保持原顺序
unique_ordered = []
for num in numbers:
    if num not in unique_ordered:
        unique_ordered.append(num)
print(unique_ordered)
```