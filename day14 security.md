[TOC]
<font face = "Consolas">

# security
> 没有绝对安全的系统: 有限的时间,资源无法应对无限种情况
  所以需要集中精力处理重大影响的威胁

## 目标/威胁
### 数据机密性(data confidentiality)/数据泄露
### 数据完整性(data integrity)/数据篡改
### 系统可用性(system availability)/拒绝服务

## 内部攻击方式
### 逻辑炸弹(logic bombs)
恶意编程
### 后门(trap doors)
留给维护用的后门被恶意利用
### 网络钓鱼(logic spoofing)
### 缓冲区溢出(buffer overflow)

## 外部攻击方式
### 恶意软件(Malware)
#### 特洛伊木马(trojan horses)
伪装成正常软件
#### 病毒(virus)
### 蠕虫病毒(worm)
网络上大量繁殖,阻塞通信
### 隐蔽信道(convert channels)
把要传递的信息隐蔽在公开的信道中(暗号)


## 防护
### 加密(cryptography)
> plaintext明文, ciphertext密文, encryption加密, decryption解密
#### 对称密钥(symmetric key)
加密密钥和解密密钥是同一个(如单码代替)
> 易破解
#### 公钥加密(public-key)
加密密钥和解密密钥可以不一样(RSA)
#### 数字签名(digital signatures)
发送前将文档的MD5用私钥加密,得到密文一起发出去,对方收到后将密文用公钥解密得到发送时的MD5,然后检查前后MD5值是否相同.
### 保护域(protection domain)
规定进程可以访问的对象
* 使用访问控制列表**ACL**(access control list)存储
    > 按照用户存储
    可能导致某些用户权限被放大

### 用户认证(user authentication)
密码等

### 多级安全机制(multilevel security)
上级有权阅读下级信息,下级可以汇报

### 强制访问控制MAC(mandatory access controls)
> 系统决定
### 自主访问控制DAC(discretionary access controls)

### 杀毒
### 沙盒(Sandbox)
将可能的恶意软件隔离在沙盒中隔离敏感信息,观察他是否跳转到非法地址