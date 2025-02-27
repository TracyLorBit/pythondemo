# Python学习笔记 - 第三章：条件语句

## 1. if语句基础

条件语句让程序能够根据不同条件执行不同的代码：

```python
age = 18

if age >= 18:
    print("你已经成年了")
    print("可以申请驾照")
```

**注意：Python使用缩进来表示代码块，通常使用4个空格**

## 2. if-else语句

当条件不满足时执行另一段代码：

```python
temperature = 25

if temperature > 30:
    print("今天很热，注意防暑")
else:
    print("天气还不错")
```

## 3. if-elif-else语句

处理多个条件：

```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"你的成绩等级是: {grade}")
```

## 4. 嵌套if语句

在if语句内部再使用if语句：

```python
weather = "晴天"
temperature = 25

if weather == "晴天":
    if temperature > 20:
        print("适合户外活动")
    else:
        print("天气晴朗但有点凉")
else:
    print("不是晴天")
```

## 5. 复合条件

使用逻辑运算符组合多个条件：

```python
age = 20
has_license = True

# 使用 and
if age >= 18 and has_license:
    print("可以开车")

# 使用 or
day = "周末"
if day == "周六" or day == "周日":
    print("今天是休息日")

# 使用 not
is_raining = False
if not is_raining:
    print("没有下雨，可以出门")
```

## 6. 条件表达式（三元运算符）

简化的if-else语句：

```python
age = 20

# 传统写法
if age >= 18:
    status = "成年人"
else:
    status = "未成年"

# 条件表达式写法
status = "成年人" if age >= 18 else "未成年"
print(status)
```

## 7. 实用示例

### 判断闰年
```python
year = 2024

if (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0):
    print(f"{year}年是闰年")
else:
    print(f"{year}年不是闰年")
```

### 简单的登录验证
```python
username = input("请输入用户名: ")
password = input("请输入密码: ")

if username == "admin" and password == "123456":
    print("登录成功！")
elif username == "admin":
    print("密码错误！")
else:
    print("用户名不存在！")
```

### BMI计算器
```python
weight = float(input("请输入体重(kg): "))
height = float(input("请输入身高(m): "))

bmi = weight / (height ** 2)

if bmi < 18.5:
    category = "偏瘦"
elif bmi < 24:
    category = "正常"
elif bmi < 28:
    category = "偏胖"
else:
    category = "肥胖"

print(f"您的BMI指数是: {bmi:.2f}")
print(f"体重状况: {category}")
```

## 8. 常见错误

```python
# 错误：使用赋值运算符而不是比较运算符
x = 5
if x = 5:  # 错误！应该用 ==
    print("x等于5")

# 正确写法
if x == 5:
    print("x等于5")

# 错误：缩进不一致
if x > 0:
print("x是正数")  # 错误！缺少缩进

# 正确写法
if x > 0:
    print("x是正数")
```

## 练习题

1. 编写程序判断一个数是正数、负数还是零
2. 根据月份判断季节（3-5月春季，6-8月夏季，9-11月秋季，12-2月冬季）
3. 编写一个简单的计算器，根据用户输入的运算符进行不同的计算
4. 判断一个年份是否是21世纪（2001-2100年）

## 答案示例

```python
# 1. 判断正负数
num = float(input("请输入一个数: "))
if num > 0:
    print("这是正数")
elif num < 0:
    print("这是负数")
else:
    print("这是零")

# 2. 判断季节
month = int(input("请输入月份(1-12): "))
if 3 <= month <= 5:
    print("春季")
elif 6 <= month <= 8:
    print("夏季")
elif 9 <= month <= 11:
    print("秋季")
elif month == 12 or 1 <= month <= 2:
    print("冬季")
else:
    print("月份输入错误")
```