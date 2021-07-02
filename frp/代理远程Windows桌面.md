## 使用 Frp 内网穿透代理内网windows远程桌面



#### Frp服务端：

**服务器操作系统：** Ubuntu Server 20.04 LTS

**服务器CPU架构：**AMD64

**Frp版本：**0.37.0

```bash
# 从Frp官方仓库拉取Linux版frp程序包
wget https://github.com/fatedier/frp/releases/download/v0.37.0/frp_0.37.0_linux_amd64.tar.gz

# 解压frp程序包到系统临时目录
tar -zxf frp_0.37.0_linux_amd64.tar.gz -C /tmp

# 在用户家目录创建frps目录用于存放frp服务端文件
mkdir -p ~/frps

# 复制Frp服务端文件到用户家目录
cp /tmp/frp_0.37.0_linux_amd64/frps* ~/frps/

# 配置frp服务端
vim ~/frps/frps.ini
```

为frp服务端配置端口，默认是 7000，如果700端口被占用需要自行配置空闲可使用的端口

```ini
[common]
bind_port = 7000
```

以上为服务端配置内容

`ESC` 后输入 `:wq` 回车保存配置内容并退出vim

```bash
# 为Frp服务端程序赋予执行权限
chmod +x ~/frps/frps

# 运行Frp服务
 ~/frps/frps -c ~/frps/frps.ini
```

```bash
# 输出以下内容代表服务的开启成功
2021/06/19 17:24:41 [I] [root.go:200] frps uses config file: /root/frps/frps.ini
2021/06/19 17:24:41 [I] [service.go:192] frps tcp listen on 0.0.0.0:7000
2021/06/19 17:24:41 [I] [root.go:209] frps started successfully
```





#### Frp客户端：

**根据系统下载对应的Frp软件包：**

-   Windows amd64：https://github.com/fatedier/frp/releases/download/v0.37.0/frp_0.37.0_windows_amd64.zip

