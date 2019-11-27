---
title : Exp9
permalink: courses/embedded system/Exp9
header:
  image: /assets/courses/embedded system/exp9.png
  teaser: /assets/courses/embedded system/exp9.png
---

Bluetooth
===

* Recall to Lab “Part-8-Voltage Data Logger”
  * Please implement a analog-to-digital converter function in your Arduino.
      * Sampling rate: 10 Hz. 
      * Analog input: PIN A0
  * Please generate a DC voltage from power supply and fed into Arduino PIN A0, then convert the analog DC voltage into digital data in Arduino every (1/10) sec.
  * Transmit the digitalized ADC data from Arduino to PC via Bluetooth and display it in the PC’s terminal software.


communication code:
```c
#include <SoftwareSerial.h>   // 引用程式庫
 
// 定義連接藍牙模組的序列埠
SoftwareSerial BT(8, 9); // 接收腳, 傳送腳
char val;  // 儲存接收資料的變數
 
void setup() {
  Serial.begin(9600);   // 與電腦序列埠連線
  Serial.println("BT is ready!");
 
  // 設定藍牙模組的連線速率
  // 如果是HC-05，請改成38400
  BT.begin(9600);
}
 
void loop() {
  // 若收到「序列埠監控視窗」的資料，則送到藍牙模組
  if (Serial.available()) {
    val = Serial.read();
    BT.print(val);
  }
 
  // 若收到藍牙模組的資料，則送到「序列埠監控視窗」
  if (BT.available()) {
    val = BT.read();
    Serial.print(val);
  }
}
```


voltage data:
```c
#include <SoftwareSerial.h>   // 引用程式庫
 
// 定義連接藍牙模組的序列埠
SoftwareSerial BT(8, 9); // 接收腳, 傳送腳
char val;  // 儲存接收資料的變數
unsigned long time1;
void setup() {
  Serial.begin(9600);   // 與電腦序列埠連線
  Serial.println("BT is ready!");
 
  // 設定藍牙模組的連線速率
  // 如果是HC-05，請改成38400
  BT.begin(9600);
}
 
void loop() {
// read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // Convert the analog reading (which goes from 0 - 1023) to a voltage (0 - 5V):
  float voltage = sensorValue * (5.0 / 1023.0);
  // print out the value you read:
  time1=millis();
  Serial.print(time1);
  Serial.print(" ms ");
  BT.print(time1);
  BT.print(" ms ");
  Serial.print(voltage);
   Serial.println(" V ");
  BT.print(voltage);
  BT.println(" V ");
   
  delay(84);
}

```


Communication
===
<iframe src="/assets/courses/embedded system/exp9.mp4" style="width:100%; height:500px;" frameborder="0" allowfullscreen></iframe>

Results-voltage data
===
![image-center]({{ site.url }}{{ site.baseurl }}/assets/courses/embedded system/exp9-result.png){: .align-center}

Discussion
===
藍芽對於嵌入式裝置真的是分常的重要，因為我們很多嵌入式的裝置只要透過藍芽，就可以變為無線，讓整個裝置更加的完整。藍芽模組也算是好設定、好使用的~所以學習藍芽模組真的是非常重要的。
