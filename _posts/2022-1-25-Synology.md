---
layout: post
title:  "Synology settings"
date:   2022-01-25 16:00 
categories: NAS
---





黑群晖折腾记。

### 1. 外网访问

需要公网ip+域名+DDNS.

1. 在腾讯云注册域名：https://dnspod.cloud.tencent.com/
2.  进入控制台，找到域名，点解析。
3. 点添加记录，主机记录`@`，记录类型`A`，记录值公网ip。
4. 右上角我的账号，安全设置，API密钥，DNSPod Token。
5. 点创建密钥，随便起名，然后记录ID和Token。
6. 在路由器或群里里添加DDNS，服务商选 DNSPod.cn，主机名称写域名，用户名写ID，密码写Token。
7. 端口映射后可以通过域名:5000访问。

添加SSL证书可参考：https://codess.cc/archives/90.html

外网可以通过webdav挂载硬盘，需要安装`WebDAV Server`套件。Windows系统建议使用RaiDrive挂载，系统自带的太难用了。https://www.raidrive.com/

### 2. Transmission

添加社群地址：[http://packages.synocommunity.com](http://packages.synocommunity.com/). 如果提示“无效的位置”需要在ssh里更新证书。

```bash
sudo mv /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt.bak && sudo curl -Lko /etc/ssl/certs/ca-certificates.crt https://curl.se/ca/cacert.pem
```

在社群里搜索安装Transmission。然后在ssh安装中文UI。

```bash
wget https://github.com/ronggang/transmission-web-control/raw/master/release/install-tr-control-cn.sh

bash install-tr-control-cn.sh
```

修改账号密码编辑配置文件中的`rpc-password`。

```bash
vim /volume1/@appstore/transmission/var/settings.json
```



### 
