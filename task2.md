# task2

## 条件语句

### if 语句

```
if expression:
    expr_true_suite
```

- if 语句的 `expr_true_suite` 代码块只有当**条件表达式 `expression` 结果为真时才执行**，**否则将继续执行紧跟在该代码块后面的语句。**
- 单个 if 语句中的 `expression` 条件表达式可以通过布尔操作符 `and`，`or`和`not` 实现多重条件判断。

【例子】

```
if 2 > 1 and not 2 > 3:
    print('Correct Judgement!')

# Correct Judgement!
```

###  if - else 语句

```
if expression:
    expr_true_suite
else:
    expr_false_suite
```

- Python 提供与 if 搭配使用的 else，**如果 if 语句的条件表达式结果布尔值为假，那么程序将执行 else 语句后的代码。**

【例子】

```
temp = input("猜一猜小姐姐想的是哪个数字？")
guess = int(temp) # input 函数将接收的任何数据类型都默认为 str。
if guess == 1010:
    print("你太了解小姐姐的心思了！")
    print("哼，猜对也没有奖励！")
else:
    print("猜错了，小姐姐现在心里想的是1010！")
print("游戏结束，不玩儿啦！")
```

`if`语句支持嵌套，即在一个`if`语句中嵌入另一个`if`语句，从而构成不同层次的选择结构。Python 使用缩进而不是大括号来标记代码块边界，因此要特别注意`else`的悬挂问题。

【例子】

```
hi = 6
if hi > 2:
    if hi > 7:
        print('好棒!好棒!')
else:
    print('切~')
```

【例子】

```
temp = input("不妨猜一下你爸爸现在心里想的是那个数字：")
guess = int(temp)
if guess > 8:
    print("大了，大了")
else:
    if guess == 8:
        print("你这么懂小哥哥的心思吗？")
        print("哼，猜对也没有奖励！")
    else:
        print("小了，小了")
print("游戏结束，不玩儿啦！")
```

### if - elif - else 语句

```
if expression1:
    expr1_true_suite
elif expression2:
    expr2_true_suite
    .
    .
elif expressionN:
    exprN_true_suite
else:
    expr_false_suite
```

- elif 语句即为 **else if**，用来**检查多个表达式是否为真**，并**在为真时执行特定代码块中的代码**。

【例子】

```
temp = input('请输入成绩:')
source = int(temp)
if 100 >= source >= 90:
    print('A')
elif 90 > source >= 80:
    print('B')
elif 80 > source >= 60:
    print('C')
elif 60 > source >= 0:
    print('D')
else:
    print('输入错误！')
```

###  assert 关键词

- `assert`这个关键词我们称之为“断言”，当这个关键词**后边的条件为 False** 时，**程序自动崩溃并抛出`AssertionError`的异常。**

【例子】

```
my_list = ['lsgogroup']
my_list.pop(0)
assert len(my_list) > 0

# AssertionError
```

- 在进行单元测试时，可以用来在程序中**<u>置入检查点</u>**，<u>只有条件为 True 才能让程序正常工作</u>。

【例子】

```
assert 3 > 7

# AssertionError
```

## 循环语句

### while 循环

`while`语句最基本的形式**包括一个位于顶部的布尔表达式**，**一个或多个属于`while`代码块的缩进语句。**

```
while 布尔表达式:
    代码块
```

`while`循环的代码块会<u>**一直循环执行**，**直到布尔表达式的值为布尔假**</u>。

如果布尔表达式不带有`<、>、==、！=、in、not in`等运算符，<u>仅仅给出数值之类的条件，也是可以的</u>。当`while`后写入一个非零整数时，视为真值，执行循环体；写入`0`时，视为假值，不执行循环体。也<u>可以写入`str、list`或任何序列</u>，**长度非零则视为真值，执行循环体；否则视为假值，不执行循环体。**

【例子】

```
count = 0
while count < 3:
    temp = input("不妨猜一下小哥哥现在心里想的是那个数字：")
    guess = int(temp)
    if guess > 8:
        print("大了，大了")
    else:
        if guess == 8:
            print("你是小哥哥心里的蛔虫吗？")
            print("哼，猜对也没有奖励！")
            count = 3
        else:
            print("小了，小了")
    count = count + 1
print("游戏结束，不玩儿啦！")
```

