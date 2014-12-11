#麻省理工学院公开课：计算机科学及编程导论
Tags： Python
##课程目标，数据类型，运算，变量 
目标：
1.  编把写程序
2.  读懂别人的程序
3.  把工程编写进去自己的框架
4.  像计算科学家一样思考

>程序：对推论过程的陈述

**Python**

**变量**：


1. numbers
2. string
3. Bruloors
 

##分支，条件和循环
Assignment（赋值申明）
变量的类型

不要反复无常改变变量类型
>statements = legal commends that Python can interpret,print,assignment
优秀代码的风格
 - 加注释
 - 变量名称的选择
28个关键词不能当变量名
**分枝式程序**
>一个能基于测试来改变指令顺序的程序，测试通常是针对变量的值
```python
x = 15
if (x/2)*2 == x:
    print '偶数'
else: print '奇数'
```
冒号是开始，回车是结束
算法复杂度

##一般代码样式，循环式程序
**good style**
类型| 符号|数据结构
-----|------
num|+,*|assitgnment
string||input/output
brolent|and,or|loop med(while)
图灵完全化语言
 - 迭代所要做的步骤
 
 - 流程图 

模拟代码
simuwle
ans |  x |  answers
----|---------
0   |  16 |  0
1     ||     1
2       ||   4
3         || 9
4          ||16
5          ||25
denfencive programming
防卫性设计

```python
x = 1515361
ans = 0
if x >= 0:
    while ans*ans < x:
        ans = ans +1
        #print 'ans = ',ans
    if ans*ans != x:
        print x,' 不是完全平方数'
    else: print ans
else: print x,' 是负数'
```

```python
x = 10
i = 1
while i<x:
    if x%i == 0:
        print '约数',i
    i= i+1
```
循环机制
特定的结构
 for  loop
   for <vov> in <some collection>
      balck of code
      
```python
x = 10
for i in range(1,x):
    if x%i == 0:
        print '约数',i
```
Tuple - ordered sequence of elenmments(immatable)
**混合数据结构**
元组
```python
test = (1,2,3,4)
test[1]#selection
test[-1]#slices
```

```python
x = 100
divisors = ( )#初始化一个空的元组
# 这里讲义上误作[ ]，此更正（圆括号表示元组tuple、方括号表示列表list）
divisors：约数
for i in range(1, x):
    if x%i == 0:
        divisors = divisors + (i, )
```
```python
s1 = 'abcdefg'
s2 = 'hijklmn'
print s1 + s2
print s1.find('cde')
```
```python
sumDigits = 0
for c in str(1952):
    sumDigits += int(c)
print sumDigits
```
##函数抽象与递归简介

回故
 
- assignment
-  conditionals
- looping constructs (for ,while)
图灵完备
模块，抽像
Functions
- black up into modules
- suppsess detail
- create 'new primitives '

function 
def  keyword
name(x) formal parameters
return keyword
None special value

>局部绑定并不影响全局绑定
call function 
   local table
**链表**
抽像：
形参
函数可以没有参数，但是需要有括号
def
return 
None -特殊变量 

方程组
20个头，56个腿，求多少只猪，多少只鸡
$numP+numC=20$
$4*numP+2*numC=56$
```python
def solve(numLegs, numHeads):
    #solve解，num表示number（数目），tot表示total（总数），leg脚、head头、pig猪、chick鸡
    for numChicks in range(0, numHeads + 1):
        numPigs = numHeads - numChicks
        totLegs = 4*numPigs + 2*numChicks
        if totLegs == numLegs:
            return [numPigs, numChicks]
    return [None, None]


def barnYard():
    #barnyard农场
    heads = int(raw_input('输入头的个数：'))
    legs = int(raw_input('输入脚的个数：'))
    pigs, chickens = solve(legs, heads)
    if pigs == None:
        print '无解'
    else:
        print '猪的数目是：', pigs
        print '鸡的数目是：', chickens
```

农场主还养了蜘蛛
**嵌套循环**

```python
def solve1(numLegs, numHeads):
    #spider蜘蛛
    for numSpiders in range(0, numHeads + 1):
        for numChicks in range(0, numHeads - numSpiders + 1):
            numPigs = numHeads - numChicks - numSpiders
            totLegs =4*numPigs + 2*numChicks + 8*numSpiders
            if totLegs == numLegs:
                return [numPigs, numChicks, numSpiders]
    return [None, None, None]

def barnYard1():
    heads = int(raw_input('输入头的个数：'))
    legs = int(raw_input('输入脚的个数：'))
    pigs, chickens, spiders = solve1(legs, heads)
    if pigs == None:
        print '无解'
    else:
        print '猪的数目是：', pigs
        print '鸡的数目是：', chickens
        print '蜘蛛的数目是：', spiders
```

