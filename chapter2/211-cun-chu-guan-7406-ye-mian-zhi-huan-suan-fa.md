#存储管理——页面置换算法

广泛应用于分层的存储体系当中；比如Cache数量有限当有块被占用，需要调入新的块时，就涉及到页面的置换问题，在内存的体系中，也存在同样的问题；

考试中常常考查两种：先进先出和最近最少使用

最优算法（Optimal，OPT）：理论层面上的页面淘汰算法，是在整个事情发生之后（已知访问序列是怎样的），根据这个序列算出什么时间点访问什么序列能够得到最高的效率，针对不同场景最优算法是不一样的；而在实际的执行过程中，往往没有办法从整体了解到要访问的页面顺序（比如，涉及到分支，要根据条件判断，不知道下一个序列究竟是哪个）。

随机(RAND)算法（随机淘汰一个，性能不稳定）

先进先出（FIFO）算法：有可能产生“抖动”；

> 比如：432143543215

最近最少使用算法：不会“抖动”