【例子】布尔表达式返回0，循环终止。

```
string = 'abcd'
while string:
    print(string)
    string = string[1:]

# abcd
# bcd
# cd
# d
```

### while - else 循环

```
while 布尔表达式:
    代码块
else:
    代码块
```

当`while`循环正常执行完的情况下，执行`else`输出，如果`while`循环中执行了**跳出循环的语句**，比如 `break`，**将不执行`else`代码块的内容**。

【例子】

```
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = count + 1
else:
    print("%d is not less than 5" % count)
    
# 0 is  less than 5
# 1 is  less than 5
# 2 is  less than 5
# 3 is  less than 5
# 4 is  less than 5
# 5 is not less than 5
```

【例子】

```
count = 0
while count < 5:
    print("%d is  less than 5" % count)
    count = 6
    break
else:
    print("%d is not less than 5" % count)

# 0 is  less than 5
```

### for 循环

`for`循环是迭代循环，在Python中相当于一个通用的序列迭代器，**可以遍历任何有序序列**，如`str、list、tuple`等，也可以**遍历任何可迭代对象**，如`dict`。

```
for 迭代变量 in 可迭代对象:
    代码块
```

<u>每次循环</u><u>，</u>**<u>迭代变量被设置为可迭代对象的当前元素</u>**，提供给代码块使用。

【例子】

```
for i in 'ILoveAnita':
    print(i, end=' ')  # 不换行输出

# I L o v e A n i t a
```

【例子】

```
member = ['陈百强', '张国荣', '刘德华', '梅艳芳', '周润发']
for each in member:
    print(each)

# 陈百强
# 李四
# 刘德华
# 梅艳芳
# 周润发

for i in range(len(member)):
    print(member[i])

# 陈百强
# 张国荣
# 刘德华
# 梅艳芳
# 周润发
```

【例子】

```
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for key, value in dic.items():
    print(key, value, sep=':', end=' ')
    
# a:1 b:2 c:3 d:4 
```

【例子】

```
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for key in dic.keys():
    print(key, end=' ')
    
# a b c d 
```

【例子】

```
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}

for value in dic.values():
    print(value, end=' ')
    
# 1 2 3 4
```

###  for - else 循环

```
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```

当`for`循环**正常执行完的情况下，执行`else`输出**，如果`for`循环中**执行了跳出循环的语句**，比如 `break`，**将不执行`else`代码块的内容**，与`while - else`语句一样。

【例子】

```
for num in range(10, 20):  # 迭代 10 到 20 之间的数字
    for i in range(2, num):  # 根据因子迭代
        if num % i == 0:  # 确定第一个因子
            j = num / i  # 计算第二个因子
            print('%d 等于 %d * %d' % (num, i, j))
            break  # 跳出当前循环
    else:  # 循环的 else 部分
        print(num, '是一个质数')

# 10 等于 2 * 5
# 11 是一个质数
# 12 等于 2 * 6
# 13 是一个质数
# 14 等于 2 * 7
# 15 等于 3 * 5
# 16 等于 2 * 8
# 17 是一个质数
# 18 等于 2 * 9
# 19 是一个质数
```

### range() 函数

```
range([start,] stop[, step=1])
```

- 这个BIF（Built-in functions）有三个参数，其中用中括号括起来的两个**表示这两个参数是可选的。**
- <u>`step=1` 表示第三个参数的默认值是1</u>。
- `range` 这个BIF的作用是**生成一个从`start`参数的值开始到`stop`参数的值结束的数字序列**，该序列**包含`start`的值**但**不包含`stop`的值**。

【例子】

```
for i in range(2, 9):  # 不包含9
    print(i)

# 2
# 3
# 4
# 5
# 6
# 7
# 8
```

【例子】

```
for i in range(1, 10, 2):
    print(i)

# 1
# 3
# 5
# 7
# 9
```

### enumerate()函数

```
enumerate(sequence, [start=0])
```

