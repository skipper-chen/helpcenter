# 开启Windows远程桌面（RDP）

## 开启Windows远程桌面（RDP）

## 专业版开启RDP

**Windows专业版或者更高级的版本是有开关的，可以直接开启电脑的RDP。**

[**点击开启**](ms-settings:remotedesktop?activationSource=SMC-IA-4028379)

### Win11

设置——系统——远程桌面——启用

***

### Win10

**设置——系统——远程桌面——启用远程桌面**

***

### Win7

右键我的电脑——属性——左边侧栏高级系统设置——远程，在下方“远程桌面”方框下勾选“允许远程连接到此计算机”

## 家庭版开启远程桌面

> 家庭版无法通过系统设置开启远程桌面，但可以借助开源工具开启。

### 下载SuperRDP

首先，需要安装SuperRDP [点击下载](https://github.com/anhkgg/SuperRDP/releases)

### 安装superRDP

1. 运行SuperRDP.exe(需管理员权限)
2. 根据提示选择1（安装）或者2（卸载）
3. 等待完成即可

```
--------------------------------------------------------
---------SuperRDP for Windows 10 Home Version-----------
-------------Copyright (c) 2021 anhkgg.com--------------
-------------anhkgg | 公众号：汉客儿 -------------------
--------------------------------------------------------

--------------------------------------------------------

[+] SuperRDP initialize...

[*] SuperRDP already installed? 【Yes!】

[+] SuperRDP initialize success...

--------------------------------------------------------

Please select option:
  1: Install SuperRDP to Program Files folder (default)
  2: Uninstall SuperRDP
  3: Force restart Terminal Services

>（#在这里输入数字“1”或“2”后按回车确认）
```

### 验证远程桌面服务是否成功。

1. Win+R，输入 mstsc.exe 启动远程桌面程序；
2. 输入127.0.0.1后点击连接，测试服务是否成功。
