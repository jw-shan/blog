---
layout: post
title:  "Running jupyter notebook in specified directory"
date:   2020-03-31 16:00 
categories: Linux WSL
---

We always need to run jupyter notebook in a specified directory.

A common method is to change the default dir in the configuration file. Another valid method is to change dir in `cmd` command first and then run jupyter, just like:

```bash
cd /d E:\PythonProject\
jupyter notebook
```

But it seems a little inconvenient. We give two simple method using registry of windows and  `cmdtool` of [WSL terminal](https://mskyaxl.github.io/wsl-terminal/README.zh_CN.html) respectively.

## Registry in windows platform

- 按快捷键 `win+R` 并输入 `regedit` 打开注册表
- 找到 `计算机\HKEY_CLASSES_ROOT\Directory\Background\shell`
- 右键-新建-项，可将其命名为`jupyter`（或者任意其他名称）
- 在默认的数据可添加你想要显示的文字，如“Open Jupyter notebook here”
- 右键`jupyter`-新建-项，并命名为`command`，将其数值改为`cmd.exe "--working-dir" "%v." "/k C:\Users\Administrator\Anaconda3\Scripts\jupyter-notebook.exe"`，其中`xx\xx.exe`是你系统中jupyter notebook文件
- 此时在文件夹中右键已经显示在此处打开jupyter notebook
- 如果你想要更改右键显示的图标，可以右键`jupyter`-新建-字符串值，命名为`icon`，数值改为你下载的.ico图标文件即可
- 若你想要实现右键文件夹时实现同样功能，只需要在`计算机\HKEY_CLASSES_ROOT\Directory\shell`中进行相同的操作即可。

## WSL

- First running `tools/1-add-open-wsl-terminal-here-menu.js` and `tools/2-add-wsl-terminal-dir-to-path.js`.

- When you want to run jupyter in a folder `A`, just open terminal in `A`, and then execute `cmdtool wstart jupyter notebook`.

- You can set a shortcut in WSL, for example:

  ```bash
  alias nb="cmdtool wstart jupyter notebook"
  ```

  Then execute `nb`.

