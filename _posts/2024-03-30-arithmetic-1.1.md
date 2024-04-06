---
layout: post
title: 算法刷题笔记-经典面试150道-数组/字符串
categories: [Arithmetic, leecode]
description: 算法刷题笔记
keywords: Arithmetic, leecode
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
typora-root-url: ../
---

经典面试150道--数组/字符串部分

## 189. 轮转数组

python：

切片取余：

```python
n = len(nums)
nums[:] = nums[-k % n:] + nums[:-k % n]
```

边删边插：

```python
for _ in range(k): nums.insert(0, nums.pop())
```

## [121. 买卖股票的最佳时机](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock/)

**贪心**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        cost, profit = float('+inf'), 0
        for price in prices:
            cost = min(cost, price)
            profit = max(profit, price - cost)
        return profit

```

> 由于每次迭代中都是局部最优的选择，且贪心地选择了在当前情况下看起来最有利可图的操作，因此这段代码使用了贪心算法来解决买卖股票的最佳时机问题。

## [122. 买卖股票的最佳时机 II](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)

贪心或动态规划

贪心：

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        return sum(max(0, b - a) for a, b in pairwise(prices))

def pairwise(iterable):
    """生成相邻元素的元组"""
    a, b = iter(iterable), iter(iterable)
    next(b, None)
    return zip(a, b)
```

动态规划：

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        f = [[0] * 2 for _ in range(n)]
        f[0][0] = -prices[0]
        for i in range(1, n):
            f[i][0] = max(f[i - 1][0], f[i - 1][1] - prices[i])
            f[i][1] = max(f[i - 1][1], f[i - 1][0] + prices[i])
        return f[n - 1][1]

```

或者，

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        n = len(prices)
        f = [-prices[0], 0]
        for i in range(1, n):
            g = [0] * 2
            g[0] = max(f[0], f[1] - prices[i])
            g[1] = max(f[1], f[0] + prices[i])
            f = g
        return f[1]

```


代码



测试用例

测试用例



测试结果

## [134. 加油站](https://leetcode.cn/problems/gas-station/)**

作者：Naughty DavincicEV的题解很妙！

当遍历全部加油站一次的gas总量减去cost总量大于0则满足按顺序绕环路行驶一周的要求，否则不满足。
**途中最小值很可能是一个负值，这个负值的绝对值最大代表油量亏欠到了最大值**，则从0号加油站到现在会亏欠最多的油量，那么从下一个加油站开始行使到最后一个加油站会永远保持正值的油量，再行驶至上一个加油站也仍然为正值。

```python
class Solution:
    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        have = gas[0] - cost[0]
        minnum = [have, 0]
        for i in range(1, len(gas)):
            have = gas[i] - cost[i] + have
            if have <= minnum[0]:
                minnum = [have, i]
        if have < 0:
            return -1
        return (minnum[1] + 1) % len(gas)

'''作者：Naughty DavincicEV
链接：https://leetcode.cn/problems/gas-station/solutions/2713165/zhao-chu-tu-zhong-sheng-yu-you-liang-zui-tc7k/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。'''
```

## [135. 分发糖果](https://leetcode.cn/problems/candy/)

方法二：常数空间遍历
思路及解法

注意到糖果总是尽量少给，且从 111 开始累计，每次要么比相邻的同学多给一个，要么重新置为 111。依据此规则，我们可以画出下图：

![image-20240402165901596](/images/posts/2024-03-30-arithmetic/image-20240402165901596.png)

其中相同颜色的柱状图的高度总恰好为 1,2,3…。

而高度也不一定一定是升序，也可能是 …3,2,1 的降序：

![image-20240402165915052](/images/posts/2024-03-30-arithmetic/image-20240402165915052.png)

注意到在上图中，对于第三个同学，他既可以被认为是属于绿色的升序部分，也可以被认为是属于蓝色的降序部分。因为他同时比两边的同学评分更高。我们对序列稍作修改：

![image-20240402165949033](/images/posts/2024-03-30-arithmetic/image-20240402165949033.png)

注意到右边的升序部分变长了，使得第三个同学不得不被分配 444 个糖果。

依据前面总结的规律，我们可以提出本题的解法。我们从左到右枚举每一个同学，记前一个同学分得的糖果数量为 $\textit{pre}$：

- 如果当前同学比上一个同学评分高，说明我们就在最近的递增序列中，直接分配给该同学 $\textit{pre} + 1$ 个糖果即可。

- 否则我们就在一个递减序列中，我们直接分配给当前同学一个糖果，并把该同学所在的递减序列中所有的同学都再多分配一个糖果，以保证糖果数量还是满足条件。

  - 我们无需显式地额外分配糖果，只需要记录当前的递减序列长度，即可知道需要额外分配的糖果数量。


  - **同时注意当当前的递减序列长度和上一个递增序列等长时，需要把最近的递增序列的最后一个同学也并进递减序列中。**

这样，我们只要记录当前递减序列的长度 $\textit{dec}$，最近的递增序列的长度$\textit{inc}$ 和前一个同学分得的糖果数量 $\textit{pre}$ 即可。

