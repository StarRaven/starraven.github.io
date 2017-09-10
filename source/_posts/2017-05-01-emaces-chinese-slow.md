title: Emacs在Windows下速度缓慢，光标延迟解决方案
date: 2017-05-01 12:26:03 
tags: [Emacs]
categories: Programming
---

症状：
- windows下Emacs运行后延迟剧大，比如按一下右要过几秒才会光标右移
- 下面指令区域的延迟应该是正常的现象，好像在tutorial还是哪里有说只有按的比较慢那边才会显示。
  
解决方案：
- Options->Set Default Font->将那个奇怪的字体改成宋体或微软雅黑后关闭
- Options->Save Options
　　