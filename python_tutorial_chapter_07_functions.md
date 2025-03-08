# Python学习笔记 - 第七章：函数

## 1. 函数基础

函数是组织好的、可重复使用的代码块：

```python
# 定义函数
def greet():
    print("你好，世界！")

# 调用函数
greet()  # 输出: 你好，世界！

# 带参数的函数
def greet_person(name):
    print(f"你好，{name}！")

greet_person("张三")  # 输出: 你好，张三！

# 带返回值的函数
def add_numbers(a, b):
    result = a + b
    return result

sum_result = add_numbers(5, 3)
print(sum_result)  # 输出: 8
```

## 2. 函数参数

### 位置参数
```python
def introduce(name, age, city):
    print(f"我叫{name}，今年{age}岁，来自{city}")

introduce("张三", 25, "北京")  # 按顺序传递参数
```

### 关键字参数
```python
def introduce(name, age, city):
    print(f"我叫{name}，今年{age}岁，来自{city}")

# 使用关键字参数，可以不按顺序
introduce(city="上海", name="李四", age=30)
introduce("王五", city="广州", age=28)  # 混合使用
```

### 默认参数
```python
def greet(name, greeting="你好"):
    print(f"{greeting}，{name}！")

greet("张三")           # 输出: 你好，张三！
greet("李四", "早上好")  # 输出: 早上好，李四！

# 默认参数的陷阱
def add_item(item, target_list=[]):  # 错误！不要使用可变对象作为默认参数
    target_list.append(item)
    return target_list

# 正确的写法
def add_item(item, target_list=None):
    if target_list is None:
        target_list = []
    target_list.append(item)
    return target_list
```

### 可变参数
```python
# *args - 接收任意数量的位置参数
def sum_all(*numbers):
    total = 0
    for num in numbers:
        total += num
    return total

print(sum_all(1, 2, 3))        # 6
print(sum_all(1, 2, 3, 4, 5))  # 15

# **kwargs - 接收任意数量的关键字参数
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

print_info(name="张三", age=25, city="北京")
# 输出:
# name: 张三
# age: 25
# city: 北京

# 混合使用
def complex_function(required_arg, *args, **kwargs):
    print(f"必需参数: {required_arg}")
    print(f"位置参数: {args}")
    print(f"关键字参数: {kwargs}")

complex_function("必须的", 1, 2, 3, name="张三", age=25)
```

## 3. 函数作用域和变量

```python
# 全局变量
global_var = "我是全局变量"

def scope_demo():
    # 局部变量
    local_var = "我是局部变量"
    print(local_var)
    print(global_var)  # 可以访问全局变量

scope_demo()
# print(local_var)  # 错误！无法访问局部变量

# 修改全局变量
counter = 0

def increment():
    global counter  # 声明要修改全局变量
    counter += 1

increment()
print(counter)  # 1

# nonlocal关键字 - 用于嵌套函数
def outer_function():
    x = 10
    
    def inner_function():
        nonlocal x  # 修改外层函数的变量
        x += 5
        print(f"内层函数中x = {x}")
    
    inner_function()
    print(f"外层函数中x = {x}")

outer_function()
```

## 4. 返回值

```python
# 返回单个值
def square(x):
    return x * x

# 返回多个值
def calculate(a, b):
    add_result = a + b
    sub_result = a - b
    mul_result = a * b
    return add_result, sub_result, mul_result

# 接收多个返回值
sum_val, diff_val, prod_val = calculate(10, 5)
print(f"和: {sum_val}, 差: {diff_val}, 积: {prod_val}")

# 或者作为元组接收
results = calculate(10, 5)
print(results)  # (15, 5, 50)

# 没有return语句的函数返回None
def no_return():
    print("这个函数没有返回值")

result = no_return()
print(result)  # None
```

## 5. 高阶函数

### 函数作为参数
```python
def apply_operation(x, y, operation):
    return operation(x, y)

def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

print(apply_operation(5, 3, add))      # 8
print(apply_operation(5, 3, multiply)) # 15

# 使用lambda函数
print(apply_operation(5, 3, lambda x, y: x - y))  # 2
```

### 内置高阶函数
```python
numbers = [1, 2, 3, 4, 5]

# map() - 对每个元素应用函数
squares = list(map(lambda x: x**2, numbers))
print(squares)  # [1, 4, 9, 16, 25]

# filter() - 过滤元素
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4]

# sorted() - 自定义排序
students = [
    {"name": "张三", "score": 85},
    {"name": "李四", "score": 92},
    {"name": "王五", "score": 78}
]

# 按分数排序
sorted_students = sorted(students, key=lambda s: s["score"])
print(sorted_students)
```

## 6. 装饰器基础

```python
# 简单装饰器
def my_decorator(func):
    def wrapper():
        print("函数执行前")
        func()
        print("函数执行后")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# 输出:
# 函数执行前
# Hello!
# 函数执行后

# 带参数的装饰器
def timing_decorator(func):
    import time
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"函数 {func.__name__} 执行时间: {end_time - start_time:.4f}秒")
        return result
    return wrapper

@timing_decorator
def slow_function():
    import time
    time.sleep(1)
    return "完成"

result = slow_function()
```

## 7. 递归函数