```python
class Solution:
    def candy(self, ratings: List[int]) -> int:
        n = len(ratings)
        ret = 1
        inc, dec, pre = 1, 0, 1

        for i in range(1, n):
            if ratings[i] >= ratings[i - 1]:
                dec = 0
                pre = (1 if ratings[i] == ratings[i - 1] else pre + 1)
                ret += pre
                inc = pre
            else:
                dec += 1
                if dec == inc:
                    dec += 1
                ret += dec
                pre = 1
        
        return ret

'''作者：力扣官方题解
链接：https://leetcode.cn/problems/candy/solutions/533150/fen-fa-tang-guo-by-leetcode-solution-f01p/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。'''
```

## [42. 接雨水](https://leetcode.cn/problems/trapping-rain-water/)**

> 作者：灵茶山艾府
> 链接：https://leetcode.cn/problems/trapping-rain-water/solutions/1974340/zuo-liao-nbian-huan-bu-hui-yi-ge-shi-pin-ukwm/
> 来源：力扣（LeetCode）
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

### 方法一：前后缀分解

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        n = len(height)
        pre_max = [0] * n  # pre_max[i] 表示从 height[0] 到 height[i] 的最大值
        pre_max[0] = height[0]
        for i in range(1, n):
            pre_max[i] = max(pre_max[i - 1], height[i])

        suf_max = [0] * n  # suf_max[i] 表示从 height[i] 到 height[n-1] 的最大值
        suf_max[-1] = height[-1]
        for i in range(n - 2, -1, -1):
            suf_max[i] = max(suf_max[i + 1], height[i])

        ans = 0
        for h, pre, suf in zip(height, pre_max, suf_max):
            ans += min(pre, suf) - h  # 累加每个水桶能接多少水
        return ans

```

时间复杂度：$\mathcal{O}(n)$，其中 nnn 为 $\textit{height}$ 的长度。
空间复杂度：$\mathcal{O}(n)$。

### 方法二：相向双指针

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        ans = left = pre_max = suf_max = 0
        right = len(height) - 1
        while left < right:
            pre_max = max(pre_max, height[left])
            suf_max = max(suf_max, height[right])
            if pre_max < suf_max:
                ans += pre_max - height[left]
                left += 1
            else:
                ans += suf_max - height[right]
                right -= 1
        return ans

```

复杂度分析
时间复杂度：O(n)\mathcal{O}(n)O(n)，其中 nnn 为 height\textit{height}height 的长度。
空间复杂度：O(1)\mathcal{O}(1)O(1)，仅用到若干变量。

### 方法三：单调栈

[单调栈【基础算法精讲 26】](https://leetcode.cn/link/?target=https%3A%2F%2Fwww.bilibili.com%2Fvideo%2FBV1VN411J7S7%2F)

上面的方法相当于「竖着」计算面积，单调栈的做法相当于「横着」计算面积。

这个方法可以总结成 16个字：**找上一个更大元素，在找的过程中填坑**。

注意 while 中加了等号，这可以让栈中没有重复元素，从而在有很多重复元素的情况下，使用更少的空间。

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        ans = 0
        st = []
        for i, h in enumerate(height):
            while st and h >= height[st[-1]]:
                bottom_h = height[st.pop()]
                if not st:  # len(st) == 0
                    break
                left = st[-1]
                dh = min(height[left], h) - bottom_h  # 面积的高
                ans += dh * (i - left - 1)
            st.append(i)
        return ans

```

复杂度分析
时间复杂度：$\mathcal{O}(n)$，其中 nnn 为 $\textit{height}$的长度。虽然我们写了个二重循环，但站在每个元素的视角看，这个元素在二重循环中最多入栈出栈各一次，因此循环次数之和是$\mathcal{O}(n)$，所以时间复杂度是 $\mathcal{O}(n)$。
空间复杂度：$\mathcal{O}(\min(n,U))$，其中 $U=\max(\textit{height})-\min(\textit{height})+1$。注意栈中没有重复元素，在 $\textit{height}$ 值域很小的情况下，空间复杂度主要取决于 $\textit{height}$ 的值域范围。

## [6. Z 字形变换](https://leetcode.cn/problems/zigzag-conversion/)

```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        n = len(s)
        if numRows <= 1:
            return s
        else:
            n_cnt = numRows * 2 - 2
        trans = ''
        # 1st row
        i = 0
        while True:
            t = i * n_cnt
            if t < n:
                trans += s[t]
            else: 
                break
            i += 1
        # middle row
        for r in range(1,numRows-1):
            i = 0
            while True:
                t1 = i * n_cnt + r
                if t1 < n:
                    trans += s[t1]
                else:
                    break
                t2 = i * n_cnt + (n_cnt-r)
                if t2 < n:
                    trans += s[t2]
                else:
                    break
                i += 1
        # last row
        i = 0
        while True:
            t = i * n_cnt + numRows-1
            if t < n:
                trans += s[t]
            else: 
                break
            i += 1
        return trans
                

```

N 字形变换（巧设 flag ）

```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows < 2: return s
        res = ["" for _ in range(numRows)]
        i, flag = 0, -1
        for c in s:
            res[i] += c
            if i == 0 or i == numRows - 1: flag = -flag
            i += flag
        return "".join(res)

'''作者：Krahets
链接：https://leetcode.cn/problems/zigzag-conversion/solutions/21610/zzi-xing-bian-huan-by-jyd/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。'''
```

