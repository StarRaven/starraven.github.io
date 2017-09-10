title: 按键精灵[Navigation to the webpage was canceled]解决方案
date: 2017-04-12 19:42:23 
tags: [按键精灵]
categories: Programming
---

  症状：
  -  按键精灵启动后运行脚本显示弹窗[???]
  -  双击脚本打开脚本编辑器下方调试窗口显示[Navigation to the webpage was canceled]，点运行无效
  -  系统为win10英文版

<!--more-->

  解决：
  
  
　　直接搜索错误信息搜到的一般是win8以上觉得\*.chm文件不安全而启动的保护机制，这些系统在没有改动之前是无法打开\*.chm文件的，打开后会直接报以上错显示一个空白的网页页面。如果是此类问题的解决方案网上都有，即文件权限中的unlock，解锁了权限之后就能开了。
  
　　但是按键精灵应该不可能是编译成了chm而导致无法运行，所以觉得应该是英文版系统的问题。
  
  - 开始菜单->Settings（新版本为开始菜单左边的小齿轮）/或直接打入control panel，新菜单的搜索功能非常好用
  - Time&Language->左边列表中Region&language->右边列表中Additional date, time, &regional settings
  - 右边列表中Region下第一个Change location
  - Location标签下Home location改为China
  - Administrative标签下Change system locale->改为Chinese (Simplified, China)
  - Formats标签下Format改为Chinese (Simplified, China) [大部分网站没有注明这一步，但是少了这步测试下来是不行的]
  - 重启
  
　　此方法不会将系统变为中文系统，且会解决新装系统中文字体古怪的问题。