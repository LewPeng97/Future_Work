### 题目

将一个给定字符串根据给定的行数，以从上往下、从左到右进行 Z 字形排列。

比如输入字符串为 `"LEETCODEISHIRING"` 行数为 3 时，排列如下：

```
L   C   I   R
E T O E S I I G
E   D   H   N
```

之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如：`"LCIRETOESIIGEDHN"`。

请你实现这个将字符串进行指定行数变换的函数：

```
string convert(string s, int numRows);
```

**示例 1：**

```
输入: s = "LEETCODEISHIRING", numRows = 3
输出: "LCIRETOESIIGEDHN"
```

**示例 2:**

```
输入: s = "LEETCODEISHIRING", numRows = 4
输出: "LDREOEIIECIHNTSG"
解释:

L     D     R
E   O E   I I
E C   I H   N
T     S     G
```

### 思路

```
从左至右遍历，同时使用数组记录该元素属于哪一行，当达到numRows时，数组下标开始递减直至为0，重复此操作直至结束。
时间复杂度为O(n)
空间复杂度为O(n)
```

### 代码

```
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows < 2:
            return s
        res = [''for _ in range(numRows)]
        hang,flag = 0,-1
        for char in s:
            res[hang] += char
            if hang == 0 or hang == numRows-1:
                flag = -flag
            hang += flag
        return ''.join(res)
```

