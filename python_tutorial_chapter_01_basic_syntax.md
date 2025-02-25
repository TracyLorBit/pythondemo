# Python学习笔记 - 第一章：基础语法

## 1. Python简介

Python是一种解释型、面向对象、动态数据类型的高级程序设计语言。它简洁易读，非常适合初学者学习编程。

## 2. 变量和数据类型

### 2.1 变量定义
在Python中，变量无需声明类型，直接赋值即可：

```python
# 整数
age = 25
print(age)  # 输出: 25

# 字符串
name = "张三"
print(name)  # 输出: 张三

# 浮点数
height = 1.75
print(height)  # 输出: 1.75

# 布尔值
is_student = True
print(is_student)  # 输出: True
```

### 2.2 基本数据类型

1. **整数 (int)**: 表示整数，如 10, -5, 0
2. **浮点数 (float)**: 表示小数，如 3.14, -0.5
3. **字符串 (str)**: 表示文本，用引号包围，如 "hello", '你好'
4. **布尔值 (bool)**: 表示真假，只有 True 和 False

### 2.3 查看变量类型

```python
x = 10
print(type(x))  # 输出: <class 'int'>

y = "Hello"
print(type(y))  # 输出: <class 'str'>
```

## 3. 输入和输出

### 3.1 输出 - print()函数

```python
print("Hello, World!")  # 输出文本
print(123)              # 输出数字
print("我的年龄是", 25)  # 输出多个值
```

### 3.2 输入 - input()函数

```python
name = input("请输入您的姓名: ")
print("您好,", name)

# 注意：input()函数总是返回字符串
age_str = input("请输入您的年龄: ")
age = int(age_str)  # 转换为整数
print("您的年龄是", age)
```

## 4. 注释

```python
# 这是单行注释

"""
这是多行注释
可以写多行
"""

'''
这也是多行注释
也可以用单引号
'''
```

## 练习题

1. 定义一个变量存储你的姓名，并打印出来
2. 使用input()函数获取用户输入的两个数字，并计算它们的和
3. 定义不同类型的变量，并使用type()函数查看它们的类型

## 下一章预告
下一章我们将学习Python的运算符和表达式。