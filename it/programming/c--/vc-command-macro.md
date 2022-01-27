# VC Command Macro usage

## 命令
* `#pragma once`

* `#pragma comment(lib, "wsock32.lib")`

## 宏定义
* WIN32_LEAN_AND_MEAN
```
#define WIN32_LEAN_AND_MEAN
```
1. 不加载MFC所需的模块。 如果你的工程不适用MFC, 就加上这句，这样一来在编译链接时，包括最后生成的一些供调试的模块时，速度更快，容量更小。
2. 这个是针对Win32 相关的头文件的，比如在包含WIN32/MFC SDK 头文件之前定义些宏，可以通过预处理来关闭掉一些不太常用的系统接口或参数，这样可以加快编译的速度。 可以参考Windows.h文件里和 WIN32_LEAN_AND_MEAN 相关的部分。