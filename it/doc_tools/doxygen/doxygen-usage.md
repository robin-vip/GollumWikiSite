# doxygen usage#

**操作系统：Ubuntu 20.04 LTS**

## 配置doxygen
doxygen的使用方法通过doxygen -h (也可以参考使用手册/usr/share/doc/doxygen/doxygen_manual.pdf)

* 快速创建配置文件doxyfile
```
doxygen -s -g doxyfile                简化版的doxyfile，没有很多注释信息。
doxygen -g doxyfile
```
这种创建方式比较简单，但是配置比较复杂。

* 可视化配置  
doxygen-gui提供了doxywizard可视化配置工具  
在shell终端输入下面的命令可以启动可视化配置工具
```
doxywizard                           新建一个Doxyfile，并进行配置。
doxywizard Doxyfile                  从已有配置文件Doxyfile读取配置。
```

## 代码注释规范

## 链接  
[Doxygen 注释语法和使用](https://blog.csdn.net/qq_41204464/article/details/102458103)  