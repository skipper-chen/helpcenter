# 远程开机使用说明

## 远程开机

### 首先确认您设备的主板是否支持`WAKE-ON-LAN`，若您已开启，请跳过此步骤

#### 1.进入BIOS

开机时反复按`DELTET`或`F2/F8/F12`等按键进入BIOS设置界面;

> 具体按键可参考主板说明书或参考网络教程。

#### 2.确认主板是否支持远程开机

在BIOS电源管理选项中查看菜单是否有`Remote Wake Up`或`Wake on LAN`等类似选项，否则不支持远程开机。

## 添加远程开机服务

#### **1.进入节点小宝控制台**

节点小宝控制台 —— [https://yc.iepose.com](https://yc.iepose.com)

#### **2.点击添加远程开机服务**

#### **3.输入电脑或NAS的MAC地址**

💡可通过以下方式获取电脑或NAS的MAC地址：

> **电脑**：在电脑上打开命令行，输入`ipconfig /all`，找到`物理地址`字段的值，结构为`AA-BB-CC-DD-EE-FF`

> **NAS**：在NAS上打开命令行，输入`ifconfig`，找到NAS内网IP的网卡，输入`ether`的值，结构为`AA-BB-CC-DD-EE-FF`

## 远程开机设备设置

### windows远程开机系统设置

#### **1.开启唤醒功能**

* 通常到“Power Managment（电源管理）”下寻找如下列选项或类似的配置项，并可以启用它。

```
Boot on LAN;
Wake on LAN;
PME Event WakeUp;
Resume by MAC LAN;
Wake-Up by PCI card;
Wake Up On PCI PME;
Power On by PCI Card;
WakeUp by PME of PCI;
Power On By PCI Devices;
WakeUp by Onborad LAN;
Resume By PCI or PCI-E Ddevice.
```

#### **可视化图形的UEFI BIOS，可参考下列设置方式：**

高级 > 高级电源管理（APM）> 开启 Resume By PCI or PCI-E Ddevice（由 pci/pcie 设备唤醒）选项。

#### **2.系统设置**

右键点击开始菜单-设备管理器，对网卡进行设置。

![img](https://www.iepose.com/img/icon89.68ae94a4.png)

**网卡电源设置**

![img](https://www.iepose.com/img/icon90.0573f5a6.png)

***

### 飞牛NAS远程开机系统设置(其他Lixun设备可参考此教程)

**1.进入SSH**

**2.输入命令**

```
sudo apt update
sudo apt install ethtool wakeonlan
```

**3.查询网卡名称**

```
ip add
```

**4.启用`Walke-on_Lan`**

**5.设置开机自启**

①创建开机自启服务文件

```
sudo nano /etc/systemd/system/wol.service
```

②输入以下内容

```
#请将`<网卡名称>`进行替换为实际查询到的名称

[Unit]
Description=Wake-on-LAN for <网卡名称> 
After=network.target

[Service]
Type=oneshot
ExecStart=/usr/sbin/ethtool -s <网卡名称> wol g

[Install]
WantedBy=multi-user.target
```

按下`Ctrl(command)+X`保存，输入`Y`确认保存。

③启用服务

```
sudo systemctl enable wol.service
```

## 远程开机失败

下发指令后，需要一定时间完成开机过程，请稍作等待后查看设备在线状态

被开机主机局域网内没有在线的节点小宝设备端设备
