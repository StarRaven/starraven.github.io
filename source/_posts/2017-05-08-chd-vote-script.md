title: 彩虹岛候选一键投票脚本（Tampermonkey）
date: 2017-05-08 14:26:03 
tags: [tampermonkey, javascript, pt]
categories: Programming
---
  chd是个比较好进（目前）的国内pt站，但是考核特别多，最近刚上岛，有个新手考核，上传下载10G还比较好说，但是1000魔力着实令人发指。我在葡萄挂了大学四年（虽然也没怎么好好玩pt不过也上传了1T左右，魔力大概也就个几千）。

  好在除了传统的挂种子之外投票候选区一样可以得到魔力值，所以随手写了个脚本，具体tampermonkey的脚本怎么用我就不说了，百度有很多，代码如下，注意事项在最下面。
  
<!--more-->

``` javascript
// ==UserScript==
// @name         CHDBits一键候选投票
// @version      2.0
// @description  CHDBits一键候选投票
// @author       StarRaven
// @match        http://chdbits.co/offers.php
// @github       https://github.com/StarRaven/CHDBits-Auto-Vote.git
// ==/UserScript==

var zNode       = document.createElement ('div');
zNode.innerHTML = '<button id="myButton" type="button" style="width:200px;height:30px;margin-bottom:20px;">'+'自 动 投 票</button>';
zNode.setAttribute ('id', 'myContainer');
var parNode = document.getElementById("outer");
parNode.insertBefore(zNode,parNode.childNodes[0]);

document.getElementById ("myButton").addEventListener (
    "click", ButtonClickAction, false
);

var allURL = [];
var n = 0;

function showUrl(index) {
    index = index || 0;
    if (allURL.length === 0 || index < 0 || index >= allURL.length) {
        return;
    }
    var popup = window.open(allURL[index]);
    popup.onload = function() {
        var status = popup.document.getElementsByTagName('p')[0].innerHTML;
        //console.log(status);
        if (status == "你已经投过票，每个候选只能投一次。"){
            popup.close();
            return;
        }
        popup.close();
        showUrl(index + 1);
    };
}

function ButtonClickAction (zEvent) {
    var aDom = document.getElementsByTagName("a");
    for(var i=0,len=aDom.length;i<len;i++){
        if ((aDom[i].href).indexOf("vote=yeah")>0){
            //console.log(aDom[i].href);
            allURL[n] = aDom[i].href;
            n++;
        }
    }
    showUrl();
}
```

Hint:
- chrome默认的设置禁止了单页面弹出多窗口，会导致打开多个页面的代码只能打开第一个页面，需要在chrome设置：Settings->Show advanced settings...->Privacy->Content settings...->Pop-ups->Allow all sites to show pop-ups

2.0 Update:
- 页面加载完自动关闭页面，大大节省时间
- 发现已投过票页面立即停止，避免浪费无谓的时间
- 投票按钮移到中间正上方，较为醒目

1.0 Update:
- vote按钮在页面左上角
- 代码中的3000为延时3000毫秒，嫌太慢的可以改小
- 一旦运行在彻底开完页面之前就停不下来了，而且会自动焦点chrome窗口，建议可以玩玩手机或者开个全屏在最前的播放器看看电影
- 老实说以前没怎么写过js脚本，东拼西凑凑出来的，大家看个乐呵就行233

---

一键清空收件箱的脚本在[这里](2017/05/12/2017-05-12-chd-delete-script "一键清空收件箱的脚本").