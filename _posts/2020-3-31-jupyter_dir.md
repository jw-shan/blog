---
layout: post
title:  "Running jupyter notebook in current directory"
date:   2020-03-31 16:00 
categories: Linux WSL
---

We always need to run jupyter notebook in different directories.

A common method is to change the default dir in the configuration file. Another valid method is to change dir in `cmd` command first and then run jupyter, just like:

```bash
cd /d E:\PythonProject\
jupyter notebook
```

But it seems a little inconvenient. Below is a method using the `cmdtool` of [WSL terminal](https://mskyaxl.github.io/wsl-terminal/README.zh_CN.html).

- First running `tools/1-add-open-wsl-terminal-here-menu.js` and `tools/2-add-wsl-terminal-dir-to-path.js`.

- When you want to run jupyter in a folder `A`, just open terminal in `A`, and then execute `cmdtool wstart jupyter notebook`.

- You can set a shortcut in WSL, for example:

  ```bash
  alias nb="cmdtool wstart jupyter notebook"
  ```

  Then execute `nb`.

