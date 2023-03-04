---
layout:       post
title:        "科学上网"
subtitle:     "VPN"
date:         2023-03-02 12:00:00
author:       "Yufan Deng"
header-img:   "img/in-post/post-eleme-pwa/eleme-at-io.jpg"
header-mask:  0.3
catalog:      true
multilingual: true
tags:
    - 加密服务端
---

> 这篇文章转载自[知乎上的回答](http://www.zhihu.com/question/25657351/answer/31278511)
# 域名解析
- 搭建VPN前提是要有dns解析服务，这要求自己必须准备一个域名来解析IP地址
- 我用的是cloudflare服务（以前用的是阿里云，然后嘛懂得都懂），购买域名（购买的是一二级域名,即顶级域名），dns设置，添加记录，类型为A，三级域名随便填，解析对象为你所用vps或虚拟机的IP地址。
# 连接vps或远程连接虚拟机进行代码执行
首先，得会使用SSH连接海外服务器（非常简单，自己琢磨），或者可以远程连接海外虚拟机打开终端。
其次，输入代码更新系统数据，确保环境能正常运行代码。例如我输入的代码是：
- apt update -y 
- apt install -y curl socat
- 然后执行X-UI代码
- bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
- 放行端口，输入命令

- iptables -I INPUT -p tcp --dport 443 -j ACCEPT
- iptables -I INPUT -p tcp --dport 54321 -j ACCEPT
# 申请 SSL 的证书
输入命令：x-ui

- x-ui 管理面板设置
添加证书和密钥路径，重启面板
通过域名访问x-ui 管理面板：<br>https://域名:54321
# 注意事项
- 1、实在不行的话，可以给设备添加权限，即执行命令
- sudo su
- 2、密钥路径，在root/cert目录下的两个文件，一个为fullchain.cer,另一个为二三级域名.key
- 密钥在cloudflare左侧栏的overview（总览，我翻译的，意思一样就行）下的API（往下滑），点击get your API token（获取你的令牌），Global API key（全局密钥），输入你的cloudflare登入密码
- SSL证书申请时输入的邮箱为你注册cloudflare的注册邮箱，域名只需要输入一二级域名（即二级和顶级域名，www.baidu.com,即输入baidu.com），切记不可输入三级域名。
- 若有不解或犹豫操作，可发至邮箱286846966@qq.com/dengyufan666666@gmail.com（谷歌邮箱我不经常浏览）联系作者。


<div >
   
</div>