- sequence -- 一个序列、迭代器或其他支持迭代对象。
- start -- 下标起始位置。
- 返回 enumerate(枚举) 对象

【例子】

```
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
lst = list(enumerate(seasons))
print(lst)
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
lst = list(enumerate(seasons, start=1))  # 下标从 1 开始
print(lst)
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

`enumerate()`与 for 循环的结合使用

```
for i, a in enumerate(A)
    do something with a  
```

用 `enumerate(A)` **<u>不仅返回了 `A` 中的元素，还顺便给该元素一个索引值 (默认从 0 开始)</u>**。此外，用 **`enumerate(A, j)`** 还可以**确定索引起始值为 `j`**。

【例子】

```
languages = ['Python', 'R', 'Matlab', 'C++']
for language in languages:
    print('I love', language)
print('Done!')

'''
I love Python
I love R
I love Matlab
I love C++
Done!
'''

for i, language in enumerate(languages, 2):
    print(i, 'I love', language)
print('Done!')

'''
2 I love Python
3 I love R
4 I love Matlab
5 I love C++
Done!
'''
```

### break 语句

`break`语句可以**跳出当前所在层的循环**。

【例子】

```
import random
secret = random.randint(1, 10) #[1,10]之间的随机数

while True:
    temp = input("不妨猜一下小哥哥现在心里想的是那个数字：")
    guess = int(temp)
    if guess > secret:
        print("大了，大了")
    else:
        if guess == secret:
            print("你这样懂小哥哥的心思啊？")
            print("哼，猜对也没有奖励！")
            break
        else:
            print("小了，小了")
print("游戏结束，不玩儿啦！")
```

### continue 语句

`continue`**终止本轮循环并开始下一轮循环**。

【例子】 +=（两个值相加,然后返回值给符号左侧的变量） %（求余数）

```
for i in range(10):
    if i % 2 != 0:
        print(i)
        continue
    i += 2
    print(i)

# 2
# 1
# 4
# 3
# 6
# 5
# 8
# 7
# 10
# 9
```

###  pass 语句

`pass` 语句的意思是“**不做任何事**”，如果你<u>在需要有语句的地方不写任何语句</u>，那么<u>解释器会提示出错</u>，而 `pass` 语句就是<u>用来解决这些问题的</u>。

【例子】

```
def a_func():

# SyntaxError: unexpected EOF while parsing
```

【例子】

```
def a_func():
    pass
```

`pass`是**空语句，不做任何操作**，只起到占位的作用，**其作用是为了保持程序结构的完整性**。尽管`pass`语句不做任何操作，但**<u>如果暂时不确定要在一个位置放上什么样的代码，可以先放置一个`pass`语句，让代码可以正常运行。</u>**

### 推导式

#### **列表推导式**

```
[ expr for value in collection [if condition] ]
```

【例子】

```
x = [-4, -2, 0, 2, 4]
y = [a * 2 for a in x]
print(y)
# [-8, -4, 0, 4, 8]
```

【例子】**(次方)

```
x = [i ** 2 for i in range(1, 10)]
print(x)
# [1, 4, 9, 16, 25, 36, 49, 64, 81]
```

【例子】

```
x = [(i, i ** 2) for i in range(6)]
print(x)

# [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
```

【例子】

```
x = [i for i in range(100) if (i % 2) != 0 and (i % 3) == 0]
print(x)

# [3, 9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99]
```

【例子】

```
a = [(i, j) for i in range(0, 3) for j in range(0, 3)]
print(a)

# [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
```

【例子】

```
x = [[i, j] for i in range(0, 3) for j in range(0, 3)]
print(x)
# [[0, 0], [0, 1], [0, 2], [1, 0], [1, 1], [1, 2], [2, 0], [2, 1], [2, 2]]

x[0][0] = 10
print(x)
# [[10, 0], [0, 1], [0, 2], [1, 0], [1, 1], [1, 2], [2, 0], [2, 1], [2, 2]]
```

【例子】

```
a = [(i, j) for i in range(0, 3) if i < 1 for j in range(0, 3) if j > 1]
print(a)

# [(0, 2)]
```

#### **元组推导式**

```
( expr for value in collection [if condition] )
```

【例子】

```
a = (x for x in range(10))
print(a)

