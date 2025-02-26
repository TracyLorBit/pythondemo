# Python学习笔记 - 第二章：运算符和表达式

## 1. 算术运算符

Python支持各种数学运算：

```python
# 基本算术运算
a = 10
b = 3

print(a + b)    # 加法: 13
print(a - b)    # 减法: 7
print(a * b)    # 乘法: 30
print(a / b)    # 除法: 3.3333...
print(a // b)   # 整除: 3
print(a % b)    # 取余: 1
print(a ** b)   # 幂运算: 1000
```

## 2. 比较运算符

比较运算符返回布尔值（True或False）：

```python
x = 5
y = 8

print(x == y)   # 等于: False
print(x != y)   # 不等于: True
print(x < y)    # 小于: True
print(x > y)    # 大于: False
print(x <= y)   # 小于等于: True
print(x >= y)   # 大于等于: False
```

## 3. 逻辑运算符

用于组合布尔表达式：

```python
age = 20
score = 85

# and: 两个条件都为真时返回True
print(age >= 18 and score >= 80)  # True

# or: 至少一个条件为真时返回True
print(age < 18 or score >= 90)    # False

# not: 取反
print(not age < 18)               # True
```

## 4. 赋值运算符

简化赋值操作：

```python
x = 10

x += 5    # 等于 x = x + 5, 结果: 15
x -= 3    # 等于 x = x - 3, 结果: 12
x *= 2    # 等于 x = x * 2, 结果: 24
x /= 4    # 等于 x = x / 4, 结果: 6.0
x //= 2   # 等于 x = x // 2, 结果: 3.0
x %= 2    # 等于 x = x % 2, 结果: 1.0
x **= 3   # 等于 x = x ** 3, 结果: 1.0
```

## 5. 成员运算符

检查元素是否在序列中：

```python
text = "Hello World"
numbers = [1, 2, 3, 4, 5]

print("H" in text)        # True
print("X" in text)        # False
print(3 in numbers)       # True
print(6 not in numbers)   # True
```

## 6. 运算符优先级

从高到低：

1. `**` (幂运算)
2. `*`, `/`, `//`, `%` (乘法、除法)
3. `+`, `-` (加法、减法)
4. `==`, `!=`, `<`, `>`, `<=`, `>=` (比较)
5. `not` (逻辑非)
6. `and` (逻辑与)
7. `or` (逻辑或)

```python
# 使用括号改变运算顺序
result1 = 2 + 3 * 4     # 14 (先乘后加)
result2 = (2 + 3) * 4   # 20 (先加后乘)
```

## 7. 类型转换

```python
# 字符串转数字
age_str = "25"
age_int = int(age_str)
print(age_int + 5)  # 30

# 数字转字符串
score = 95
score_str = str(score)
print("你的分数是: " + score_str)

# 转换为浮点数
height = float("1.75")
print(height)  # 1.75
```

## 练习题

1. 计算圆的面积（半径为5，π取3.14159）
2. 判断一个数是否是偶数
3. 比较两个数的大小，并输出较大的数
4. 计算复合利息：本金1000元，年利率5%，存3年后的总金额

## 答案示例

```python
# 1. 圆的面积
radius = 5
pi = 3.14159
area = pi * radius ** 2
print(f"圆的面积是: {area}")

# 2. 判断偶数
num = 8
if num % 2 == 0:
    print(f"{num} 是偶数")
else:
    print(f"{num} 是奇数")
```