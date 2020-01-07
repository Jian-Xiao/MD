# Sublime 使用笔记
<!-- MarkdownTOC -->

- [1 Sublime 字体](#1-sublime-字体)
- [2 Sublime 插件安装](#2-sublime-插件安装)
    - [2.1 Package Control](#21-package-control)
    - [2.2 Markdown](#22-markdown)
- [3 Sublime 快捷键](#3-sublime-快捷键)

<!-- /MarkdownTOC -->


<a id="1-sublime-字体"></a>
### 1 Sublime 字体
Sublime 默认的字体会造成**字体错位**，推荐用等宽字体——**楷体**  
点击Preferences &rarr; Setting 中配置如下：  
```
{
    "font_face":"楷体",
    "font_size":13
}
```

<a id="2-sublime-插件安装"></a>
### 2 Sublime 插件安装

<a id="21-package-control"></a>
#### 2.1 Package Control
按住 Ctrl + Shift + P 即可调出控制台，会提示安装 Package Control

<a id="22-markdown"></a>
#### 2.2 Markdown
Ctrl + Shift + P 调出控制台 &rarr; 输入install+回车 &rarr; 即可查询下列插件:  

插件|作用|备注
:--:|:--:|:--:
MarkdownEditing | 可以MD格式**查看和编辑**文件 | 在**右下角**选择查看格式
MarkdownTOC | 编辑文件时自动**生成目录** | 在**Tools**中选择 Insert TOC
OmniMarkupPreviewer | 在浏览器中**预览MD文件** | 以**MD格式**查看该文件并按住 Ctrl + Alt + O

其中MarkdownTOC配置Setting如下：  
```
{
  "defaults": {
    "autoanchor": true,    //自动跳转
    "autolink": true,      //自动链接
    "uri_encoding": false  //中文不转义
  }
}
```

<a id="3-sublime-快捷键"></a>
### 3 Sublime 快捷键

按键组合|作用
:------:|:--:
Shift + Alt + 1  | 合并页面
Shift + Alt + 2  | 分成左右两页
Shift + Ctrl + P | 调出控制台
Ctrl + Alt + O   | 预览Markdown 