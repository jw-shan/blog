---
layout: post
title:  "Using VSCode as LaTex IDE"
date:   2021-03-08 16:00 
categories: VSCode Latex
---

This article record the configuration of the VSCode as a LaTeX IDE.

### 1. Deploy LaTex Environment

Install [TexLive](https://www.tug.org/texlive/).

### 2. Configure VSCode

1. Install [VSCode](https://code.visualstudio.com/).

2.  Press `Ctrl+Shift+X`, then install then `LaTex Workshop` extension.

3. Press `Ctrl+,` to enter setting,  modify setting.json as follows

   ```json
   {
           "latex-workshop.latex.recipes": [
       {
           "name": "pdflatex -> bibtex -> pdflatex*2",
           "tools": [
               "pdflatex",
               "bibtex",
               "pdflatex",
               "pdflatex"
           ]
       },
       {
           "name": "xelatex",
           "tools": [
               "xelatex"
           ]
       }, {
           "name": "latexmk",
           "tools": [
               "latexmk"
           ]
       }
       ],
       "latex-workshop.latex.tools": [{
       "name": "latexmk",
       "command": "latexmk",
       "args": [
           "-synctex=1",
           "-interaction=nonstopmode",
           "-file-line-error",
           "-pdf",
           "%DOC%"
       ]
       }, {
       "name": "xelatex",
       "command": "xelatex",
       "args": [
           "-synctex=1",
           "-interaction=nonstopmode",
           "-file-line-error",
           "%DOC%"
       ]
       }, {
       "name": "pdflatex",
       "command": "pdflatex",
       "args": [
           "-synctex=1",
           "-interaction=nonstopmode",
           "-file-line-error",
           "%DOC%"
       ]
       }, {
       "name": "bibtex",
       "command": "bibtex",
       "args": [
           "%DOCFILE%"
       ]
       }],
       "latex-workshop.view.pdf.viewer": "tab",
       "latex-workshop.latex.autoBuild.run": "never", 
       "latex-workshop.latex.autoClean.run": "onBuilt", 
       "latex-workshop.latex.clean.fileTypes": [
         "*.aux",
         "*.bbl",
         "*.blg",
         "*.idx",
         "*.ind",
         "*.lof",
         "*.lot",
         "*.out",
         "*.toc",
         "*.acn",
         "*.acr",
         "*.alg",
         "*.glg",
         "*.glo",
         "*.gls",
         "*.ist",
         "*.fls",
         "*.log",
         "*.fdb_latexmk",
       ],
       "editor.wordWrap": "on",
       "git.ignoreWindowsGit27Warning": true,
       "workbench.colorTheme": "ReUI Default Bordered (react-native)",
       "workbench.sideBar.location": "right"
   
     }
   ```

4. Reset

   

---

## Choose compiler

```latex
%!TEX program = pdflatex
```

