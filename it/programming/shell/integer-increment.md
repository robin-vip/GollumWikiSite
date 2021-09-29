<h1>integer increment</h1>
shell整型变量自增

## 方法：
* declare -i  声明整型变量
<pre>
sunrise@ubuntu:~$ declare -i x=1
sunrise@ubuntu:~$ x+=1
sunrise@ubuntu:~$ echo $x
2
</pre>

* 使用let命令
<pre>
sunrise@ubuntu:~$ i=1
sunrise@ubuntu:~$ let i+=1
sunrise@ubuntu:~$ echo $i
2
sunrise@ubuntu:~$ let i+=1
sunrise@ubuntu:~$ echo $i 
3
</pre>

* 使用(())
<pre>
sunrise@ubuntu:~$ i=1
sunrise@ubuntu:~$ ((++i))
sunrise@ubuntu:~$ echo $i
2
</pre>

* 使用expr命令
<pre>
sunrise@ubuntu:~$ i=1
sunrise@ubuntu:~$ i=`expr $i + 1`
sunrise@ubuntu:~$ echo $i
2
</pre>

* 使用$(())
<pre>
sunrise@ubuntu:~$ i=1
sunrise@ubuntu:~$ i=$(($i + 1))
sunrise@ubuntu:~$ echo $i
2
</pre>

* 使用$[]
<pre>
sunrise@ubuntu:~$ i=1
sunrise@ubuntu:~$ i=$[$i + 1]
sunrise@ubuntu:~$ echo $i
2
</pre>

## 备注：
<pre>
1. 使用i=$(expr $i + 1)比i=`expr $i + 1`要好些
2. 使用(())或者$(())速度要比expr快
3. 如果不考虑速度问题，涉及到不同平台的兼容，最好使用expr
4. Bash(sh)上使用比较多的情形:let,expr,(())
</pre>

