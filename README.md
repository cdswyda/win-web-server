# Windows 下的本地 WebServer

快速搭建可快迁移的本地 WebServer，支持多版本 php，多虚拟主机，多端口。

本项目是基于 [nginx](https://nginx.org/en/) 和 [php](https://www.php.net/) 的本地 WebServer，使用 [winsw](https://github.com/winsw/winsw) 将其注册为系统服务，方便管理。

## 简介

虽然 node / php / python 等都可以快速启动一个 web server。 但是相对来说，功能肯定远不如 nginx。而且 nginx 也是一个跨平台的 web server，所以在本地搭建一个 nginx 服务，可以快速迁移到线上。

那么为什么不是 [XAMPP](https://www.apachefriends.org/zh_cn/index.html) 呢？

XAMPP 真的很棒，我也使用了很久. 但是基于以下几个原因，这里我不再使用 XAMPP

1. XAMPP 不能比较方便的支持多个php版本。
2. web 入口我更希望是 nginx，而不是 apache。
3. XAMPP 不能很方便的支持多个虚拟主机，配置形式和线上常用的 宝塔面板等差异较大。

那么为什么不是 [phpstudy](https://www.xp.cn/) 呢？

1. 很久没有新的版本的了，不知道还维护与否。
2. 内置的 nginx 版本太旧了，不方便单独升级。

基于 XAMPP 和 phpstudy 不够用的前提下。我想知其然，更想知其所以然，所以我自己搭建一个。

## nginx

1. 从 [nginx.org](https://nginx.org/en/download.html) 下载你需要的版本，之后解压放在在 nginx 目录下。
2. 修改 conf/nginx.conf 下的配置文件，http节点下添加 `include vhosts/*.conf;`，http 下的 server 节点配置注释或者删除
3. 在 conf/vhosts 目录下添加你的虚拟主机配置文件，参考 [vhosts](./nginx/vhosts/)。
4. 修改 [nginx-server.xml](./nginx/nginx-server.xml) 中启动的注册服务配置。
5. 管理员身份运行 `nginx-server.exe instal` 注册为系统服务。

## php

1. 从 [php](https://www.php.net/downloads.php) 下载需要的版本放在 php 目录下。
2. 修改 [php/php-server.xml](./php/php-server.xml) 中启动的版本和端口号。
3. 管理员身份运行 `php-server.exe instal` 注册为系统服务。

## FAQ
