---
title : CG2019-HW2
permalink: courses/CG2019/HW2
header:
  image: https://learnopengl.com/img/advanced-lighting/advanced_lighting_comparrison.png
  caption: "Photo credit: [**LearnOpenGL**](https://learnopengl.com/Advanced-Lighting/Advanced-Lighting)"
  teaser: https://learnopengl.com/img/advanced-lighting/advanced_lighting_comparrison.png

---




Basic Lighting
==
* Ambient lighting
就算沒light一定還會有最基本的環境光, 使物體不會完全的dark
* Diffuse lighting
面相light source越多，其越亮
* Specular lighting
模擬spotlight, 比較傾向光的顏色而不是物體本身

Shader
==
**vertex shader**
Calculate final vertex position of each vertex.  The main job of a vertex shader is to calculate the final positions of the vertices in the scene.
**geometric shader**
The work of Geometry Shader is to take an input primitive and generate zero or more output primitive.  Geometry Shader is able to remove primitives or tessellate them by outputting many primitives for a single input. Geometry shaders can also convert primitives to different types. For example, point primitive can become triangles.
**fragment shader**
Calculates the color of each fragment that user sees on the screen. The fragment shader runs for each fragment in the geometry. The job of the fragment shader is to determine the final color for each fragment.

Specular
==
* Phong shading
會先計算光線基於法向量而算出的反射向量，然後再拿反射向量跟V去內積，之後依亮度乘上次方
* Blinn-Phong shading
放棄使用反射向量，去使用所謂的halfway vector,這個向量會在V跟光線中間
![](https://i.imgur.com/Xd9SD0Y.png)

Source
==
* [reference](https://www.siggraph.org/education/materials/HyperGraph/illumin/specular_highlights/blinn_model_for_specular_reflect_1.htm)
* [wiki](https://www.wikiwand.com/en/Blinn%E2%80%93Phong_reflection_model)
* [learnopengl.com](https://learnopengl.com/Getting-started/Shaders)
* [learnopengles](https://www.learnopengles.com/tag/per-vertex-lighting/)

Link
==
* [github](https://github.com/genius92606/opengl-shading)


Result
===
<iframe src="/assets/courses/CG2019/HW2.mp4" style="width:100%; height:500px;" frameborder="0" allowfullscreen></iframe>

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