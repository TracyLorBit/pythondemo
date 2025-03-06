# Python学习笔记 - 第六章：字典和集合

## 1. 字典(Dictionary)基础

字典是一种键值对的数据结构，类似于现实中的词典：

```python
# 创建字典
student = {
    "姓名": "张三",
    "年龄": 20,
    "专业": "计算机科学",
    "成绩": 85.5
}

# 空字典
empty_dict = {}
another_empty = dict()

print(student)  # {'姓名': '张三', '年龄': 20, '专业': '计算机科学', '成绩': 85.5}
print(len(student))  # 4
```

## 2. 字典访问和修改

```python
student = {"姓名": "张三", "年龄": 20, "专业": "计算机科学"}

# 访问值
print(student["姓名"])  # 张三
print(student.get("年龄"))  # 20
print(student.get("电话", "未提供"))  # 未提供 (默认值)

# 修改值
student["年龄"] = 21
print(student["年龄"])  # 21

# 添加新键值对
student["电话"] = "13800138000"
print(student)

# 删除键值对
del student["电话"]  # 使用del语句
grade = student.pop("专业")  # 使用pop方法，返回被删除的值
print(f"删除的专业: {grade}")
```

## 3. 字典方法

```python
student = {"姓名": "张三", "年龄": 20, "专业": "计算机科学"}

# keys() - 获取所有键
print(student.keys())    # dict_keys(['姓名', '年龄', '专业'])
print(list(student.keys()))  # ['姓名', '年龄', '专业']

# values() - 获取所有值
print(student.values())  # dict_values(['张三', 20, '计算机科学'])
print(list(student.values()))  # ['张三', 20, '计算机科学']

# items() - 获取所有键值对
print(student.items())   # dict_items([('姓名', '张三'), ('年龄', 20), ('专业', '计算机科学')])

# update() - 更新字典
new_info = {"成绩": 88, "年龄": 21}
student.update(new_info)
print(student)

# clear() - 清空字典
temp_dict = {"a": 1, "b": 2}
temp_dict.clear()
print(temp_dict)  # {}
```

## 4. 字典遍历

```python
student = {"姓名": "张三", "年龄": 20, "专业": "计算机科学", "成绩": 85}

# 遍历键
for key in student:
    print(key)

# 遍历键(显式)
for key in student.keys():
    print(key)

# 遍历值
for value in student.values():
    print(value)

# 遍历键值对
for key, value in student.items():
    print(f"{key}: {value}")
```

## 5. 字典推导式

```python
# 基本字典推导式
squares = {x: x**2 for x in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# 带条件的字典推导式
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
print(even_squares)  # {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}

# 从两个列表创建字典
names = ["张三", "李四", "王五"]
ages = [20, 25, 30]
name_age = {name: age for name, age in zip(names, ages)}
print(name_age)  # {'张三': 20, '李四': 25, '王五': 30}
```

## 6. 嵌套字典

```python
# 学生信息系统
students = {
    "001": {
        "姓名": "张三",
        "年龄": 20,
        "成绩": {"数学": 85, "英语": 78, "计算机": 92}
    },
    "002": {
        "姓名": "李四",
        "年龄": 19,
        "成绩": {"数学": 90, "英语": 85, "计算机": 88}
    }
}

# 访问嵌套数据
print(students["001"]["姓名"])  # 张三
print(students["001"]["成绩"]["数学"])  # 85

# 计算平均成绩
for student_id, info in students.items():
    scores = info["成绩"].values()
    average = sum(scores) / len(scores)
    print(f"{info['姓名']}的平均成绩: {average:.2f}")
```

## 7. 集合(Set)基础

集合是无序且不重复的元素集合：

```python
# 创建集合
colors = {"红", "绿", "蓝"}
numbers = set([1, 2, 3, 4, 5])
empty_set = set()  # 注意：{}创建的是空字典，不是空集合

print(colors)   # {'红', '绿', '蓝'}
print(len(colors))  # 3

# 集合自动去重
duplicate_numbers = {1, 2, 2, 3, 3, 4}
print(duplicate_numbers)  # {1, 2, 3, 4}
```

## 8. 集合操作

```python
# 添加元素
colors = {"红", "绿", "蓝"}
colors.add("黄")
print(colors)  # {'红', '绿', '蓝', '黄'}

# 添加多个元素
colors.update(["紫", "橙"])
print(colors)

# 删除元素
colors.remove("橙")  # 如果元素不存在会报错
colors.discard("粉")  # 如果元素不存在不会报错
print(colors)

# 清空集合
temp_set = {1, 2, 3}
temp_set.clear()
print(temp_set)  # set()
```

