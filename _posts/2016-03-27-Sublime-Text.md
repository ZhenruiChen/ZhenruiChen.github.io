---
layout:    post
tags:      技术 Mac
title:     Sublime Text 3 常用功能
keywords:  Sublime Text plugins 插件
description: Sublime Text 是一款跨平台的文本编辑器，通过数量众多的插件可以实现便捷的编辑和调试，比如 C++ 编译、Latex 编译等。

---

Sublime Text 是一款跨平台的文本编辑器，通过数量众多的插件可以实现便捷的编辑和调试，比如 C++ 编译、Latex 编译等。下面列出了博主常用的一些插件。

# Package Control

command + shift + p 打开命令行

```
Package Control: Install Package
Package Control: Remove Package
```

## Essential Plugins

+ AlignTab
+ AutoFileName
+ BrackeHighlighter
+ Clickable URLs
+ Codecs33
+ ColorPicker
+ ConvertToUTF8
+ Git
+ GitGutter
+ LaTeXTools
+ MarkdownEditing
+ Package Control
+ PackageResourceViewer
+ SideBarEnhancements
+ SideBarFolders
+ SublilmeAStyleFormatter
+ SyncedSidebarBg
+ Terminal
+ WordCount

## Build with C++11

```
{
	"shell_cmd": "g++ -std=c++11 \"${file}\" -o \"${file_path}/${file_base_name}\"",
	"file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
	"working_dir": "${file_path}",
	"selector": "source.c, source.c++",

	"variants":
	[
		{
			"name": "Run",
			"shell_cmd": "g++ -std=c++11 \"${file}\" -o \"${file_path}/${file_base_name}\" && \"${file_path}/${file_base_name}\""
		}
	]
}
```

## Latex for Mac OSX

1. 使用 Package Control 安装插件 LaTeXTools
2. 安装 Mac OSX 下的 PDF 软件 Skim. 可以通过 brew cask 或者直接在网站下载
3. 设置 Skim 反向链接到 Sublime Text. Skim --> Preferences --> Sync --> Preset: Sublime Text.
4. 在Sublime Text 中编辑 Latex 文件，使用 `Command + B` 进行编译和预览。



