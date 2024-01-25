# 网络分层
## 1. OSI七层模型
### 应用层
- 为计算机提供服务
- DNS HTTP P2P EMAIL SMTP
### 表示层
- 数据处理（编解码、加密解密、压缩解压缩）
- JPEG MPEG ASCII EBCDIC
### 会话层
- 管理（建立、维护、重连）应用程序之间的会话
- TCP SIP RTP RPC-Named-pipes
### 传输层
- 为两台主机进程之间的通信提供通用的数据传输服务
- TCP UDP SCTP SSL TLS
### 网络层
- 路由和寻址（决定数据在网络的游走路径）
- IP ICMP IGMP ARP RARP
### 数据链路层
- 帧编码和误差纠正控制
- PPP IEEE 802.2/LLC IEEE 802.3/LLC
### 物理层
- 透明地传送比特流传输
- RJ45 RJ11 RS232

## 2. TCP/IP四层模型
### 应用层
- 为计算机提供服务
- DNS HTTP P2P EMAIL SMTP
### 传输层
- 为两台主机进程之间的通信提供通用的数据传输服务
- TCP UDP SCTP SSL TLS
### 网际层
- 路由和寻址（决定数据在网络的游走路径）
- IP ICMP IGMP ARP RARP
### 网络接口层
- 帧编码和误差纠正控制
- PPP IEEE 802.2/LLC IEEE 802.3/LLC
