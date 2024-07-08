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
待更新
### Openwrt
待更新