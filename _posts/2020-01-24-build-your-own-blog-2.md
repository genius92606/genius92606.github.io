---
title: "Build A Blog With Jekyll And GitHub Pages Part 2"
share: true
header:
  overlay_image: "https://scriptedtea.com/assets/images/posts/jekyll_pages.jpg"
  caption: "Photo credit: **Lars Veelaert**"
  teaser: "https://scriptedtea.com/assets/images/posts/jekyll_pages.jpg"
classes: wide
categories:
  - tutorial
tags:
  - github
  - jekyll
  - blog
last_modified_at: 2020-01-24T16:00:52-04:00
---


Step 1
===
Fork the repository [here](https://github.com/mmistakes/minimal-mistakes), then rename the repo to **USERNAME.github.io** - replacing **USERNAME** with your GitHub username.

Remember to go to Settings
![setting](/assets/images/setting.PNG)

and make sure the source of  Github pages have change to master branch
![master](/assets/images/master.PNG)

Step 2
===
You can remove following folders and files if you want
* .editorconfig
* .gitattributes
* .github 
* /docs
* /test
* CHANGLOG.md
* minimal-mistakes-jekyll.gemspec
* README.md

Step 3
===
Set up jekyll on Window

1. Download and Install a Ruby+Devkit version from [RubyInstaller Downloads](https://rubyinstaller.org/downloads/). Use default options for installation.
2. Run the ```ridk install``` step on the last stage of the installation wizard. This is needed for installing gems with native extensions. You can find additional information regarding this in the RubyInstaller Documentation
3. Open a new command prompt window from the start menu, so that changes to the ```PATH``` environment variable becomes effective. Install Jekyll and Bundler via: ```gem install jekyll bundler```
4. Check if Jekyll installed properly: ```jekyll -v```

Step 4
===
open **CMD**

```
cd Desktop/yourFolder
bundle exec jekyll serve
```
Then, open your browser and go to http://localhost:4000

You can also type this
```
bundle exec jekyll serve --post 4001
```
for multiple website, **4001** can be other number.<br>
Some numbers are not allowed, you can try it by yourself~


