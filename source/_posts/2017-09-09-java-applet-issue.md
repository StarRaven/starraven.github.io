---
title: 使用Java Applet过程中的一些问题
date: 2017-09-09 22:17:46
tags: [java, applet]
categories: Programming
---

　　这一阵子跑到匹大来念书了，忙了一个月也算安定下来了。有闲心重新打理这个博客了，希望有空的时候能补上几篇我整个出国过程的文章，也算可以帮助一些和我一样成绩不怎么好的同学吧。

　　这篇文章的起因主要是因为第一学期选了一门叫Interactive System Design的课，第一个作业是做一个about me的page我就不吐槽了。第二个作业竟然是用java applet来写东西。我第一眼看到这个名词的时候就觉得大事不妙，先不说当年本科那个配jsp的SSH环境是多么的痛苦，这applet一听就觉得特别复古，简直就和小学时候听到DOS环境一样了。然后果不其然，配置的途中真是路途坎坷……

<!--more-->

## 问题

　　Eclipse的安装大家都是轻车熟路，JDK也不是什么难事，现在软件的安装都简单了，基本上一键就可以帮PATH也一起配好，不会出什么问题。

　　在写applet的时候碰到的第一个小问题是在eclipse的run as菜单里没有找到java applet，后来发现是自己蠢了，拿helloworld举个例子：
``` java
import java.applet.*;
public class HelloWorld extends Applet {
```
　　只要import了正确的类，并且主类extends了Applet（表明这是个applet）选项就会自动出现。

　　第二个才是大问题，写完html之后惊讶地发现**浏览器打开后一片空白**

## 解决
### appletviewer

　　第一种解决方法最简单，打开命令行，切到html目录，执行appletviewer命令：
``` bash
appletviewer index.html
```
　　但是有一个缺点，打开后的大小并非页面大小，还是那个applet的大小，很没有真实感。

### 浏览器配置

　　第二种就是正规的浏览器配置了，首先我在自己电脑上使用的是64位的最新版chrome，而chrome浏览器又是最早不支持NPAPI的，简言之就是不支持java applet，所以打开以后是白屏，连缺省控件都不会给你显示，因为他直接过滤掉了。

　　于是我就屁颠屁颠去下了个firefox，结果发现……晴天霹雳，firefox 52版本之后也不支持了……（所以到底为什么我还要用applet……）下了老版50版本的firefox之后，发现还是什么也没有……跑去查阅了官方文档，里面说只有32位的才支持（眩晕……），之后我就直接去了firefox portable（懒得装了），下载了50的32位portable版，结果还是白屏。再查阅java的文档，如果要用32位的浏览器，就必须安装32位的jre……

　　这次安装完之后终于有结果了，出现了缺省控件的字样，但是还是不能运行，会显示“Applications Blocked by Security Settings”的字样，具体的完美解决方案我也没有找到，只能找到一个临时的：运行configure java，security标签页中直接在白名单里edit list，把html的路径添上（就是file:///）打头的目录，最后就可以运行了，每次变更了目录就需要重新添加一遍白名单。

## 总结
　　既然java applet已经淘汰的这么彻底了，还是少用为妙……教授似乎还说了要带运行结果到课堂，我随身带的笔记本又是linux的，还得重新配置一遍，想了想还是放弃吧……
