---
layout: post
title:  "Using VSCode as LaTex IDE"
date:   2021-03-08 16:00 
categories: VSCode Latex
---

This article record the configuration of the VSCode as a LaTeX IDE.

### 1. Deploy LaTex Environment

Install [MacTex](https://www.tug.org/mactex/) for MacOS or [TexLive](https://www.tug.org/texlive/) for windows.

### 2. Configure VSCode

1. Download and install [VSCode](https://code.visualstudio.com/).

2. Press `Ctrl/cmd+Shift+X`, then install then `LaTex Workshop` extension.

3. Press `Ctrl/cmd+Shift+P` and search `json`, then open user setting (JSON).

4. modify setting.json as follows.

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
   }, {
       "name": "xelatex",
       "tools": [
           "xelatex"
       ]
   }, {
       "name": "latexmk",
       "tools": [
           "latexmk"
       ]
   },
   {
       "name": "pdflatex",
       "tools": [
           "pdflatex",
           "pdflatex"
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
   //   "*.aux",
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
     "*.aux",
     "*.glg",
     "*.glo",
     "*.gls",
     "*.ist",
     "*.fls",
     "*.log",
     "*.dvi",
     "*.nav",
     "*.snm",
     "*.vrb",
     "*.fdb_latexmk",
   ],
   "editor.wordWrap": "on",
   "git.ignoreWindowsGit27Warning": true,
   "workbench.colorTheme": "ReUI II Dark (Italic)",
   "workbench.sideBar.location": "right",
   "editor.fontSize": 16,
   "workbench.productIconTheme": "fluent-icons",
   "files.associations": {
       "*.rmd": "markdown"
   },
   "cSpell.userWords": [
       "covariates",
       "debiased",
       "functionals",
       "ignorability",
       "Lipschitz",
       "misspecification",
       "misspecified",
       "Neyman",
       "nonparametrically",
       "pathwise",
       "pointwise",
       "quantile",
       "Schwarz",
       "Semiparametric",
       "unconfounded",
       "undersmoothing",
       "Veff"
   ],
   "remote.SSH.remotePlatform": {
       "1.tcp.ngrok.io": "linux"
   },
   "workbench.editorAssociations": {
       "*.ipynb": "jupyter-notebook"
   },
   "terminal.integrated.inheritEnv": false,
   "security.workspace.trust.untrustedFiles": "open",
   "notebook.cellToolbarLocation": {
       "default": "right",
       "jupyter-notebook": "left"
   },
   "latex-workshop.message.error.show": false,
   "latex-workshop.latex.recipe.default": "lastUsed",
   "latex-workshop.latex.build.forceRecipeUsage": false,
   "window.zoomLevel": -1,
   "workbench.settings.useSplitJSON": true
   }
   ```

5. Save and reset.

   

---

## Choose compiler

```latex
%!TEX program = pdflatex
```

