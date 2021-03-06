## 快速开始
> 本篇主要介绍如何快速创建一个插件并且在gnome桌面中应用

### 参考文档

本篇内容主要参考官方文档，附上[传送门](https://wiki.gnome.org/Projects/GnomeShell/Extensions/Writing) 

### 开发环境

我自己的开发环境为ubuntu系统下默认安装了gnome桌面，并且安装visual studio code作为开发工具

### 安装一个第三方插件

关于安装第三方插件，可以查看知乎上的一篇文章[传送门](https://zhuanlan.zhihu.com/p/36265103)，亲测可用

### 生成一个默认插件

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
```
## &#x26A0;注意  
应用插件前需要先重启gnome-shell  
重启的方法为alt + f2调出命令行工具，然后输入r或者restart回车执行

```bash
## 应用该插件 (enable后为插件uuid)
gnome-extensions enable example@wiki.gnome.org

## 禁用该插件 (disable后为插件uuid)
gnome-extensions disable example@wiki.gnome.org
```

如果你创建的是一个演示插件并且顺利的话，应用插件后在gnome桌面右上角就会出现一个笑脸的icon，点击它会显示一个PopupMenu，至此我们的开发插件之旅踏出了第一步✨✨✨

## 附录
关于gnome-extensions常用命令
```bash
gnome-extensions --help | gnome-extensions -h: 查询所有命令
gnome-extensions create -i: 创建插件并且加载，执行完需要重启gnome-shell才能加载
gnome-extensions list: 列出现在所有插件
gnome-extensions enable [uuid]: 启用某插件
gnome-extensions disable [uuid]: 禁用某插件
gnome-extensions uninstall [uuid]: 卸载某插件，会删除对应的源文件
gnome-extensions pack [uuid]: 把对应的插件打成zip
```

