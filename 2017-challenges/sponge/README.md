# 代码说明
对明文进行hash，用户需构造不同的明文来获得相同的hash值即可得到flag

hash基本流程
+ 1、当前状态state xor block ，aes加密得到新的state
+ 2、经过3次上述过程
+ 3、最后一块单独处理，返回结果

# 攻击流程：
```
    aes加密和解密可逆，并且AES(AES(a)+b)+c = D, D是第3词加密前的初始状态
    则可推导出 b = AESd(D+c) + AES(a)
    b的约束条件有：后6字节为0
    故通过爆破a和c，来使得得到的b满足条件即可
    之后，另最后一块也为o ，由于D和block均相同，故得到的hash也相同。
```

# 参考链接
[https://github.com/p4-team/ctf/tree/master/2017-02-25-bkp/sponge](https://github.com/p4-team/ctf/tree/master/2017-02-25-bkp/sponge) 
