---
title : Exp2
permalink: courses/embedded system/Exp2
header:
  image: /assets/courses/embedded system/exp2.png
  teaser: /assets/courses/embedded system/exp2.png
---

Three digit time-meter
===

Please make a three digit time-meter with decimal, minimal function are described as follows:
* Two buttons (implemented by interrupt) (Inputpins)
    * Clear (Reset) 
    * Start and stop
* Three digits of time display (Output pins)
    * Digit in tens 
    * Digit in ones
    * Digit in first decimal places


<iframe src="/assets/courses/embedded system/timer.mp4" style="width:100%; height:500px;" frameborder="0" allowfullscreen></iframe>

Discussion
===

* 這次實驗我們遇到許多錯誤，有語法上的問題、電路接錯，程式邏輯上的錯誤以及腳位衝突，當中最大的發現應該是當我們用Arduino上的serial pin作為digital輸入輸出時，若同時使用serial monitor的功能會產生傳輸上的錯誤。
* 我們加分題的做法為將第一塊板子的小數點數字訊號用4個腳位作為4-bit的訊號傳給第二塊板子。第二塊板子用4個腳位接收小數點數字訊號，用7個腳位顯示小數數字。
