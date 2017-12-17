# C quiz

C语言测试，不可使用C++特性编写程序。
测试共有5题，限时3小时。

## A.打印素数
输出100以内的所有素数。
根据算法效率来计算分数。

INPUT：无

OUTPUT：
```
2 3 5 ... 97
```

## B.进制转换
写一个可以将2进制正整数(小于1000位)转化为10进制数的函数。

INPUT1：
```
1010101101010101010101010101010
```
OUTPUT1：
```
1437248170
```
INPUT2：
```
1111111111111111110111111
```
OUTPUT2：
```
33554367
```
INPUT3 :
```
1011101010101011011101001011
```
OUTPUT:
```
195737419
```
INPUT4：
```
0000000000001
```
OUTPUT4：
```
1
```

## C. Search a 2D Matrix
写一个程序来在一个m * n 矩阵中寻找一个数字。
这个矩阵有以下性质:

+ 每一行的数字从左到右递增
+ 每一行的第一个数字都比上一行的最后一个数字大

**考虑使用改矩阵的特性来实现一个较为高效的算法**

**输入格式:**
M(行)
N(列)
Target（搜索的目标）
M行数字,每行有N个数字.
**输出格式:**
true(找到了)
false(未找到)

Input Data1:
```
3
4
3
1 3 5 7
10 11 16 20
23 30 34 50
```
Output:
```
true
```

Input Data2:
```
1
2
3
1 3
```

Output:
```
true
```

Input Data3:
```
3
3
20
1 3 5
7 9 11
13 15 17
19 21 23
```

Output:
```
false
```

Input Data4:
```
2
2
8
1 2
3 4
```

Output:
```
false
```

## D.合并序列
合并两个已增序排列的序列，要求合并后的序列仍然保持增序。(有考虑效率者或使用更高级数据结构者可加分)

**输入格式**
每个测试用例有两个序列，每个序列第一行的值为该序列有N个数字，接下来N个数字为该序列的元素．

**输出格式**
一个有序序列

INPUT1：
```
4
1 5 6 9
6 
2 5 7 10 12 15
```
OUTPUT1：
```
1 2 5 5 6 7 9 10 12 15
```


INPUT2：
```
5
5 8 9 10 23
3
2 5 7
```
OUTPUT2：
```
2 5 5 7 8 9 10 23
```

INPUT3：
```
5
1 3 5 10 20
5
2 4 6 8 19
```
OUTPUT3:
```
1 2 3 4 5 6 8 10 19 20
```

## E.Target Sum
**description** :
You are given a list of non-negative integers, a1, a2, ..., an, and a target, S. Now you have 2 symbols + and -. For each integer, you should choose one from + and - as its new symbol.

**Input** :

Each input file contains one test case.
Print in the first line the number of the non-negative integers and the target.
Print in the second line each number : 
```
num target
a0 a1 a2 ····· a(num-1) 
```

**Output** : 
Print how many ways to assign symbols to make sum of integers equal to target S.
```ways```

**Note** :

1. The length of the given array is positive and will not exceed 20.
2. The sum of elements in the given array will not exceed 1000.
3. Your output answer is guaranteed to be fitted in a 32-bit integer.

**Example1 :**
### Input:
```
5 3 
1 1 1 1 1 
```
### Output: 
```
5
```
### Explanation: 
-1+1+1+1+1 = 3
+1-1+1+1+1 = 3
+1+1-1+1+1 = 3
+1+1+1-1+1 = 3
+1+1+1+1-1 = 3
There are 5 ways to assign symbols to make the sum of nums be target 3.

**Example2 :**
### Input:
```
5 3 
1 2 3 4 5 
```
### Output: 
```
3
```
### Explanation: 
-1-2-3+4+5 = 3
+1-2+3-4+5 = 3
-1+2+3+4-5 = 3
There are 3 ways to assign symbols to make the sum of nums be target 3.


**Example3 :**
### Input:
```
5 5 
1 2 3 4 5 
```
### Output: 
```
3
```
### Explanation: 
+1+2+3+4-5 = 5
-1+2+3-4+5 = 5
+1-2-3+4+5 = 5

There are 3 ways to assign symbols to make the sum of nums be target 5.


