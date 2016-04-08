---
layout:      post
title:       DigitalOcean 配置 Shadowsocks 实现科学上网
tags:        工具
keywords:    DigitalOcean Shadowsocks VPS
description: 在 DigitalOcean 主机上配置 Shadowsocks
---

## 注册 DigitalOcean 账号
+ 在[ DigitalOcean 官网][DigitalOcean]上注册账号。附上我的[邀请链接][referral]，通过这个链接注册可以获得 $10 的奖励。

[DigitalOcean]: https://www.digitalocean.com/
[referral]: https://www.digitalocean.com/?refcode=dc8d6b59a467
[GithubStudent]: https://education.github.com/pack

+ 在 [Github Student Developer Pack][GithubStudent] 中找到 DigitalOcean，获取的 offer code 可以额外获得 $100 的奖励。

+ 绑定信用卡或者 PayPal 的账号，就可以使用各种方式得到的奖励。

## 服务器端配置 Shadowsocks

+ 建立一个 Droplet. Droplet 的字面意思是液滴，在这里应该是指主机。根据网友博客中的建议，选择旧金山（San Francisco）的机房.操作系统选择 Ubuntu 14.04 LTS（LTS 指的是“Long Term Support”，有五年时间的技术支持）。如果要支持 IPv6 方式的科学上网，请勾选 IPv6 选项。为了方便配置，建议添加 SSH Key.

+ 租用主机之后，可以查看主机的硬件配置和网络参数。最便宜的 $5/mo 套餐足以满足科学上网的需求，对应的硬件配置是 512 MB 的内存，20 GB 的 固态硬盘，每月 1000 GB 的流量。查看主机的 IP 地址，在后续配置时会用到。我租用的机房 IPv4 地址是 `104.236.135.215`，IPv6 地址是 `2604:a880:1:20::fa:9001`.

+ 连接到远程服务器，安装 Shadowsocks.

```
ssh root@104.236.135.215
apt-get update # 更新依赖的库文件
apt-get install python-pip
pip install shadowsocks
```

## 启动 Shadowsocks

+ 如果对配置参数比较熟悉，直接使用命令行进行配置，具体内容可以参考 [Shadowsocks 在 GitHub 上的官方介绍][Shadowsocks]。这里我采用配置文件进行管理。

[Shadowsocks]: https://github.com/shadowsocks/shadowsocks

```
# 建立配置文件 /etc/shadowsocks.json
vim /etc/shadowsocks.json
```

+ 添加下面的信息.需要填入主机的 IP 地址，设置密码，选择要使用的端口号。其他参数可以采用 Shadowsocks 给出的默认值。

```
{
    "server":"::",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"type_your_password_here",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```

+ 在前端启动

```
ssserver -c /etc/shadowsocks.json
```

+ 在后台启动或关闭

```
ssserver -c /etc/shadowsocks.json -d start
ssserver -c /etc/shadowsocks.json -d stop
```

## 客户端的配置

Shadowsocks 在客户端的使用非常简单。下载对应的客户端程序，填入主机 IP 地址、端口号和密码。

[Windows][Shadowsocks_Windows] / [OS X][Shadowsocks_OSX]  
[Android][Shadowsocks_Android] / [iOS][Shadowsocks_iOS]

[Shadowsocks_Windows]: https://github.com/shadowsocks/shadowsocks-csharp
[Shadowsocks_OSX]: https://github.com/shadowsocks/shadowsocks-iOS/wiki/Shadowsocks-for-OSX-Help
[Shadowsocks_Android]: https://github.com/shadowsocks/shadowsocks-android
[Shadowsocks_iOS]: https://github.com/shadowsocks/shadowsocks-iOS/wiki/Help

## 参考文献

[Shadowsocks 在 GitHub 上的官方介绍][Shadowsocks]  
[使用Digital Ocean和shadowsocks来科学上网 | 咀嚼之味][jerryzou]

[jerryzou]: http://jerryzou.com/posts/shadowsocks-with-digitalocean/
