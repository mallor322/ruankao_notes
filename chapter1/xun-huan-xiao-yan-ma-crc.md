#循环校验码-CRC

可以检错，不可以纠错

CRC循环校验在进行信息编码时，在尾部加入校验信息，编码后的数据能与循环校验码的**生成多项式**相除后余数为0；

先学习模2除法

> 异或：不同得1，相同得0；



用一个例子来学习CRC编码的运作过程：



在生成CRC编码进行模2除法之前，要根据生成多项式对原始报文编码补0，补0的个数为（生成多项式的位数-1）个即为做除法时余数的位数。

生成的CRC编码再对生成多项式进行模2除法，如果余数为0，说明校验正确。
