<h1>Git archive</h1>

```
一般的压缩工具（tar，7zip， Winzip， rar等）在工作区归档时可能会将版本库（.git目录）包含其中，甚至将工作区的忽略文件，
临时文件也包含其中。git archive 可以避免这种情况。
```
    * git archive 支持的归档文件格式
```
$ git archive -l
tar
tgz
tar.gz
zip
```
    * 归档分支或commit
```
git archive --format tar.gz --output "output.tar.gz" master
master: 将master分支归档， 可以是commit id, 或者HEAD.
--format: 指定归档文件格式，如不指明此项，则根据--output中的文件名推断文件格式.
```
    * 归档指定文件,目录
```
git archive -o output.tar.gz HEAD myfile mydir1 mydir2
```
    * 基于tag归档
```
git archive --format=tar --prefix=1.0/ v1.0 | gzip > output-1.0.tar.gz
基于tag v1.0 建立归档，并且归档中的文档添加目录前缀 1.0
```