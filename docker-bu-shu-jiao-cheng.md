# Docker部署教程

## Docker部署教程

## Docker-CLI

> 如遇端口冲突，请映射容器的9118端口

### x86\_64

```bash
docker run -d --name owjdxb --network host -v $(pwd)/store:/data/store --device /dev/net/tun:/dev/net/tun --cap-add NET_ADMIN --cap-add SYS_ADMIN --restart unless-stopped ionewu/owjdxb
```

### arm\_64

```bash
docker run -d --name owjdxb --network host -v $(pwd)/store:/data/store --device /dev/net/tun:/dev/net/tun --cap-add NET_ADMIN --cap-add SYS_ADMIN --restart unless-stopped ionewu/owjdxb_a64
```

### arm\_32

```bash
docker run -d --name owjdxb --network host -v $(pwd)/store:/data/store --device /dev/net/tun:/dev/net/tun --cap-add NET_ADMIN --cap-add SYS_ADMIN --restart unless-stopped ionewu/owjdxb_a32
```

***

## Docker-Compose

> 如遇端口冲突，请映射容器的9118端口

### x86\_64

```yaml
version: '3'
services:
    owjdxb: # 为容器指定一个名称
    image: ionewu/owjdxb # x86_64镜像
    network_mode: host # 使用host网络模式启动
    volumes:
        - $(pwd)/store:/data/store # 将当前目录下的store文件夹挂载到容器内的/data/store目录
    devices:
      - "/dev/net/tun:/dev/net/tun"  # 挂载TUN设备 
    cap_add:
      - NET_ADMIN  # 网络管理权限
      - SYS_ADMIN  # 系统管理权限
    restart: unless-stopped

```

### arm\_64

```yaml
version: '3'
services:
    owjdxb: # 为容器指定一个名称
    image: ionewu/owjdxb_a64 # arm_64镜像
    network_mode: host # 使用host网络模式启动
    volumes:
        - $(pwd)/store:/data/store # 将当前目录下的store文件夹挂载到容器内的/data/store目录
    devices:
      - "/dev/net/tun:/dev/net/tun"  # 挂载TUN设备 
    cap_add:
      - NET_ADMIN  # 网络管理权限
      - SYS_ADMIN  # 系统管理权限
    restart: unless-stopped
```

### arm\_32

```yaml
version: '3'
services:
    owjdxb: # 为容器指定一个名称
    image: ionewu/owjdxb_a32 # arm_64镜像
    network_mode: host # 使用host网络模式启动
    volumes:
        - $(pwd)/store:/data/store # 将当前目录下的store文件夹挂载到容器内的/data/store目录
    devices:
      - "/dev/net/tun:/dev/net/tun"  # 挂载TUN设备 
    cap_add:
      - NET_ADMIN  # 网络管理权限
      - SYS_ADMIN  # 系统管理权限
    restart: unless-stopped
```

***

## 绑定

**快速绑定**

启动容器后可访问 `IP:9118` 进入绑定界面；

***

## 常见问题

### 镜像拉取失败

> 由于网络问题，部分用户无法拉取镜像文件。需要手动导入镜像

**下载镜像**

从官网下载您对应架构的镜像文件：

* 群晖下载`.tgz`
* 飞牛、绿联等下载`.tar`

**导入镜像**

* 群晖、绿联：可通过docker管理面板选择镜像并导入
* 飞牛需要通过`docker load`导入镜像

**飞牛导入镜像教程**

1. 官网下载docker镜像文件：`x86_64.tar`
2. 将文件上传到飞牛文件夹：`/docker/images`
3. 使用SSH访问飞牛，输入一下命令（请注意镜像文件名是否与下载的一致）

```bash
sudo docker load -i /vol1/1000/docker/images/ionewu_owjdxb_v21.img.tar$$
```

4. 使用飞牛Docker面板或`Docker-CLI`/`Docker-Compose`启动节点小宝。
