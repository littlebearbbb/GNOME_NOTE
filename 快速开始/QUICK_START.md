## 快速开始
> 本篇主要介绍如何快速创建一个插件并且在gnome桌面中应用

### 参考文档

本篇内容主要参考官方文档，附上[传送门](https://wiki.gnome.org/Projects/GnomeShell/Extensions/Writing) 

### 开发环境

我自己的开发环境为ubuntu系统下默认安装了gnome桌面，并且安装visual studio code作为开发工具

### 具体流程

1. 生成一个默认插件
```bash
## -i 命令会引导你键入插件name,description,uuid
## 生成时你可以选择一个有代码的实例项目
gnome-extensions create -i
## 执行上面命令后系统会在下面路径生成uuid文件夹
## 其中包含两个文件
## metadata.json: 标注插件的环境参数
## extension.js: 包含插件的主要逻辑
cd ~/.local/share/gnome-shell/extensions/

## 查看gnome-shell的系统日志
## 通过该命令可以查看当前日志，文档里说是可以发现错误什么的，但是用这种方式debug肯定还是不行，debug部分后续会单独开一个小结
journalctl -f -o cat /usr/bin/gnome-shell

## 应用该插件 (enable后为插件uuid)
gnome-extensions enable example@wiki.gnome.org

## 禁用该插件 (disable后为插件uuid)
gnome-extensions disable example@wiki.gnome.org
```

如果你创建的是一个演示插件并且顺利的话，应用插件后在gnome桌面右上角就会出现一个笑脸的icon，点击它会显示一个PopupMenu，至此我们的开发插件之旅踏出了第一步✨✨✨

