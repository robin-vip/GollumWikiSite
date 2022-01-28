# VC Command Macro usage

## 命令
* `#pragma once`
让同一文件不会被include多次。 "同一文件"是指物理上的一个文件，而不是指内容相同的两个文件。无法对一个头文件中的一段代码作`#pragma once`声明，而只能针对文件。  
在C/C++中，`#pragma once`是一个非标准但被广泛支持的方式。  
`#ifndef`是C/C++语言的标准支持， 它不仅能保证同一文件不会被包含两次，也能够保证不同文件完全相同的内容不会被包含两次。

* `#pragma comment(comment-type[, "commentstring"])`
comment-type 是一个预定义的标志符，指定注释的类型，通常应该是：complier, exestr, lib, linker之一。  
commentstring: 是一个提供为comment-type提供附加信息的字符串。  
remarks:  
1. compiler: 放置编译器的版本或者名字到一个对象文件，该选项是被linker忽略的。
2. exestr: 在以后的版本将被取消。
3. lib: 放置一个库搜索记录到对象文件中，这个类型应该是和commentstring (指定要linker搜索的lib的名称和路径)。 这个库的名字放在Object文件的默认库搜索记录的后面，linker搜索这个库就像在命令行输入这个命令一样。可以在一个源文件中设置多个库记录，它们在object文件中的顺序和在源文件中的顺序一样。如果默认库和附加库的次序是需要区别的，使用Z编译开关是防止默认库放到object模块。
4. linker: 指定一个连接选项，这样就不用在命令行输入或者在开发环境中设置。


## 宏定义
* WIN32_LEAN_AND_MEAN
```
#define WIN32_LEAN_AND_MEAN
```
1. 不加载MFC所需的模块。 如果你的工程不适用MFC, 就加上这句，这样一来在编译链接时，包括最后生成的一些供调试的模块时，速度更快，容量更小。
2. 这个是针对Win32 相关的头文件的，比如在包含WIN32/MFC SDK 头文件之前定义些宏，可以通过预处理来关闭掉一些不太常用的系统接口或参数，这样可以加快编译的速度。 可以参考Windows.h文件里和 WIN32_LEAN_AND_MEAN 相关的部分。