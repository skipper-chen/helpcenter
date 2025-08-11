# 群晖 使用说明

## 群晖-使用说明

## 兼容性

群晖架构查询

* x86\_64
* arm\_64

## 系统要求

* DSM\_6 +
* DSM\_7 +

## 下载套件

矿神套件(DSM\_7+)：「套件中心」设置套件来源：`https://spk7.imkns.com`\
官方套件下载：(不支持32位)

* [DSM\_6\_x86](https://tan.ionewu.com/api/jdxb/download/v2/qh_x86)
* [DSM\_6\_arm](https://tan.ionewu.com/api/jdxb/download/v2/qh_arm)
* [DSM\_7\_x86](https://tan.ionewu.com/api/jdxb/download/v2/qh_dsm7_x86)
* [DSM\_7\_arm](https://tan.ionewu.com/api/jdxb/download/v2/qh_dsm7_arm)

## 安装套件

> 如需群晖访问其他组网设备，请查看文末权限修复教程

1. 打开「套件中心」→右上角「手动安装」；
2. 点击「上传套件」，按照指引继续完成安装；
3. 第三发套件安装提示，此处点击“同意”；
4. 确认设置，点击“完成”即可；
5. 点击节点小宝图标，启动套件；
6. 进入设备绑定界面

## 远程访问群晖

1.绑定群晖NAS后，下载电脑客户端（点击下载）\[https://www.iepose.com/download]； 2.登录后，点击「打开控制台」；

3.点击群晖卡片可快速访问到群晖NAS；

4.添加完成后，返回「控制台主页」或打开「PC客户端」，即可一键远程访问内网群晖NAS。

## 群晖发起远程访问

发起组网访问需要给节点小宝套件提权，您需通过ssh登录群晖输入提权命令。

1.打开 `控制面板` -> `终端机` -> `启用SSH`

2.通过 `终端机` -> `SSH` 连接到群晖

3.输入以下命令，回车后输入 DSM 密码

```shell
sudo sed -i 's/package/root/g' /var/packages/owjdxb/conf/privilege
```

4.通过命令修复权限后前往套件中心，手动重启节点小宝套件。

5.输入`route -n`，验证是否创建组网路由表。

## 更多远程访问方案

您还可以通过「内网穿透」和「异地组网」远程访问群晖NAS
