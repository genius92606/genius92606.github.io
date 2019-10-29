---
title: "Courses"
layout: splash
permalink: /courses/
date: 2016-03-23T11:48:41-04:00
header:
  image: /assets/images/study.jpg
excerpt: "The courses I studied in NCKU"
intro: 
  - excerpt: 'freshman'
intro2: 
  - excerpt: 'sophomore'
intro3: 
  - excerpt: 'junior'
intro4: 
  - excerpt: 'senior'  
feature_row:
  - image_path: /assets/courses/images/CG2.png
    image_caption: "Image courtesy of [Unsplash](https://unsplash.com/)"
    alt: "placeholder image 2"
    title: "Placeholder 2"
    excerpt: "This is some sample content that goes here with **Markdown** formatting."
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
feature_row2:
  - image_path: /assets/courses/images/CG2.png
    alt: "placeholder image 2"
    title: "Placeholder Image Left Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Left aligned with `type="left"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
feature_row3:
  - image_path: http://web.svgncti.org/wp-content/uploads/2017/10/course-product-image.Web-Programmingpng-600x360.png
    image_caption: "Image courtesy of [NCTI](http://web.svgncti.org/product/web-programming/)"
    alt: "placeholder image 1"
    title: "Web Programming"
    excerpt: "A hard course about web programming"
    url: "courses/wp2018/"
    btn_label: "Read More"
    btn_class: "btn--primary"
feature_row4:
  - image_path: /assets/courses/images/CG2.png
    title: "Rendering"
    excerpt: 'Rendering class'
    url: "courses/rendering/"
    btn_label: "Read More"
    btn_class: "btn--primary"
  - image_path: /assets/courses/images/computer-graphic.jpg
    title: "Computer graphics"
    excerpt: 'Application'
    url: "courses/CG2019/"
    btn_label: "Read More"
    btn_class: "btn--primary"  
---

{% include feature_row id="intro" type="center" %}

<!--
{% include feature_row %}
-->

{% include feature_row id="intro2" type="center" %}

<!--
{% include feature_row id="feature_row2" type="center" %}
-->

{% include feature_row id="intro3" type="center" %}

 
{% include feature_row id="feature_row3"  %}


{% include feature_row id="intro4" type="center" %}


{% include feature_row id="feature_row4"  %}


