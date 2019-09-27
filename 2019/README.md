# 2019-MUXI: 后端组机试题目

    本次机试的主要考察形式为:现场进行专业知识的学习,并对题目进行解决.

## Go语言学习资料

+ [学长写的教程](https://github.com/ShiinaOrez/Tutor-Go) 可以从第三节，开始我们的第一个例子开始
+ [飞雪无情写的go in action 笔记](https://www.flysnow.org/2017/03/13/go-in-action-go-doc.html) 
+ [Go by Example](https://books.studygolang.com/gobyexample/)
+ [A Tour of Go](https://tour.go-zh.org/)
+ [Go语言圣经](https://books.studygolang.com/gopl-zh/)

请着重学习 **数组(Array)** **切片(Slice)** **字符串转化** 相关内容

使用[Go语言在线运行](https://www.bytelang.com/online/run-code/golang)来进行代码的运行, 最后的代码提交形式为一个**ZIP压缩包**, 内容为 ``序号.go`` 文件. (尽量避免)

**提交文件的邮箱为: ``shiina_orez@qq.com``**

    你应该尝试去写很多的测试程序, 这样可以加深你的理解, 测试时的数据可以写在程序中而不是执行标准输入语句,这样可以减少你们的负担, 输出时注意输出格式, 方便我们查看时能够很好的阅读你们的输出结果.

**测试时候请自己 填写测试数据 有疑问可以问学长**

**如果抄袭或者作弊 一律直接 爪巴**

------

## 题目

### 一、找出数组/切片(array/slice)中第二小的数 （简易）

**测试样例:**

```go
testData := []int{3, 4, 2, 6, 7, 2, 3, 1, 1}
```

**样例输出:**

```
2
```

特别标注, 当倒数第二小的数有多个的时候, 只输出其中的一个

```go
// 代码模板
package main

import "fmt"

func findSecondSmallNum(data []int) int {
    // insert your code here
}

func main() {
    testData := []int{3, 4, 2, 6, 7, 2, 3, 1, 1}
    fmt.Println(findSecondSmallNum(testData))
}
```

------

### 二、斐波那契数列 	（简易）

> 用文字来说，就是斐波那契数列由0和1开始，之后的斐波那契系数就是由之前的两数相加而得出。首几个斐波那契系数是：
>
> 0，1，1，2，3，5，8，13，21，34，55，89，144，233……
>
> **特别指出**：[0](https://zh.wikipedia.org/wiki/0)不是第一项，而是第零项。

请写出程序，输入数字n，返回斐波那契数列的第n项

**测试样例:**

```go
fibIndex := 11
```

**样例输出:**

```
89
```

```go
// 代码模板
package main

import "fmt"

func getFibNum(index int) int64 {
    // insert your code here
}

func main() {
    fibIndex := 11
    fmt.Println(getFibNum(fibIndex))
}
```

------

### 三、判断多个字符串中的公共最长前缀

> 前缀是指一个字符串中的开头一段子字符串,显然一个字符串的前缀也可以是它本身或者为空字符串

传入一个字符串切片, 输出它们的公共最长前缀

**测试样例:**

```go
testStrings := []string{
    "I am string1",
    "I am string2",
    "I am Art3mis.",
    "I am Parzival.",
}
```

**样例输出:**

```go
I am //末尾有空格
```

你应该考虑到各种情况, 比如全部都是空串的情况.

**你应该保证你的代码运行的足够快.**

```go
package main

import (
    "fmt"
    // maybe has more packages
)

func findLongestCommonPrefix(data []string) string {
    // insert your code here
}

func main() {
    testStrings := []string{
        "I am string1",
        "I am string2",
        "I am Art3mis.",
        "I am Parzival.",
    }
    fmt.Println(findLongestCommonPrefix(testStrings))
}
```

------

### 四、(二选一, 任选一题进行完成)
### 1. 全排列

> 给定 {1, 2, 3, , , n}，其全排列为 n! 个，这是最基础的高中组合数学知识，现给出一个数组，请你输出他的全排列

**测试样例:**

```go
testNum := 3
```

**样例输出:**

```go
123
132
231
213
312
321
```

```go
// 代码模板
package main

import "fmt"

func getFullPermutation(num int) [][]int {
    // insert your code here
}

func main() {
    testNum := 3
    testResult := getFullPermutation(testNum)
    for _, result := range testResult {
        fmt.Println(result)
    }
}
```

------

### 2. 阅读伪代码实现归并排序

在算法巨著<<算法导论>>中, 往往使用大家都能看懂的**伪代码**的形式来描述算法, 本题考察**理解算法和实现的能力**.

以下是<<算法导论>>中用于描述**归并排序**的伪代码:

```
MERGE(A, p, q, r)
    n1 = q-p+1
    n2 = r-q
    for i=1 to n1
        L[i] = A[p+i-1]
    for j=1 to n2
        R[j] = A[q+j]
    L[n1+1] = ∞
    L[n2+1] = ∞
    i=1
    j=1
    for k=p to r
        if L[i]<=R[j]
            A[k] = L[i]
            i = i + 1
        else
            A[k]=R[j]
            j = j+1

MERGE-SORT(A,p,r)
    if p < r
        q =(p+r)/2
        MERGE-SORT(A, p, q)
        MERGE-SORT(A, q+1, r)
        MERGE(A, p, q, r)
```

因为单独阅读难度过大, 这里进行一些解释, 便于辅助理解:

> 归并排序的主要思想是将数组不断划分为左右两块分别排序, 然后再合并

+ 函数MERGE-SORT(A, p, r)中: 
    + A代表Array, 也就是即将要被排序的数组
    + p代表数组即将排序的起始位置, 在第一次调用的时候即为0
    + r代表数组即将排序的结束位置, 在第一次调用的时候即为数组的长度-1
    + 代码中的q为待排序片段的中点

请编程实现二路归并排序的Go语言程序.

**样例输入:**

```go
testData := []int{3, 4, 5, 66, 82, 1, 33, 22, 12, 4}
```

**样例输出:**
```go
[1, 3, 4, 4, 5, 12, 22, 33, 66, 82]
```

```go
// 代码模板
package main

import "fmt"

func merge(array []int, left, mid, right int) {
    // insert your code here
}

func mergeSort(array []int, left, right int) {
    // insert yout code here
}

func main() {
    testData := []int{3, 4, 5, 66, 82, 1, 33, 22, 12, 4}
    mergeSort(testData, 0, 9)
    fmt.Println(testData)
}
```

------

> 最后, 本题目由2019@Muxi-BackendGroup提供.

> 祝大家顺利!

> 2019.09.28 by Muxi Studio in CCNU
