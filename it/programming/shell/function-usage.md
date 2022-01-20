# function usage

## 返回值
* return  
1. return 只能返回数字，不能返回字符串，否则会有错误提示: `numeric argument required`  
2. return 需要和 $? 配套使用, 调用处通过 `$?` 获取函数返回值  
example:
```shell
#/bin/sh
fun_sample() {
    return 25
}
fun_sample
ret_val=$?
```

* echo
1. echo 可以返回字符串  
2. 如果函数调用处将函数返回值赋值给变量时，函数中调用echo语句输出的内容不会再输出到标准输出，重定向到了赋值的变量
3. 用echo返回的函数不能再有其它与返回值无关echo调用，除非是直接退出程序。 否则所有执行到的echo语句的内容都会赋值给变量  
example:
```shell
#/bin/sh
fun_sample() {
    echo "beginning of function."
    echo "string for test"
}
ret_val=$(fun_sample)
```
上面的例子中，"beginning of function." 和 "string for test"都会赋值给ret_val