# <generator object <genexpr> at 0x0000025BE511CC48>

print(tuple(a))

# (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
```

#### **字典推导式**

```
{ key_expr: value_expr for value in collection [if condition] }
```

【例子】

```
b = {i: i % 2 == 0 for i in range(10) if i % 3 == 0}
print(b)
# {0: True, 3: False, 6: True, 9: False}
```

#### **集合推导式**

```
{ expr for value in collection [if condition] }
```

【例子】

```
c = {i for i in [1, 2, 3, 4, 5, 5, 6, 4, 3, 2, 1]}
print(c)
# {1, 2, 3, 4, 5, 6}
```

#### **其它**

```
d = 'i for i in "I Love Lsgogroup"'
print(d)
# i for i in "I Love Lsgogroup"

e = (i for i in range(10))
print(e)
# <generator object <genexpr> at 0x0000007A0B8D01B0>

print(next(e))  # 0
print(next(e))  # 1

for each in e:
    print(each, end=' ')

# 2 3 4 5 6 7 8 9

s = sum([i for i in range(101)])
print(s)  # 5050
s = sum((i for i in range(101)))
print(s)  # 5050
```

(求和**↑**）

###  综合例子

```
passwdList = ['123', '345', '890']
valid = False
count = 3
while count > 0:
    password = input('enter password:')
    for item in passwdList:
        if password == item:
            valid = True
            break
            
    if not valid:
        print('invalid input')
        count -= 1
        continue
    else:
        break
```

**练习题**：

1、编写一个Python程序来查找那些既可以被7整除又可以被5整除的数字，介于1500和2700之间。

```python
for num in range(1500, 2700):
	if num % 35 == 0:
        print(num)
   
   
```

2、龟兔赛跑游戏

题目描述：

话说这个世界上有各种各样的兔子和乌龟，但是研究发现，所有的兔子和乌龟都有一个共同的特点——喜欢赛跑。于是世界上各个角落都不断在发生着乌龟和兔子的比赛，小华对此很感兴趣，于是决定研究不同兔 子和乌龟的赛跑。他发现，兔子虽然跑比乌龟快，但它们有众所周知的毛病——骄傲且懒惰，于是在与乌龟的比赛中，一旦任一秒结束后兔子发现自己领先t米或以 上，它们就会停下来休息s秒。对于不同的兔子，t，s的数值是不同的，但是所有的乌龟却是一致——它们不到终点决不停止。

然而有些比赛相当漫长，全程观看会耗费大量时间，而小华发现只要在每场比赛开始后记录下兔子和乌龟的数据——兔子的速度v1（表示每秒兔子能跑v1 米），乌龟的速度v2，以及兔子对应的t，s值，以及赛道的长度l——就能预测出比赛的结果。但是小华很懒，不想通过手工计算推测出比赛的结果，于是他找 到了你——清华大学计算机系的高才生——请求帮助，请你写一个程序，对于输入的一场比赛的数据v1，v2，t，s，l，预测该场比赛的结果。

输入:

输入只有一行，包含用空格隔开的五个正整数v1，v2，t，s，l，其中(v1,v2< =100;t< =300;s< =10;l< =10000且为v1,v2的公倍数)

输出:

输出包含两行，第一行输出比赛结果——一个大写字母“T”或“R”或“D”，分别表示乌龟获胜，兔子获胜，或者两者同时到达终点。

第二行输出一个正整数，表示获胜者（或者双方同时）到达终点所耗费的时间（秒数）。

------

样例输入：

10 5 5 2 20

样例输出

D 4

```python
v1,v2,t,s,l = map(int,input().split())
t,s1,s2 = 0,0,0
while s1 < 1 and s2 < 1:
    if s1-s2 < t: 
        time = time+1 
        s1 = s1+v1
        s2 = s2+v2
    else:
        for i in range(s) 
        time = time+1
		s2 = s2+v2 
        if s2 >= l: 
            break
if s1 > s2:
    print("R")
elif s1 == s2:
    print("D")

else :
    print("T")
print(time)
        
        
   

   
```