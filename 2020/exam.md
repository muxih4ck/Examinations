# 木犀后端组2020年秋招机试题

## 注意事项

+   代码编写与运行环境：[Go语言在线运行网站](https://goplay.tools/)
+   代码提交：一道题一个 `序号.go` 文件（`.go`为文件后缀），最后代码以一个 **zip 压缩包**的形式提交，提交到邮箱 `1142319190@qq.com`
+   测试的时候自己填写测试数据，你需要尽可能地考虑可能存在的多种情况
+   如有疑问可询问在场的学长学姐
+   **机试期间全程禁止交流讨论、上网搜索，如有作弊或抄袭，一律 out**

>   在 Windows 下不会修改文件后缀的看[这里](https://jingyan.baidu.com/article/92255446a3a11d851648f48e.html)

## Go 语言学习

你需要事先学习 Go 语言的基本语法

Go 语言学习材料：

+   [Go by Example](https://books.studygolang.com/gobyexample/)
+   [Go语言圣经](https://books.studygolang.com/gopl-zh/)
+   [菜鸟教程](https://www.runoob.com/go/go-tutorial.html)

重点：数组、切片、字符串

---

## 题目

###  1.Muxi or CCNU（简单）

描述：给定一个整数 n，如果能被 7 整除则输出 "Muxi"，如果能被 4 整除则输出 "CCNU"，如果既能被 7 整除，又能被 4 整除就输出 "MuxiCCNU"，否则就输出 "Failed"。

**示例1：**

```
输入：252
输出：MuxiCCNU
```

**示例2：**

```
输入：63
输出：Muxi
```

**代码模板：**

```go
package main

import "fmt"

func main() {
    var n = 252
    // insert your code
}
```



### 2. 一维数组的动态和（简单）

给定一个数组 nums ，返回 nums 的动态和。

数组动态和的计算公式为：`runningSum[i] = sum(nums[0], nums[1], … ,nums[i]) `。

**示例：**

```
输入：nums = [22, 33, 69, 96]
输出：[22, 55, 124, 220]
```

**代码模板：**

```go
package main

import "fmt"

func runningSum(nums []int) []int {
	// insert your code
}

func main() {
    nums := []int{22, 33, 69, 96}
    fmt.Println(runningSum(nums))
}
```



### 3. 格式转换（简单）

给定任意一个**3位的正整数**，按照以下规则将其转换为相应的格式：

+   用 B 表示百位的数
+   用 S 表示十位的数
+   用 G 表示个位的数

请编写一个函数，能进行上述格式的转换并返回一个字符串类型的结果。

提示：可以看看字符串、变量、循环等章节。

**示例1：**

```
输入： 234
输出： BBSSSGGGG
```

**示例2：**

```
输入： 123
输出： BSSGGG
```

**代码模板：**

```go
package main

import "fmt"

func formatInteger(n int) string {
    // insert your code
}

func main() {
	var n = 234
    fmt.Println(formatInteger(n))
}
```



### 4. 删除重复元素

输入包含重复元素的、无序的、int 型数组。你需要在 **原地** 删除重复出现的元素，使得每个元素只出现一次，结果输出新数组和其长度。

注：

* 原地，指在原数组基础上修改，不借用新的数组（append 函数底层建立了新的数组，故不能使用）

* 修改完后，无需考虑新数组中超出其长度的部分，输出时可通过 for 循环限制其输出长度。（不管中间是怎么做的，只要输入任意数组经过运算后，结果正确即可）

* 输出的顺序不做规定，示例2中也可以是 `0 1 2 3 4 5 6`

* 提示：可以看看数组、slice（切片）等章节

**示例1：**

```
输入： 1 1 2
输出：
	1 2
	2
```

**示例2：**

```
输入： 0 4 1 2 5 3 2 2 1 6 1 6 0 3
输出： 
	0 4 1 2 5 3 6
	7
```

**代码模板：**

```go
package main

import (
	// packages
)

func removeDuplicates(nums []int) {
    // insert your code
}

func main() {
    nums := []int{1,1,2}
    removeDuplicates(nums)
}
```



### 5. 单词的子串

给定一个字符串 sentence 作为句子，同时指定检索**子串** str，其中 sentence 由若干单词组成，单词之间被**单个空格**分隔。

>   子串是串中任意个**连续**的字符组成的子序列，如在 abcdef 中，ae 不是子串，而 bc 是子串。

请你检查检索词 str 是否为句子 sentence 中某个单词的**子串**。

   - 如果 str 是某一个单词的子串，则返回该单词在 sentence 中所对应的**单词下标**（即单词在该字符串中是第几个单词）；
   - 如果 str 是多个单词的子串，则返回匹配的第一个单词的单词下标；
   - 如果 str 不是任何单词的子串，则返回 -1 。

**示例 1：**

```
输入：sentence = "I love eating burger", str = "urg"
输出：4
解释："urg" 是 "burger" 的子串，而 "burger" 是句子中第 4 个单词
```

**示例 2:**

```
输入：sentence = "I love muxi", str = "mx"
输出：-1
解释："mx" 不是句子中任何单词的子串。
```

**示例 3:**

```
输入：sentence = "corona dream", str = "d"
输出：2
解释："d" 是第二个单词的子串。
```

代码模板：

```go
package main

import "fmt"

func substringIndex(sentence string, str string) int {
    // insert your code
}

func main() {
    sentence := "I love muxi"
    str := "mx"
    fmt.Println(substringIndex(sentence, str))
}
```



### 6. 粗心的朋友

你的朋友正在使用键盘输入他的名字 name。偶尔，在键入字符时，按键可能会被长按，字符可能被输入 1 次或多次。

你将会检查键盘输入的字符 `typed`。如果它对应的可能是你的朋友的名字（其中一些字符可能被长按），那么就返回 true，否则返回 false。

**示例 1：**

```
输入：name = "alex", typed = "aaleex"
输出：true
解释：'alex' 中的 'a' 和 'e' 被长按。
```

**示例 2：**

```
输入：name = "saeed", typed = "ssaaedd"
输出：false
解释：'e' 一定需要被键入两次，但在 typed 中只有一次。
```

**示例 3：**

```
输入：name = "leelee", typed = "lleeelee"
输出：true
```

**示例 4：**

```
输入：name = "laiden", typed = "laiden"
输出：true
解释：长按名字中的字符并不是必要的。
```

**代码模板：**

```go
package main

import "fmt"

func isLongPressedName(name string, typed string) bool {
	// insert your code
}

func main() {
    // 自己填写测试用例
    name := ""
    typed := ""
    fmt.Println(isLongPressedName(name, typed))
}
```



### 7. 完美括号

给定一个只包括 `(`、`)`、`{`、`}`、`[`、`]` 等括号的字符串，判断字符串是否是完美括号。

完美括号字符串需满足：

+   左括号必须用相同类型的右括号闭合；

+   左括号必须以正确的顺序闭合；

+   注意空字符串可被认为是有效字串。

**示例1：**

```
输入: "()"
输出: true
```

**示例2：**

```
输入: "()[]{}"
输出: true
```

**示例3：**

```
输入: "(]"
输出: false
```

**示例4：**

```
输入: "([)]"
输出: false
```

**示例5：**

```
输入: "{[]}"
输出: true
```

**代码模板：**

```go
package main

import "fmt"

func isPerfect(s string) bool {
    // insert your code
}

func main() {
    s := ""
    fmt.Println(isPerfect(s))
}
```



### 8. 全排列

给定一个不包含重复数字的序列，返回所有数字的全排列。

**示例：**

```
输入: 1 2 3
输出:
[
  [1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]
]
```

**代码模板：**

```go
package main

import "fmt"

func permuteUnique(nums []int) [][]int {
	// insert your code
}

func main() {
    nums := []int{1,2,3}
    fmt.Println(permuteUnique(nums))
}
```

---

>   最后，
>
>   本题目由 2020@Muxi-BackendGroup 提供。
>
>   祝大家顺利！
>
>   2020.10.02 by Muxi Studio in CCNU

