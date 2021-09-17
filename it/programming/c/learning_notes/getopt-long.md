<h1>getopt_long</h1>

```
       getopt, getopt_long, getopt_long_only, optarg, optind, opterr, optopt - Parse command-line options
```
```
#include <unistd.h>  
extern char *optarg;  
extern int optind, opterr, optopt;  
#include <getopt.h>
int getopt(int argc, char * const argv[],const char *optstring);  
int getopt_long(int argc, char * const argv[], const char *optstring, const struct option *longopts, int *longindex);  
int getopt_long_only(int argc, char * const argv[], const char *optstring, const struct option *longopts, int *longindex);
```

参数以及返回值介绍（以上三个函数都适用）：

1、argc和argv和main函数的两个参数一致。

2、optstring: 表示短选项字符串。
```
形式如“a:b::cd:“，分别表示程序支持的命令行短选项有-a、-b、-c、-d，冒号含义如下：
(1)只有一个字符，不带冒号——只表示选项， 如-c 
(2)一个字符，后接一个冒号——表示选项后面带一个参数，如-a 100
(3)一个字符，后接两个冒号——表示选项后面带一个可选参数，即参数可有可无，如果带参数，则选项与参数直接不能有空格
    形式应该如-b200
```

3、longopts：表示长选项结构体。结构如下：
```
struct option 
{  
     const char *name;  
     int         has_arg;  
     int        *flag;  
     int         val;  
};  
eg:
 static struct option longOpts[] = {
      { "daemon", no_argument, NULL, 'D' },
      { "dir", required_argument, NULL, 'd' },
      { "out", required_argument, NULL, 'o' },
      { "log", required_argument, NULL, 'l' },
      { "split", required_argument, NULL, 's' },
      { "http-proxy", required_argument, &lopt, 1 },
      { "http-user", required_argument, &lopt, 2 },
      { "http-passwd", required_argument, &lopt, 3 },
      { "http-proxy-user", required_argument, &lopt, 4 },
      { "http-proxy-passwd", required_argument, &lopt, 5 },
      { "http-auth-scheme", required_argument, &lopt, 6 },
      { "version", no_argument, NULL, 'v' },
      { "help", no_argument, NULL, 'h' },
      { 0, 0, 0, 0 }
    };
```

(1)name:表示选项的名称,比如daemon,dir,out等。

(2)has_arg:表示选项后面是否携带参数。该参数有三个不同值，如下：
```
           a: no_argument(或者是0)时 ——参数后面不跟参数值，eg: --version,--help
           b: required_argument(或者是1)时 ——参数输入格式为：--参数 值 或者 --参数=值。eg:--dir=/home
           c: optional_argument(或者是2)时  ——参数输入格式只能为：--参数=值
```

(3)flag:这个参数有两个意思，空或者非空。
```
a:如果参数为空NULL，那么当选中某个长选项的时候，getopt_long将返回val值。
eg，可执行程序 --help，getopt_long的返回值为h.             
b:如果参数不为空，那么当选中某个长选项的时候，getopt_long将返回0，并且将flag指针参数指向val值。
eg: 可执行程序 --http-proxy=127.0.0.1:80 那么getopt_long返回值为0，并且lopt值为1。
```

(4)val：表示指定函数找到该选项时的返回值，或者当flag非空时指定flag指向的数据的值val。

4、longindex：longindex非空，它指向的变量将记录当前找到参数符合longopts里的第几个元素的描述，即是longopts的下标值。

5、全局变量：
```
    （1）optarg：表示当前选项对应的参数值。

    （2）optind：表示的是下一个将被处理到的参数在argv中的下标值。

    （3）opterr：如果opterr = 0，在getopt、getopt_long、getopt_long_only遇到错误将不会输出错误信息到标准输出流。opterr在非0时，向屏幕输出错误。

    （4）optopt：表示没有被未标识的选项。
```

6、返回值：
```
     （1）如果短选项找到，那么将返回短选项对应的字符。

     （2）如果长选项找到，如果flag为NULL，返回val。如果flag不为空，返回0

     （3）如果遇到一个选项没有在短字符、长字符里面。或者在长字符里面存在二义性的，返回“？”

     （4）如果解析完所有字符没有找到（一般是输入命令参数格式错误，eg： 连斜杠都没有加的选项），返回“-1”

     （5）如果选项需要参数，忘了添加参数。返回值取决于optstring，如果其第一个字符是“：”，则返回“：”，否则返回“？”。
```

注意：
```
    （1）longopts的最后一个元素必须是全0填充，否则会报段错误

    （2）短选项中每个选项都是唯一的。而长选项如果简写，也需要保持唯一性。
```

代码
```
#include <iostream>
#include <unistd.h>
#include <getopt.h>
using namespace std;

int main(int argc, char **argv)
{
    int opt;
    int digit_optind = 0;
    int option_index = 0;
    /*
     * 形式如“a:b::cd:“，分别表示程序支持的命令行短选项有-a、-b、-c、-d，冒号含义如下：
     * (1)只有一个字符，不带冒号——只表示选项， 如-c 
     * (2)一个字符，后接一个冒号——表示选项后面带一个参数，如-a 100
     * (3)一个字符，后接两个冒号——表示选项后面带一个可选参数，即参数可有可无，如果带参数，则选项与参数直接不能有空格
     * 形式应该如-b200
     */
    char *optstring = "a:b:c:d";

    static struct option long_options[] = {
        /*
         * no_argument (即 0) 表明这个长参数不带参数（即不带数值，如：--name）
         * required_argument (即 1) 表明这个长参数必须带参数（即必须带数值，如：--name Bob）
         * optional_argument（即2）表明这个长参数后面带的参数是可选的，（即--name和--name Bob均可）
         */
        { "reqarg", required_argument, NULL, 'r'},
        { "noarg", no_argument, NULL, 'n'},
        { "optarg", optional_argument, NULL, 'o'},
        { 0, 0, 0, 0}
    };

    /*
     * 如果longindex非空，它指向的变量将记录当前找到参数符合longopts里的第几个元素的描述，即是longopts的下标值。
     * optind表示的是下一个将被处理到的参数在argv中的下标值。
     */
    while((opt = getopt_long(argc, argv, optstring, long_options, &option_index)) != -1)
    {
        cout << "opt = " << opt << endl;
        cout << "optarg = " << optarg << endl;
        cout << "optind = " << optind << endl;
        cout << "argv[optind -1] = " << argv[optind - 1] << endl;
        cout << "option_index = " << option_index << endl;
    }

    return 0;
}
```

运行测试：
```
root@Tk:~/git/Cplusplus/test/getopt# ./a.out -a 100 -b 200 --reqarg 
opt = 97
optarg = 100
optind = 3
argv[optind -1] = 100
option_index = 0
opt = 98
optarg = 200
optind = 5
argv[optind -1] = 200
option_index = 0
./a.out: option '--reqarg' requires an argument
opt = 63
```








