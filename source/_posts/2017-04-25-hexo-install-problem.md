title: hexo安装问题-npm换源
date: 2017-04-25 19:59:45 
tags: [hexo, npm]
categories: Programming
---

症状：

按照网上流程一直到在命令行输入
``` bash
npm install -g hexo
```
后迅速出现回显
``` bash
npm WARN deprecated swig@1.4.2: This package is no longer maintained
```
此回显不影响安装流程，可以忽略，但是出现这行命令后光标长时间在下一行闪烁而没有回应。

<!--more-->

解决：
ctrl+c打断进程
``` bash
npm config set registry https://registry.npm.taobao.org
```
``` bash
npm info underscore
```
或直接进入[淘宝 NPM 镜像网站](http://npm.taobao.org/)，按照流程替换npm为cnpm命令亦可