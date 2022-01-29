---
layout: post
title:  "Synology settings"
date:   2022-01-25 16:00 
categories: NAS
---





黑群晖折腾记。



### 1. Transmission

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

