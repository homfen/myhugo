+++
title = "Sublime Text Context Menu"
date = "2015-01-19T23:42:53Z"
categories = [
    "工具使用"
]
tags = [
    "Sublime"
]
+++

分享一下如何在Sublime中自定义右键菜单，以Git为例，我们知道Git有很多命令（Sync，Fetch，Show Log等），如果把这些命令加到右键菜单中，是否会方便一些呢？

打开Sublime，选择Tools->New Plugin...

<!--more-->

<img src="/images/post/201505141431596331604040.png"> 

在打开的文件中输入以下代码，TortoiseGit的安装地址自行修改：

```python
import os ,subprocess, sublime_plugin
class SyncCommand(sublime_plugin.TextCommand):
    def run(self, edit):
        file_name=self.view.file_name()
        path=file_name.split("\\")
        path.pop()
        current_directory="\\".join(path)
        command= "cd "+current_directory+" & E:\\program\\TortoiseGit\\bin\\TortoiseGitProc /Command:sync"
        proc = subprocess.Popen(command, shell=True)
        os.kill(proc.pid)

class FetchCommand(sublime_plugin.TextCommand):
    def run(self, edit):
        file_name=self.view.file_name()
        path=file_name.split("\\")
        path.pop()
        current_directory="\\".join(path)
        command= "cd "+current_directory+" & E:\\program\\TortoiseGit\\bin\\TortoiseGitProc /Command:fetch"
        proc = subprocess.Popen(command, shell=True)
        os.kill(proc.pid)

class ShowlogCommand(sublime_plugin.TextCommand):
    def run(self, edit):
        file_name=self.view.file_name()
        path=file_name.split("\\")
        path.pop()
        current_directory="\\".join(path)
        command= "cd "+current_directory+" & E:\\program\\TortoiseGit\\bin\\TortoiseGitProc /Command:log"
        proc = subprocess.Popen(command, shell=True)
        os.kill(proc.pid)
```   

保存的时候，新建一个文件夹，并保存为.py格式。接下来，刚刚新建的文件夹中新建一个“Context.sublime-menu”的文件（注意后缀名），里面的内容比较简单，就是刚刚的那三个命令：

```json
[
     { "command": "sync" },
     { "command": "fetch" },
     { "command": "showlog" }
]
```

ok，重启Sublime，随便打开一个文件，右键，就有了

<img src="/images/post/201505141431596331786864.png">