## 9. 集合运算

```python
set1 = {1, 2, 3, 4, 5}
set2 = {4, 5, 6, 7, 8}

# 并集 (所有元素)
union = set1 | set2  # 或者 set1.union(set2)
print(f"并集: {union}")  # {1, 2, 3, 4, 5, 6, 7, 8}

# 交集 (共同元素)
intersection = set1 & set2  # 或者 set1.intersection(set2)
print(f"交集: {intersection}")  # {4, 5}

# 差集 (在set1中但不在set2中)
difference = set1 - set2  # 或者 set1.difference(set2)
print(f"差集: {difference}")  # {1, 2, 3}

# 对称差集 (不在交集中的元素)
symmetric_diff = set1 ^ set2  # 或者 set1.symmetric_difference(set2)
print(f"对称差集: {symmetric_diff}")  # {1, 2, 3, 6, 7, 8}

# 子集和超集
small_set = {2, 3}
print(small_set.issubset(set1))  # True (small_set是set1的子集)
print(set1.issuperset(small_set))  # True (set1是small_set的超集)
```

## 10. 实用应用

### 统计唯一访问者
```python
# 网站访问日志
visitors = ["user1", "user2", "user1", "user3", "user2", "user4", "user1"]

# 统计唯一访问者
unique_visitors = set(visitors)
print(f"总访问次数: {len(visitors)}")
print(f"唯一访问者: {len(unique_visitors)}")
print(f"访问者列表: {unique_visitors}")
```

### 学生选课系统
```python
# 课程和选课学生
courses = {
    "数学": {"张三", "李四", "王五", "赵六"},
    "英语": {"张三", "王五", "钱七", "孙八"},
    "计算机": {"李四", "王五", "赵六", "钱七"}
}

# 找出同时选修数学和英语的学生
math_english = courses["数学"] & courses["英语"]
print(f"同时选修数学和英语: {math_english}")

# 找出只选修一门课的学生
all_students = set()
for students in courses.values():
    all_students.update(students)

single_course_students = set()
for student in all_students:
    course_count = 0
    for students in courses.values():
        if student in students:
            course_count += 1
    if course_count == 1:
        single_course_students.add(student)

print(f"只选修一门课的学生: {single_course_students}")
```

### 词频统计
```python
text = "python is great python is powerful python is easy"
words = text.split()

# 使用字典统计词频
word_count = {}
for word in words:
    word_count[word] = word_count.get(word, 0) + 1

print("词频统计:")
for word, count in word_count.items():
    print(f"{word}: {count}")

# 找出唯一的词
unique_words = set(words)
print(f"唯一词汇: {unique_words}")
```

## 11. 数据结构选择指南

| 数据结构 | 特点 | 适用场景 |
|----------|------|----------|
| 列表 | 有序、可变、允许重复 | 需要保持顺序、频繁修改 |
| 元组 | 有序、不可变、允许重复 | 固定数据、作为字典键 |
| 字典 | 键值对、可变、键唯一 | 快速查找、关联数据 |
| 集合 | 无序、可变、元素唯一 | 去重、集合运算 |

## 练习题

1. 创建一个电话簿程序，可以添加、查找、删除联系人
2. 统计一段文字中每个字符出现的次数
3. 找出两个班级的共同学生和各自独有的学生
4. 实现一个简单的购物车，计算商品总价
5. 分析两个文本文件的词汇差异

## 答案示例

```python
# 1. 简单电话簿
phonebook = {}

def add_contact(name, phone):
    phonebook[name] = phone
    print(f"已添加联系人: {name}")

def find_contact(name):
    if name in phonebook:
        print(f"{name}: {phonebook[name]}")
    else:
        print(f"未找到联系人: {name}")

def delete_contact(name):
    if name in phonebook:
        del phonebook[name]
        print(f"已删除联系人: {name}")
    else:
        print(f"联系人不存在: {name}")

# 使用示例
add_contact("张三", "13800138000")
add_contact("李四", "13900139000")
find_contact("张三")
delete_contact("李四")

# 2. 字符统计
text = "hello world"
char_count = {}
for char in text:
    char_count[char] = char_count.get(char, 0) + 1

for char, count in char_count.items():
    print(f"'{char}': {count}")
```