# Install sdcv (StarDict Console Version)
系统：Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic-pae i686)

1. 安装sdcv
```
# sudo apt-get install sdcv
```

2. 下载字典

3. 将字典压缩包解压到~/.stardict/dic目录下

4. 在终端使用sdcv命令查询单词
```
# sdcv star
Found 1 items, similar to star.
-->DrEye4in1词典
-->star

[stɑr;stɑ:]
n.[C]
1. 星, 恒星; (日, 月等)天体
2. 星形物; 星号
3. (表示等级等的)星级; 星形勋章
While in Taipei she stayed at a four star hotel.
她在台北停留期间住在一家四星级饭店。
4. 命运; 星象[P1]
5. (电影, 体育等的)明星, 杰出人物
His wish to become a football star has come true.
他想当足球明星的愿望实现了。
vt.
1. 用星形物装饰
2. 用星号标出
3. 使成明星, 由…主演
Yesterday we saw a film starring Charlie Chaplin.
昨天我们看了一部查理。卓别林主演的电影。
vi.
1. 当明星, 主演
She has starred in some thirty films.
她主演过大约三十部影片。
2. 表现出色
He didn't star at that job.
那份工作他做得并不出色。
a.
1. 星的; 星形的
2. 明星的, 主角的
3. 出色的, 优秀的
Tony is the star player on our team.
汤尼是我队的主力。

名复: stars

动变: starred; starred; starring

同义: 
vt.使成为注意中心
headline
excel
feature
n.星体
heavenly body

同义参见: 
decoration
sun
heroine
hero
somebody
queen
```

5. 在vim中调用sdcv查询单词
```
修改~/.vimrc, 在其中加入
" ......................................................................................
" Settings for directory.                                                                 
" ......................................................................................
function! Mydict()
    let expl=system('sdcv -n '. expand("<cword>"))
    windo if expand("%")=="diCt-tmp"|q!|endif
    25vsp diCt-tmp
    setlocal buftype=nofile bufhidden=hide noswapfile
    1s/^/\=expl/
    1
endfunction
nmap F :call Mydict()<CR>

shift + f会在vim左侧分割出字典窗口
```
