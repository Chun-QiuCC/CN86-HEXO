---
title: 快速开始 | Begin
date: 2024-7-8
---
## 说明
 [加群](https://qm.qq.com/cgi-bin/qm/qr?k=ZrLIxTgGY5P7W8SgNGfZWlLCY1kcf9Ev&jump_from=webapi&authKey=sqA+q7NjvCydLhxv5+bynRK3Jgu8DnVo6PIMenYPGrNwMNB32fd9cFFmZ3qKwpe2) 在群内申请注册你的IP地址和域名
   
  在 [此表格](https://docs.qq.com/sheet/DSGlGeWtTRE9RV3hW) 内查看已被注册的IP地址/地址块和域名，防止和他人冲突
## WireGuard安装、连接教学
### Windows
 1. 下载 [wireguard-amd64-0.5.3.msi](https://drive.crashblock.top/api/v3/file/source/25889/wireguard-amd64-0.5.3.msi?sign=yhneTtGctyM6ysjBaV7Vi3Zpwahla4J7faQyjZxf2vo%3D%3A0) 并安装
 2. 安装完后打开Windows栏里搜索“WireGuard”并打开
 3. 打开后点击左下角的“新建隧道”右边的小三角，选择空白隧道
 4. 可以看到有默认配置
 ```conf
 [Interface]
 PrivateKey = *****************
 ```
请保管好 PrivateKey ，这是你隧道的私钥，泄露将导致你的电脑处于危险状态  

 5. 将下面这段配置写在PricateKey下面
 ```conf
 DNS = 10.86.1.86
 Address = [这里填入你申请的IP地址]

 [Peer]
 PublicKey = [这里填入你要Peer的对端网络路由器公钥]
 AllowedIPs = 10.86.0.0/16
 Endpoint = [这里填入你要加入的网络路由器公网IP和端口]
 PersistentKeepalive = 25
 ```

 6. 将**你的**公钥发给对端，申请与其他人进行Peer以连入CN86网络，为了稳定，你也可以与多人进行Peer
 7. 对方同意并添加了你的连入请求后，点击右边的连接  
 8. 如果右边的节点版块下方有一行 **“上次握手时间: X秒前”** 则说明你已和对端成功 Peer
### Linux

以Debian系Linux系统为例 (或其他使用apt作为包管理器的系统)

1. 安装WireGuard

```shell
sudo apt update && sudo apt install wireguard
```
2. 生成密钥对

```shell
wg genkey | sudo tee /etc/wireguard/privatekey | wg pubkey | sudo tee /etc/wireguard/publickey
```

生成的私钥将保存在 ```/etc/wireguard/privatekey``` 中，公钥将保存在 ```/etc/wireguard/publickey``` 中。

使用 ```cat``` 命令查看私钥和公钥。切记***不要泄露私钥给任何一个人。***

3. 编写WireGuard配置

创建名为```wg0```的WireGuard配置文件
```shell
sudo vim /etc/wireguard/wg0.conf
```
配置文件请参照Windows平台教程，请注意，需要自己填写Interface私钥
5. 启动WireGuard
```shell
sudo wg-quick up wg0
```
6. 使用systemctl运行wireguard (可选)

```shell
systemctl status|start|stop|restart|enable|disable wireguard@wg0
 ```
### Openwrt
待更新