要输出所有的结果
```python
def solve2(numLegs, numHeads):
    solutionFound = False
    for numSpiders in range(0, numHeads + 1):
        for numChicks in range(0, numHeads - numSpiders + 1):
            numPigs = numHeads - numChicks - numSpiders
            totLegs =4*numPigs + 2*numChicks + 8*numSpiders
            if totLegs == numLegs:
                print '猪的数目是：' + str(numPigs) + ',',
                print '鸡的数目是：' + str(numChicks) + ',',
                print '蜘蛛的数目是：', numSpiders
                solutionFound = True
    if not solutionFound: print '无解'
```

###递归


如果你出生在美国，那么你是一个美国人
如果你不是出生在美国，只要你父母其中一个出生在美国，那么你也是美国人

回文字符串
```python
def isPalindrome(s):
    """Return True if s is a palindrome and False otherwise"""
    #如果是回文（palindrome），返回True；否则返回False
    if len(s) <=1: return True
    else: return s[0] == s[-1] and isPalindrome(s[1:-1])


def isPalindrome1(s, indent):
    """Return True if s is a palindrome and False otherwise"""
    #indent 缩进
    print indent, 'isPalindrome1调用', s
    if len(s) <= 1:
        print indent, '准备从基础情况返回True'
        return True
    else:
        ans = s[0] == s[-1] and isPalindrome1(s[1:-1], indent + indent)
        print indent, '准备返回 ', ans
        return ans


``` 


斐波那契

```python
def fib(x):
    """Return Fibonacci of x, where x is a non-negative int"""
    #返回x时的斐波那契数，其中x是非负整数
    if x == 0 or x == 1: return 1
    else: return fib(x-1) + fib(x-2)
    #此法效率很低，算fib(36)就挂了，为什么？是否有什么高效一些的算法呢？
```
##浮点数和二分法(逐次近似)
两种语言类型：int,float
```python
 a = 2**1000
 b = 2**999
 a/b
 2L
```
IEEE规则 754 floating point
1位存储符号
11位存储指数
52位存储尾数
$1/8 : 0.125 = 1.25 * 10^6$
$2 : 1.0*2^-3$
$1/10: 1*10^-1$
repr
```python
s = 0.0
for i in range(10): s +=0.1
S
0.9999999999999999
ptint(s)
1.0
```
worry about == 
```python
 import math
 a = math.sqrt(2)
a
1.4142135623730951
>>> a*a == 2
False
>>> a*a
2.0000000000000004
abs(a*2-2.0) < epslion
```
逐次逼近法：
二分求平方根法 ：
```python
def squareRootB1(x, epsilon):
    """Assume x >= 0 and epsilon > 0
       Return y s.t. y*y is within epsilon of x"""
    #假设x>=0且ε>0，返回y，使得y*y在x的ε内
    assert x >= 0, 'x必须为非负数，而不是' + str(x)
    assert epsilon > 0, 'ε必须为正数，而不是' + str(epsilon)
    low = 0
    high = x
    guess = (low + high)/2.0
    ctr = 1
    while abs(guess**2 - x) > epsilon and ctr <= 100:
        #print 'low:', low, 'high:', high, 'guess:', guess
        if guess**2 < x:
            low = guess
        else:
            high = guess
        guess = (low + high)/2.0
        ctr += 1
    assert ctr <=100, '循环计数次数超出范围'
    print 'Bl方法，循环数', ctr, '估值', guess
    return guess

```

##二分法，牛顿，拉复生方法，对于数组的简介

regession testings 
两个方程的共同解：直线方程与曲线方程，与X轴
$guess_{i+1} = guess_i-F(guess_i)/2*guess_i$
NR求根方法
```python
def squareRootNR(x, epsilon):
    """Assume x >= 0 and epsilon > 0
       Return y s.t. y*y is within epsilon of x"""
    #假设x>=0且ε>0，返回y，使得y*y在x的ε内
    assert x >= 0, 'x必须为非负数，而不是' + str(x)
    assert epsilon > 0, 'ε必须为正数，而不是' + str(epsilon)
    x = float(x)
    guess = x/2.0
    #guess = 0.001
    diff = guess**2 -x
    ctr = 1
    while abs(diff) > epsilon and ctr <= 100:
        #print '差值:', diff, '猜想值:', guess
        guess = guess - diff/(2.0*guess)
        diff = guess**2 - x
        ctr += 1
    assert ctr <=100, '循环计数次数超出范围'
    print 'NR方法，循环数', ctr, '估值', guess
    return guess
```
NR的效率比BI效率要高
计算复杂度十分重要

































