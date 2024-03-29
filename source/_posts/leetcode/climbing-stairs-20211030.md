---
title: 爬楼梯
date: 2021-10-30
categories:
  - LeetCode
tags:
  - 数据结构与算法
cover: https://images.mynetdisk.vercel.app/vuepress/cover/WechatIMG11.png
---

> 假设你正在爬楼梯。需要 n  阶你才能到达楼顶。
>
> 每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
>
> 注意：给定 n 是一个正整数。

<!-- more -->

# 70. 爬楼梯

假设你正在爬楼梯。需要 n  阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

示例 1：

输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。

1.  1 阶 + 1 阶
2.  2 阶
    示例 2：

输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。

1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/climbing-stairs
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

解题方案
第一种思路
标签：数学
如果观察数学规律，可知本题是斐波那契数列，那么用斐波那契数列的公式即可解决问题，公式如下：

$$
F_n = 1/\sqrt{5}\Big[\Big(\frac{1+\sqrt{5}}{2}\Big)^n-\Big(\frac{1-\sqrt{5}}{2}\Big)^n\Big]
$$

时间复杂度：O(logn)

第一种思路代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function (n) {
  const sqrt_5 = Math.sqrt(5);
  const fib_n =
    Math.pow((1 + sqrt_5) / 2, n + 1) - Math.pow((1 - sqrt_5) / 2, n + 1);
  return Math.round(fib_n / sqrt_5);
};
```

第二种思路
标签：动态规划
本问题其实常规解法可以分成多个子问题，爬第 n 阶楼梯的方法数量，等于 2 部分之和

爬上 n-1n−1 阶楼梯的方法数量。因为再爬 1 阶就能到第 n 阶

爬上 n-2n−2 阶楼梯的方法数量，因为再爬 2 阶就能到第 n 阶

所以我们得到公式 dp[n] = dp[n-1] + dp[n-2]dp[n]=dp[n−1]+dp[n−2]

同时需要初始化 dp[0]=1dp[0]=1 和 dp[1]=1dp[1]=1

时间复杂度：O(n)

第二种思路代码

```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function (n) {
  const dp = [];
  dp[0] = 1;
  dp[1] = 1;
  for (let i = 2; i <= n; i++) {
    dp[i] = dp[i - 1] + dp[i - 2];
  }
  return dp[n];
};
```

作者：guanpengchn
链接：https://leetcode-cn.com/problems/climbing-stairs/solution/hua-jie-suan-fa-70-pa-lou-ti-by-guanpengchn/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
