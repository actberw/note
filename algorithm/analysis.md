### 算法分析
1. 最坏情况和平均情况
2. 比较(相对速度relative speed on same machine)
3. 渐进分析(asymptotic anaysis), theta notation
 - ignore machine-dependent consts
 - 增长量级 look at growth of T(n) as n ~ infinit,
4. 几种常见的时间复杂度函数按数量级从小到大的顺序依次是：Θ(lgn)，Θ(sqrt(n))，Θ(n)，Θ(nlgn)，Θ(n2)，Θ(n3)，Θ(2n)，Θ(n!)。其中，lgn通常表示以10为底n的对数，但是对于Θ-notation来说，Θ(lgn)和Θ(log2n)并无区别（想一想这是为什么），在算法分析中lgn通常表示以2为底n的对数
