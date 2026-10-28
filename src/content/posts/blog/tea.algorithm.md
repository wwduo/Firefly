---
title: TEA算法
published: 2026-10-28
description: 这是文章的简短描述
image:
tags:
  - 算法
category: 算法
draft: false
author: 晓
---
# EA算法

## TEA算法介绍

"TEA" 的全称为"Tiny Encryption Algorithm"（即微型加密算法）是1994年由英国剑桥大学的David j.wheeler发明的。

在安全学领域，TEA（Tiny Encryption Algorithm）是一种分组加密算法，它的实现非常简单，通常只需要很精短的几行代码。

TEA算法使用64位的明文分组和128位的密钥，它使用Feistel分组加密框架，需要进行64轮迭代（推荐），最少32轮迭代

简单的说就是，TEA加密和解密的过程都是相同的只是密钥的使用顺序不一样，是以原文以8字节（64位bit）为一组，密钥16字节（128位bit）为一组，（char为1字节，int为4字节，double为8字节），该算法加密轮次可变，一般推荐为64轮，因为被加密的明文为64位，所以最终加密的结果也是64位。

该算法使用了一个神秘常数δ（即DELTA）作为倍数，DELTA 的选择基于**黄金分割比**，能够**有效减少冲突和模式重复**，从而**提高加密的安全性**。这里TEA把它定义为 δ=「(√5 - 1)231」，这个δ对应的数指就是0×9E3779B9(-0x61C88647)，这个值在加密算法（TEA）、哈希函数和伪随机数的生成中会有用到。

## TEA算法图解分析

TEA算法的图解如下图所示：
![联想截图_20261028193838.png](https://tu.xizesha.com/file/1793187904296_联想截图_20261028193838.png)

从图解中可以看到运算有**加法运算，位运算，异或运算**。

流程1：

1、首先TEA加密解密是以原文以8字节（64bit），所以从两边各自传入四个字节

2、右边传入的4个字节，这里将这4个字节称呼为M，M进行了三个部分的操作，M左移4位与密钥K[0]相加，M右移5位与密钥K[1]相加，M与δ相加，最后这三个算出的值再异或

3、左边传入的4个字节，这里将这4个字节称呼为N，N=N+M

流程2：

接着就到了下面这个部分，这里的话M和N交换了位置，

2、右边传入的4个字节，N进行了三个部分的操作，N左移4位与密钥K[2]相加，N右移5位与密钥K[3]相加，N与δ相加，最后这三个算出的值再异或

3、左边传入的4个字节，M=M+N

4、此时拿到的M和N就是加密过后的M和N

## TEA算法的实现

#include <stdio.h>  
#include <stdint.h>  
   
//加密函数  
void encrypt (uint32_t* v, uint32_t* k) {  
    uint32_t v0=v[0], v1=v[1], sum=0, i;           /* v0、v1分别是明文的左、右半部分，sum作为加密过程中的累加变量*/  
    uint32_t delta=0x9e3779b9;                     /* 作为sum的累加值，题目中往往会修改此值 */  
    uint32_t k0=k[0], k1=k[1], k2=k[2], k3=k[3];   /* 密钥 */  
    for (i=0; i < 32; i++) {                       /* tea加密进行32轮 */  
        sum += delta;  
        v0 += ((v1<<4) + k0) ^ (v1 + sum) ^ ((v1>>5) + k1);  
        v1 += ((v0<<4) + k2) ^ (v0 + sum) ^ ((v0>>5) + k3);  
    }                                              /* v0、v1只是临时变量，加密后内容要返回给v数组 */  
    v[0]=v0; v[1]=v1;  
}  
   
//解密函数  
void decrypt (uint32_t* v, uint32_t* k) {  
    uint32_t v0=v[0], v1=v[1], sum=0xC6EF3720, i;  /* v0、v1分别是明文的左、右半部分，sum作为加密过程中的累加变量 */  
    uint32_t delta=0x9e3779b9;                       
    uint32_t k0=k[0], k1=k[1], k2=k[2], k3=k[3];   /* 密钥 */  
    for (i=0; i<32; i++) {                          
        v1 -= ((v0<<4) + k2) ^ (v0 + sum) ^ ((v0>>5) + k3);  
        v0 -= ((v1<<4) + k0) ^ (v1 + sum) ^ ((v1>>5) + k1);  
        sum -= delta;  
    }                                              /* 解密后内容返还给v数组 */  
    v[0]=v0; v[1]=v1;  
}  
   
int main()  
{  
    uint32_t v[2]={1,2},k[4]={2,2,3,4};  
    // v为要加密的数据是两个32位无符号整数  
    // k为加密解密密钥，为4个32位无符号整数，即密钥长度为128位  
    printf("加密前原始数据：%u %u\n",v[0],v[1]);  
    encrypt(v, k);  
    printf("加密后的数据：%u %u\n",v[0],v[1]);  
    decrypt(v, k);  
    printf("解密后的数据：%u %u\n",v[0],v[1]);  
    return 0;  
}

**TEA解题示例**

**nssctf id3327**

**[MoeCTF 2022]ezTea**

**题目**
![联想截图_20261028193852.png](https://tu.xizesha.com/file/1793187902284_联想截图_20261028193852.png)
![联想截图_20261028193856.png](https://tu.xizesha.com/file/1793187897080_联想截图_20261028193856.png)
**解密代码**
![联想截图_20261028193901.png](https://tu.xizesha.com/file/1793187895794_联想截图_20261028193901.png)
**运行结果**
![联想截图_20261028193911.png](https://tu.xizesha.com/file/1793187899344_联想截图_20261028193911.png)
**参考文献**

[https://www.cnblogs.com/zpchcbd/p/15974293.html](https://www.cnblogs.com/zpchcbd/p/15974293.html)

[https://blog.csdn.net/c7777127_/article/details/143300021](https://blog.csdn.net/c7777127_/article/details/143300021)

[https://blog.csdn.net/m0_73393932/article/details/130094306](https://blog.csdn.net/m0_73393932/article/details/130094306)

[https://blog.csdn.net/2403_87020251/article/details/144354655](https://blog.csdn.net/2403_87020251/article/details/144354655)

[https://blog.csdn.net/xiao__1bai/article/details/123307059](https://blog.csdn.net/xiao__1bai/article/details/123307059)