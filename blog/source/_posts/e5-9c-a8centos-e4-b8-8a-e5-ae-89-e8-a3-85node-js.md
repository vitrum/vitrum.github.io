title: 在centOs上安装Node.js
tags:
  - javascript
  - node
  - node.js
  - web
id: 691
categories:
  - 计算机与 Internet
  - HTML5
date: 2011-04-26 14:28:22
---

0，基本环境

yum install gcc-c++ openssl-devel

1，获取最新版本
https://github.com/joyent/node

2，解压
tar -xzvf node.0.4.XX.tar.gz

3，进入解压目录

./configure
make
make install

4，也！成功