```python
# 计算阶乘
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # 120

# 斐波那契数列
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n-1) + fibonacci(n-2)

for i in range(10):
    print(fibonacci(i), end=" ")  # 0 1 1 2 3 5 8 13 21 34

# 优化的斐波那契（使用记忆化）
def fibonacci_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fibonacci_memo(n-1, memo) + fibonacci_memo(n-2, memo)
    return memo[n]
```

## 8. 匿名函数(lambda)

```python
# 基本语法: lambda 参数: 表达式
square = lambda x: x**2
print(square(5))  # 25

# 多个参数
add = lambda x, y: x + y
print(add(3, 4))  # 7

# 在高阶函数中使用
numbers = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x**2, numbers))
print(squares)  # [1, 4, 9, 16, 25]

# 条件表达式
max_func = lambda x, y: x if x > y else y
print(max_func(10, 5))  # 10

# 排序中使用
students = [("张三", 85), ("李四", 92), ("王五", 78)]
students.sort(key=lambda student: student[1])  # 按分数排序
print(students)
```

## 9. 实用函数示例

### 计算器函数
```python
def calculator():
    def add(x, y):
        return x + y
    
    def subtract(x, y):
        return x - y
    
    def multiply(x, y):
        return x * y
    
    def divide(x, y):
        if y == 0:
            return "错误：除数不能为零"
        return x / y
    
    operations = {
        '+': add,
        '-': subtract,
        '*': multiply,
        '/': divide
    }
    
    return operations

calc = calculator()
print(calc['+'](10, 5))  # 15
print(calc['/'](10, 0))  # 错误：除数不能为零
```

### 密码验证器
```python
def validate_password(password):
    """验证密码强度"""
    if len(password) < 8:
        return False, "密码长度至少8位"
    
    has_upper = any(c.isupper() for c in password)
    has_lower = any(c.islower() for c in password)
    has_digit = any(c.isdigit() for c in password)
    
    if not (has_upper and has_lower and has_digit):
        return False, "密码必须包含大写字母、小写字母和数字"
    
    return True, "密码强度合格"

is_valid, message = validate_password("Password123")
print(f"验证结果: {is_valid}, 信息: {message}")
```

### 文本处理函数
```python
def word_count(text):
    """统计单词频率"""
    words = text.lower().split()
    word_freq = {}
    for word in words:
        # 去除标点符号
        clean_word = ''.join(c for c in word if c.isalnum())
        if clean_word:
            word_freq[clean_word] = word_freq.get(clean_word, 0) + 1
    return word_freq

def most_common_words(text, n=5):
    """找出最常见的n个单词"""
    freq = word_count(text)
    sorted_words = sorted(freq.items(), key=lambda x: x[1], reverse=True)
    return sorted_words[:n]

text = "Python is great. Python is powerful. Python is easy to learn."
print(most_common_words(text, 3))
```

## 10. 函数文档字符串

```python
def calculate_bmi(weight, height):
    """
    计算身体质量指数(BMI)
    
    参数:
    weight (float): 体重，单位为千克
    height (float): 身高，单位为米
    
    返回:
    float: BMI值
    str: BMI分类
    
    示例:
    >>> calculate_bmi(70, 1.75)
    (22.86, '正常')
    """
    bmi = weight / (height ** 2)
    
    if bmi < 18.5:
        category = "偏瘦"
    elif bmi < 24:
        category = "正常"
    elif bmi < 28:
        category = "偏胖"
    else:
        category = "肥胖"
    
    return round(bmi, 2), category

# 查看函数文档
print(calculate_bmi.__doc__)
help(calculate_bmi)
```

## 练习题

1. 编写一个函数计算两个数的最大公约数
2. 创建一个函数生成指定长度的随机密码
3. 实现一个简单的银行账户类（使用函数模拟）
4. 编写一个装饰器来记录函数的调用次数
5. 创建一个递归函数来遍历文件夹结构

## 答案示例

```python
# 1. 最大公约数（欧几里得算法）
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

print(gcd(48, 18))  # 6

# 2. 随机密码生成器
import random
import string

def generate_password(length=8, include_symbols=True):
    chars = string.ascii_letters + string.digits
    if include_symbols:
        chars += "!@#$%^&*"
    
    password = ''.join(random.choice(chars) for _ in range(length))
    return password

print(generate_password(12))  # 生成12位密码

# 3. 银行账户模拟
def create_account(initial_balance=0):
    balance = initial_balance
    
    def deposit(amount):
        nonlocal balance
        if amount > 0:
            balance += amount
            return f"存款成功，当前余额: {balance}"
        return "存款金额必须大于0"
    
    def withdraw(amount):
        nonlocal balance
        if amount > balance:
            return "余额不足"
        if amount > 0:
            balance -= amount
            return f"取款成功，当前余额: {balance}"
        return "取款金额必须大于0"
    
    def get_balance():
        return balance
    
    return {
        'deposit': deposit,
        'withdraw': withdraw,
        'balance': get_balance
    }

# 使用示例
account = create_account(1000)
print(account['deposit'](500))   # 存款成功，当前余额: 1500
print(account['withdraw'](200))  # 取款成功，当前余额: 1300
print(account['balance']())      # 1300
```