---
layout: post
title:  "LaTex Template"
date:   2021-05-21 16:00 
categories: Latex
---

This article records some common commands in LaTeX.

### 1. Code blocks

```latex
\usepackage{listings}
\lstset{
 columns=fixed,       
 numbers=left,                                        % 在左侧显示行号
 numberstyle=\tiny\color{gray},                       % 设定行号格式
 frame=none,                                          % 不显示背景边框
 backgroundcolor=\color[RGB]{245,245,244},            % 设定背景颜色
 keywordstyle=\color[RGB]{40,40,255},                 % 设定关键字颜色
 numberstyle=\footnotesize\color{darkgray},           
 commentstyle=\it\color[RGB]{0,96,96},                % 设置代码注释的格式
 stringstyle=\rmfamily\slshape\color[RGB]{128,0,0},   % 设置字符串格式
 showstringspaces=false,                              % 不显示字符串中的空格
 language=r,                                        % 设置语言
}
```

```latex
\begin{lstlisting}
  %codes
\end{lstlisting}
```

### 2. Figure

```latex
\begin{figure}
    \centering 
    \includegraphics[width=0.7\textwidth]{a.png} 
    \caption{Main name}
    \label{fig1} 
\end{figure}
```

