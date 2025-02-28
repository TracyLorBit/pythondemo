# Python学习笔记 - 第四章：循环语句

## 1. for循环基础

for循环用于遍历序列（如列表、字符串、范围等）：

```python
# 遍历字符串
name = "Python"
for char in name:
    print(char)

# 遍历列表
fruits = ["苹果", "香蕉", "橙子"]
for fruit in fruits:
    print(f"我喜欢吃{fruit}")
```

## 2. range()函数

range()函数生成数字序列，常与for循环搭配使用：

```python
# range(n): 从0到n-1
for i in range(5):
    print(i)  # 输出: 0, 1, 2, 3, 4

# range(start, stop): 从start到stop-1
for i in range(2, 8):
    print(i)  # 输出: 2, 3, 4, 5, 6, 7

# range(start, stop, step): 指定步长
for i in range(0, 10, 2):
    print(i)  # 输出: 0, 2, 4, 6, 8

# 倒序
for i in range(10, 0, -1):
    print(i)  # 输出: 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

## 3. while循环

当条件为真时重复执行代码块：

```python
# 基本while循环
count = 0
while count < 5:
    print(f"当前计数: {count}")
    count += 1

# 用户输入控制的循环
password = ""
while password != "123456":
    password = input("请输入密码: ")
    if password != "123456":
        print("密码错误，请重试")
print("密码正确！")
```

## 4. 循环控制语句

### break语句 - 跳出循环
```python
# 在for循环中使用break
for i in range(10):
    if i == 5:
        break
    print(i)  # 输出: 0, 1, 2, 3, 4

# 在while循环中使用break
while True:
    user_input = input("输入'quit'退出: ")
    if user_input == "quit":
        break
    print(f"你输入了: {user_input}")
```

### continue语句 - 跳过当前迭代
```python
# 跳过偶数
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)  # 输出: 1, 3, 5, 7, 9

# 跳过空输入
while True:
    name = input("请输入姓名 (输入'done'结束): ")
    if name == "done":
        break
    if name == "":
        continue
    print(f"你好, {name}!")
```

## 5. 嵌套循环

循环内部再包含循环：

```python
# 打印乘法表
for i in range(1, 10):
    for j in range(1, i + 1):
        print(f"{j}×{i}={i*j}", end="\t")
    print()  # 换行

# 二维列表遍历
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for row in matrix:
    for num in row:
        print(num, end=" ")
    print()
```

## 6. enumerate()函数

获取索引和值：

```python
fruits = ["苹果", "香蕉", "橙子"]

# 传统方法
for i in range(len(fruits)):
    print(f"{i}: {fruits[i]}")

# 使用enumerate（推荐）
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# 指定起始索引
for index, fruit in enumerate(fruits, start=1):
    print(f"{index}: {fruit}")
```

## 7. zip()函数

同时遍历多个序列：

```python
names = ["张三", "李四", "王五"]
ages = [25, 30, 28]
cities = ["北京", "上海", "广州"]

for name, age, city in zip(names, ages, cities):
    print(f"{name}, {age}岁, 来自{city}")
```

## 8. 列表推导式

创建列表的简洁方法：

```python
# 传统方法
squares = []
for i in range(10):
    squares.append(i ** 2)

# 列表推导式
squares = [i ** 2 for i in range(10)]
print(squares)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# 带条件的列表推导式
even_squares = [i ** 2 for i in range(10) if i % 2 == 0]
print(even_squares)  # [0, 4, 16, 36, 64]

# 处理字符串
words = ["hello", "world", "python"]
lengths = [len(word) for word in words]
print(lengths)  # [5, 5, 6]
```

## 9. 实用示例

### 计算阶乘
```python
def factorial(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

print(f"5的阶乘是: {factorial(5)}")
```

### 猜数字游戏
```python
import random

secret_number = random.randint(1, 100)
attempts = 0

while True:
    attempts += 1
    guess = int(input("猜一个1-100之间的数字: "))
    
    if guess < secret_number:
        print("太小了！")
    elif guess > secret_number:
        print("太大了！")
    else:
        print(f"恭喜！你用{attempts}次猜中了{secret_number}")
        break
```

### 统计字符出现次数
```python
text = "hello world"
char_count = {}

for char in text:
    if char in char_count:
        char_count[char] += 1
    else:
        char_count[char] = 1

for char, count in char_count.items():
    print(f"'{char}': {count}")
```

## 10. 无限循环与注意事项

```python
# 危险：无限循环
# while True:
#     print("这会一直运行下去")

# 安全的无限循环
count = 0
while True:
    print(f"循环次数: {count}")
    count += 1
    if count >= 5:  # 设置退出条件
        break
```

## 练习题

1. 使用for循环计算1到100的和
2. 打印1-20中的所有质数
3. 编写程序找出列表中的最大值和最小值
4. 使用while循环实现简单的菜单系统
5. 创建一个程序，统计用户输入文本中每个单词的出现次数

## 答案示例

```python
# 1. 计算1到100的和
total = 0
for i in range(1, 101):
    total += i
print(f"1到100的和是: {total}")

# 或者使用内置函数
print(f"1到100的和是: {sum(range(1, 101))}")

# 2. 打印质数
for num in range(2, 21):
    is_prime = True
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            is_prime = False
            break
    if is_prime:
        print(num)
```