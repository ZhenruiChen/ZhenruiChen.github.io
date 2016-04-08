---
layout:    post
tags:      工具
title:     Beamer 显示中文的模板
keywords:  Beamer 显示中文 模板   
description: Beamer 是 Tex 中制作演示文稿的一种文档类型，非常适合用于准备学术报告的演示文稿，或者符号和公式比较多的展示材料。随着 ctex 和 xeCJK 包的推出，在 Beamer 中使用中文已经非常容易。

---

Beamer 是 Tex 中制作演示文稿的一种文档类型，非常适合用于准备学术报告的演示文稿，或者符号和公式比较多的展示材料。随着 ctex 和 xeCJK 包的推出，在 Beamer 中使用中文已经非常容易。

下面给出了一个现实中文的 Beamer 最小模板。使用时可以在此基础上添加其他功能。图表的插入跟其他类型的 Latex 文档类似。参考文献的使用之后有时间了再更新。

编译环境是 Windwos 8 中文版64位 + Tex Live 2015 完整版。编译时选择 xeLatex，不是常见的 pdfLatex 或者 Latex 编译方式。 xeLatex 方式编译时要求文本的编码格式是 UTF-8，其他格式可能会出问题。目前主流的 Latex 编辑器都是默认设为 UTF-8，其他格式需要先转换再编译。 

```
%!TEX program = xelatex

\documentclass{beamer}
\usepackage{xeCJK}

%\setCJKsansfont{黑体}
\usetheme{Madrid}

\title[标题]{完整标题}
\author[作者]{完整作者}
\institute[单位]{完整单位列表}
\date[日期]{完整日期}

\begin{document}

%------------------------------------------------

\begin{frame}
    \titlepage
\end{frame}

%------------------------------------------------

\begin{frame}{Outline}
    \tableofcontents
\end{frame}

%------------------------------------------------

\section{背景介绍}

\begin{frame}
\frametitle{中文}

\begin{block}{模块}
内容
	\begin{itemize}
	    \item 条目1
	\end{itemize}
\end{block}

\end{frame}

%------------------------------------------------

\end{document}
```



