<h1>string usage</h1>

## 取子串
```
str="20171125"
$ echo ${str:0:4}-${str:4:2}-${str:6}         // str后面第一个":"的数字代表位置，第二个":"后的数字代表长度
2017-11-25
```