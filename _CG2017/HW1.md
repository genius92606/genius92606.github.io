---
title : CG2019-HW1
permalink: courses/CG2019/HW1
header:
  image: /assets/courses/images/CG2019-hw1.gif
  teaser: /assets/courses/images/CG2019-hw1.gif

---

作業pdf
===
<iframe src="https://docs.google.com/viewer?srcid=1DwSeJMkBvm3hCCVrxGDkjVhXx9YonrjX&pid=explorer&efh=false&a=v&chrome=false&embedded=true" style="width:100%; height:650px;" frameborder="0"></iframe>


Result
==
![](https://i.imgur.com/qNShEWS.gif)

library
===
由於OpenGL驅動版本眾多，它大說數函數的位置都無法在編譯的時候確定下來，需要再運行時查詢，GLAD提供用於運行時獲取OpenGL函數地址的方式
```cpp
#include <glad/glad.h>
```
GLFW允許使用者創建OpenGL上下文，定義窗口參數以及處理輸入
```cpp
#include <GLFW/glfw3.h>
```
OpenGL Mathematics(GML)，幫助數學運算的函示庫

```cpp
#include <glm/glm.hpp>
#include <glm/gtc/matrix_transform.hpp>
#include <glm/gtc/type_ptr.hpp>
```
gui的函示
```cpp
#include <fmt/format.h>
#include <imgui.h>
#include <memory>
#include "imgui_impl_opengl3.h"
#include "imgui_impl_glfw.h"
```
```cpp
#include "WenCheng.h"
```
WenCheng.h裡包含
```cpp
#include "Texture.h"
#include "StaticMesh.h"
#include "ShaderProgram.h"
#include "ScopeResource.h"
```

Rendering Pipeline
==

1.	**Vertex Specification** 
In Vertex Specification, list an ordered list of vertices that define the boundaries of the primitive. Along with this, one can define other vertex attributes like color, texture coordinates etc. Later this data is sent down and manipulated by the pipeline.
3.	**Vertex Shader** 
The vertex specification defined above now pass through Vertex Shader. Vertex Shader is a program written in GLSL that manipulate the vertex data. The ultimate goal of vertex shader is to calculate final vertex position of each vertex. Vertex shaders are executed once for every vertex(in case of a triangle it will execute 3-times) that the GPU processes. So if the scene consists of one million vertices, the vertex shader will execute one million times once for each vertex. The main job of a vertex shader is to calculate the final positions of the vertices in the scene.
5.	**Tessellation** 
This is a optional stage. In this stage primitives are tessellated i.e. divided into smoother mesh of triangles.
7.	**Geometry Shader** 
This shader stage is also optional. The work of Geometry Shader is to take an input primitive and generate zero or more output primitive. If a triangle strip is sent as a single primitive, geometry shader will visualize a series of triangles. Geometry Shader is able to remove primitives or tessellate them by outputting many primitives for a single input. Geometry shaders can also convert primitives to different types. For example, point primitive can become triangles.
9.	**Vertex Post Processing** 
This is a fixed function stage i.e. user has a very limited to no control over these stages. The most important part of this stage is Clipping. Clipping discards the area of primitives that lie outside the viewing volume.
11.	**Primitive Assembly** 
This stage collects the vertex data into a ordered sequence of simple primitives(lines, points or triangles).
13.	**Rasterization** 
This is an important step in this pipeline. The output of rasterization is a fragments.
15.	**Fragment Shader** 
Although not necessary a required stage but 96% of the time it is used. This user-written program in GLSL calculates the color of each fragment that user sees on the screen. The fragment shader runs for each fragment in the geometry. The job of the fragment shader is to determine the final color for each fragment.
17.	**Per-sample Operations** 
There are few tests that are performed based on user has activated them or not. Some of these tests for example are Pixel ownership test, Scissor Test, Stencil Test, Depth Test.

StaticMesh
==

1. VBO(vertex buffer object)
  store a large number of vertices in the GPU’s memory~
  
2. VAO(vertex array object)
It can be bound vertex buffer objects

3. IBO(index buffer object) or EBO(element buffer object)
they reduce the repeat vertices

4. indices

ShaderProgram
==

**main.cpp**中可以看到
```cpp
auto prog = Program::LoadFromFile(
        "../resource/vs.vert",
        "../resource/fs.frag"
    );
```
可以在**ShaderProgram.cpp**找到
```cpp
Program Program::LoadFromFile(const std::string &vs, const std::string &fs)
{
    auto vs_src = ::read_file(vs);
	auto fs_src = ::read_file(fs);

    try{
        GLuint vshader = CreateShader(GL_VERTEX_SHADER, vs_src);
        GLuint fshader = CreateShader(GL_FRAGMENT_SHADER, fs_src);

        GLuint id = glCreateProgram();
        glAttachShader(id, vshader);
        glAttachShader(id, fshader);
        glLinkProgram(id);
    
        glDeleteShader(vshader);
        glDeleteShader(fshader);
        return Program(id);
    } catch(std::exception &e) {
        std::cerr<<e.what();
        return Program(0);
    }
}
```
讀取vertex and fragment shader
Create shader and program, then attach and link.


Hint
======

一些Hint，需在create window前設置好
版本、上下文的配置...
```cpp
glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 4);
    glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 5);
    glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);
    window = glfwCreateWindow(640, 480, "Simple example", NULL, NULL);
```

About main.cpp
==

**main.cpp**
```cpp
// Do not remove {}, why???
    {
    // text and mesh, shader => garbage collector
    auto g1 = Protect(text_sun);
    auto g2 = Protect(mesh_sun);
    auto g3 = Protect(prog_sun);
    
    //a lot of codes here
    
    }
    glfwDestroyWindow(window);
    glfwTerminate();
```
- The {} should not be removed so that we can release the resource first before terminating the program.

---
go to **ScopeResource.h** for definition of Protect()
```cpp
struct Deleter
{
    void operator()(T *rhs) const{
        rhs->release();
        std::cerr<<"RElease\n";
    }
};

template <class T>
auto Protect(T &rhs) -> std::shared_ptr<T>
{
    return std::shared_ptr<T>(&rhs, Deleter<T>());
}
```
- Operator overloading 
    - void operator()(T *rhs)
    - [resource link](https://www.tutorialspoint.com/cplusplus/function_call_operator_overloading.htm)
- Arrow operator in function heading
    - auto Protect(T &rhs) -> std::shared_ptr<T>
    - [resource link](https://stackoverflow.com/questions/22514855/arrow-operator-in-function-heading)
- std::shared_ptr
    - return std::shared_ptr<T>(&rhs, Deleter<T>());
    - [resource link](https://en.cppreference.com/w/cpp/memory/shared_ptr)
    

環境設置
==

**Case 1**
一開始還沒透過conan下載package所以有問題


**Case 2**
後來cmd執行cmake時遇到了![](https://i.imgur.com/njXstzL.jpg)
只需這樣便可解決
![](https://i.imgur.com/0ouyThE.jpg)

**Case 3**
最後直接開啟app.exe遇到的問題![](https://i.imgur.com/e4MECHv.jpg)
因為動態函示庫在外面的關西
所以用cmd在build資料夾中執行
```
start bin\app.exe
```
便可編譯

Resources
==

* https://www.geeksforgeeks.org/opengl-rendering-pipeline-overview/
* https://learnopengl.com/Getting-started/Hello-Triangle
* https://learnopengl-cn.readthedocs.io/zh/latest/01%20Getting%20started/04%20Hello%20Triangle/
* https://hackmd.io/Ws0u-GxWQxu2llPw_AqdWg?both


Try it yourself
===

1. Click [here](/assets/courses/CG2019/CGHW2.rar) to download the file directly
2. Open cmd and move to the folder "build"<br>
3. Start "app.exe" file in folder "bin" <br>
<br>
For example:
```
cd C:\Users\genius92606\Desktop\CGHW2\build
start bin/app.exe
```


