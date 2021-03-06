#存储管理——页面置换算法

广泛应用于分层的存储体系当中；比如Cache数量有限当有块被占用，需要调入新的块时，就涉及到页面的置换问题，在内存的体系中，也存在同样的问题；

考试中常常考查两种：先进先出和最近最少使用

**最优算法（Optimal，OPT）：**

理论层面上的页面淘汰算法，是在整个事情发生之后（已知访问序列是怎样的），根据这个序列算出什么时间点访问什么序列能够得到最高的效率，针对不同场景最优算法是不一样的；

而在实际的执行过程中，往往没有办法从整体了解到要访问的页面顺序（比如，涉及到分支，要根据条件判断，不知道下一个序列究竟是哪个），没有办法直接应用；

最优算法方案，一般是用来做基准参照，把它与其他页面淘汰算法进行对比，看其他算法方案与最优方案还有哪些差距。

**随机(RAND)算法：**（随机淘汰一个，性能不稳定）

**先进先出（FIFO）算法：**哪个页面是最新最先进入内存的，就先淘汰谁；有可能产生“抖动”（**抖动**：分配给你更多的资源，希望事情完成的更好更快一些，结果效率反而降低了）；

> 比如：432143543215，用3个页面比用4个产生的缺页反而要少

![](/imgs/1.3.11-1页面置换之先进先出算法.png)

**最近最少使用算法：**刚被访问过的不会被淘汰（因为局部性原理，刚访问过的资源，有可能马上再次被访问到）；不会“抖动”，即分配的资源越多，表现的性能越好；

![](/imgs/1.3.11-2FIFO对比LRU.png)

#页面淘汰算法实例

**基础的KB、字节、位的转换：**

1KB=1024字节=1024*8位

因此1023单元就是8bit，而16位的指令、操作数分别要占用两个单元；（这里每一个单元是1个字节，即8bit；）

**没有使用快表：**暗示每读一次程序的块，都要先在内存上查表——》访问相应的内存块，因此每个块都要有两次内存的访问，这道题程序总共涉及了6个块，因此需要6*2=12次内存访问；

**缺页中断约定俗成的规则：**默认指令不论占到几个块，都要一次性调入（这里swap指令其实垮了两个页（两个块）），因此只会产生一次缺页中断，而对于操作数而言，在两块分别占一半，会产生两次缺页中断……

![](/imgs/1.3.11-3页面淘汰算法例题.png)