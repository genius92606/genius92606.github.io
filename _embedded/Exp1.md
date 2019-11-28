---
title : Exp1
permalink: courses/embedded system/Exp1
header:
  image: /assets/courses/embedded system/exp1.png
  teaser: /assets/courses/embedded system/exp1.png
---

Thunderbolt
===
Please make a LED array (at least 5 LEDs) with 霹靂燈’s  function
<iframe src="https://docs.google.com/viewer?srcid=1oeiKk7VTzFyaHl_EKN-1jDzfe5DPySYq&pid=explorer&efh=false&a=v&chrome=false&embedded=true" style="width:100%; height:500px;" frameborder="0" allowfullscreen></iframe>

Arduino Code:
```c
int led = 8;           // the PWM pin the LED is attached to
int brightness = 255;    // how bright the LED is
int fadeAmount = 1;    // how many points to fade the LED by

// the setup routine runs once when you press reset:
void setup() {
  // declare pin 9 to be an output:
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(13, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  // set the brightness of pin 9:
  analogWrite(led, brightness);
  analogWrite(led+1,brightness-125);
  analogWrite(led+2,brightness-220);
  analogWrite(led+3,0);
  analogWrite(led-1,brightness-125);
  analogWrite(led-2,brightness-220);
  analogWrite(led-3,0);

  // change the brightness for next time through the loop:
  led = led + fadeAmount;

  if(led<=8||led>=13){
    fadeAmount=-fadeAmount;
  }
  // reverse the direction of the fading at the ends of the fade:
  /*if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }*/
  // wait for 30 milliseconds to see the dimming effect
  delay(200);
}
```

Adder & Multiplier
===
Design a 3-bits adder (input) and a 3-bits (input) multiplier, please assign two 3-bit as inputs, 6-bit as output. You can only use the basic logic operation in the Arduino (such as NOT, AND, OR, XOR…). Mathematical arrhythmic operation in Arduino is prohibited in this lab-practice.
<iframe src="https://docs.google.com/viewer?srcid=1l5LIgOKxkG4W22tIYvnAj86uM8Du6Nr8&pid=explorer&efh=false&a=v&chrome=false&embedded=true" style="width:100%; height:500px;" frameborder="0" allowfullscreen></iframe>

Arduino Code:
```c
const int Aa = 1;
const int Ab = 2;
const int Ac = 3;
const int Ba = 4;
const int Bb = 5;
const int Bc = 6;

const int S = 7;

const int Ca = 8;
const int Cb = 9;
const int Cc = 10;
const int Cd = 11;
const int Ce = 12;
const int Cf = 13;

void setup() {
  // put your setup code here, to run once:
  pinMode(Aa, INPUT);
  pinMode(Ab, INPUT);
  pinMode(Ac, INPUT);
  pinMode(Ba, INPUT);
  pinMode(Bb, INPUT);
  pinMode(Bc, INPUT);
  pinMode(S, INPUT);
  pinMode(Ca, OUTPUT);
  pinMode(Cb, OUTPUT);
  pinMode(Cc, OUTPUT);
  pinMode(Cd, OUTPUT);
  pinMode(Ce, OUTPUT);
  pinMode(Cf, OUTPUT);
  
}

void loop() {
  // put your main code here, to run repeatedly:
int a1=digitalRead(Aa);
int a2=digitalRead(Ab);
int a3=digitalRead(Ac);
int b1=digitalRead(Ba);
int b2=digitalRead(Bb);
int b3=digitalRead(Bc);
int selectMode=digitalRead(S);
int c1;
int c2;
int c3;
int c4;
int c5;
int c6;
int d1;
int d2;
int d3;
int e1;
int e2;
int e3;
int f1;
int f2;
int f3;
int g1;
int g2;
int g3;
int g4;
int h1;
int h2;
int h3;

if (selectMode == 1) {
c1=((~a1)&(b1))|((a1)&(~b1));
d2=a1&b1;
d3=(a2&d2)|(b2&d2)|(a2&b2);
c2=((a2)&(~b2)&(~d2))|((~a2)&(~b2)&(d2))|((a2)&(b2)&(d2))|((~a2)&(b2)&(~d2));
c4=(a3&d3)|(b3&d3)|(a3&b3);
c3=((a3)&(~b3)&(~d3))|((~a3)&(~b3)&(d3))|((a3)&(b3)&(d3))|((~a3)&(b3)&(~d3));
c5=0;
c6=0;
} else {
c1=((a1)&(b1));

e1=((a2)&(b1));
e2=((a3)&(b1));
e3=0;
f1=((a1)&(b2));
f2=((a2)&(b2));
f3=((a3)&(b2));

g1=((~e1)&(f1))|((e1)&(~f1));
d2=e1&f1;
d3=(e2&d2)|(f2&d2)|(e2&f2);
g2=((e2)&(~f2)&(~d2))|((~e2)&(~f2)&(d2))|((e2)&(f2)&(d2))|((~e2)&(f2)&(~d2));
g4=(e3&d3)|(f3&d3)|(e3&f3);
g3=((e3)&(~f3)&(~d3))|((~e3)&(~f3)&(d3))|((e3)&(f3)&(d3))|((~e3)&(f3)&(~d3));
c2=g1;

h1=((a1)&(b3));
h2=((a2)&(b3));
h3=((a3)&(b3));

c3=((~g2)&(h1))|((g2)&(~h1));
d2=g2&h1;
d3=(g3&d2)|(h2&d2)|(g3&h2);
c4=((g3)&(~h2)&(~d2))|((~g3)&(~h2)&(d2))|((g3)&(h2)&(d2))|((~g3)&(h2)&(~d2));
c6=(g4&d3)|(h3&d3)|(g4&h3);
c5=((g4)&(~h3)&(~d3))|((~g4)&(~h3)&(d3))|((g4)&(h3)&(d3))|((~g4)&(h3)&(~d3));
}

if (c1 == 1) {
    digitalWrite(Ca, HIGH);
  } else {
    digitalWrite(Ca, LOW);
}
if (c2 == 1) {
    digitalWrite(Cb, HIGH);
  } else {
    digitalWrite(Cb, LOW);
}
if (c3 == 1) {
    digitalWrite(Cc, HIGH);
  } else {
    digitalWrite(Cc, LOW);
}
if (c4 == 1) {
    digitalWrite(Cd, HIGH);
  } else {
    digitalWrite(Cd, LOW);
}
 if (c5 == 1) {
    digitalWrite(Ce, HIGH);
  } else {
    digitalWrite(Ce, LOW);
}
 if (c6 == 1) {
    digitalWrite(Cf, HIGH);
  } else {
    digitalWrite(Cf, LOW);
}


}
```

Discussion
===
這次的實驗讓我更了解邏輯閘的概念，也真正實作了加法器和以及乘法器。我們這次的實驗也實作了霹靂燈，一個可以很常見的東西，原來運用小小的ARDUINO版也可以很簡單的做出來。我覺得團隊實驗真的很重要，有人接電路、有人寫程式，然後大家一起討論程式該怎麼學，透過團隊合作才可以很快的完成這次的實驗。
