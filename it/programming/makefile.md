# makefile

* 在调用静态库使用-l选项时，需要注意-o选项的目的名要在-l链接的库名之前，否则gcc会认为-l是生成的目标而出错。  
下面这种写法就会报错
```
gcc  -Llib -liniparser build/obj/src/config.o build/obj/src/mkimage.o -o build/mkimage
build/obj/src/config.o: In function `LoadConfig':
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:45: undefined reference to `iniparser_load'
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:50: undefined reference to `iniparser_getlongint'
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:58: undefined reference to `iniparser_getlongint'
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:67: undefined reference to `iniparser_getlongint'
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:75: undefined reference to `iniparser_getlongint'
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:83: undefined reference to `iniparser_getlongint'
build/obj/src/config.o:/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:91: more undefined references to `iniparser_getlongint' follow
build/obj/src/config.o: In function `LoadConfig':
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:108: undefined reference to `iniparser_getstring'
/home/ward/temp/ekt_utilities/support_tools/generate_image/src/config.c:111: undefined reference to `iniparser_freedict'
collect2: error: ld returned 1 exit status
makefile:41: recipe for target 'build/mkimage' failed
make: *** [build/mkimage] Error 1
```
下面这种就没问题
```
gcc  -o build/mkimage build/obj/src/config.o build/obj/src/mkimage.o -Llib -liniparser
```
