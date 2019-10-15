---
title : rendering-hw3
permalink: courses/rendering/hw3
header:
  image: https://i.ytimg.com/vi/rmO1hQF8-70/maxresdefault.jpg
  teaser: https://i.ytimg.com/vi/rmO1hQF8-70/maxresdefault.jpg
  caption: "Photo credit: [https://www.youtube.com/watch?v=rmO1hQF8-70](https://www.youtube.com/watch?v=rmO1hQF8-70)"
---



作業pdf
===

<iframe src="https://docs.google.com/viewer?srcid=1m27bHQHTPnniJEoWSzosCI3JsZFSmjte&pid=explorer&efh=false&a=v&chrome=false&embedded=true" style="width:100%; height:650px;" frameborder="0"></iframe>

作業環境
===
Windows10, visual studio 2015

方法說明
====

進入build/Release
開啟ConsoleApplication.exe

程式如何運行
==

**讀 object**
1. 用blender建立腳色各部位的模型
2. tiny_object_loader.h來讀取.obj檔
3. add完object

**Hierarchy**
1. 建立TREE=>tree.h
2. apendChild(例如想要新增shoulder，那就會先BFS找到body的node, 然後再appendChild )
3. 之後移動或旋轉任意object，其底下所有Child都會跟著動~

**前後左右**
1. 在每個frame讀取按鍵是否被按壓
2. 每按壓+=或-=某些數值
3. 達成前進後退左轉右轉的效果

**跳躍**
1. 按下"SPACE"的當下紀錄一時間
2. 之後持續+=(高度)
3. 過0.5秒後開始換成-=(高度)
4. 到1秒便回到原本高度並切雙腳合併

程式如何操作
==

1. 開啟執行檔後
2. 鍵盤的上下左右可以控制腳色移動
3. 按鍵"C"可以切換camera位置
4. 鍵盤"W""A""S""D"可以在空間中移動(移動camera)
5. 鍵盤"SPACE"可以使腳色跳躍
6. 滑鼠移動可以轉動視角
7. 滑鼠滾輪可以ZOOM


相關連結
==
* [HackMD](https://hackmd.io/s/Bk1QLx_hN)
* [GitHub](https://github.com/genius92606/character_OpenGL)
* [HW_PPT](https://github.com/genius92606/character_OpenGL/blob/master/OpenGL_homework_3.pptx)