---
title : Simple 3D Software
permalink: projects/simple-3d-software
header:
  image: /assets/projects/final.gif
  teaser: /assets/projects/final.gif


---


This is the final projects in the rendering course. 
 
### Code:
[Simple 3D Software](https://github.com/genius92606/simple-3D-software)

Operating System
===
Windows 10, visual studio 15 2017 Win64

Instructions
====

#### Requirement
1. cmake 
[install here](https://cmake.org/download/)
2. conan - package manager (windows)
[install here](https://conan.io/)

Open command prompt
```bash
set PATH="C:\Program File\CMake\bin\";%PATH%
```
Clone the repository
```bash
git clone https://github.com/genius92606/simple-3D-software.git
```
Create "build" folder in the repository
```bash
cd simple-3D-software
mkdir build && cd build

conan remote add bincrafters https://api.bintray.com/conan/bincrafters/public-conan
conan install .. --build glad -sbuild_type=Debug
```
```bash
cd build
cmake .. -G "Visual Studio 15 2017 Win64"
```

#### Build
```bash
cd build
cmake --build .
```

#### Execution
```bash
cd build
start bin\app.exe
```

Application Instruction
==

1. Execute the application
```bash
cd build
start bin\app.exe
```
2. Click the drop down menu at the left, and click "add" to add a built-in object or click "Load obj" to read objects.
![](https://i.imgur.com/IhAxQ4V.png)
3. If choosing "Load obj", it will pop up a file directory and the user can choose files from the bottom right.
![](https://i.imgur.com/qK1QTp2.png)
4. After adding new objects, the windows will add an extra section like below, the user can change color, translate, rotation, scale of the object. Other than built-in color, we also provide the user to load customize textures by clicking "Load Texture"
![](https://i.imgur.com/YrwHcA6.png)
5. Holding scrolling wheel and moving to change perspective.
6. Scroll the wheel to zoom.
7. This application includes abmient, diffuse, and specular lighting.



Thirdparty
==
1. GLFW3
2. ImGui



Demo video
===
<iframe width="640" height="360" src="https://www.youtube-nocookie.com/embed/wzsEwaMZtxY?controls=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>