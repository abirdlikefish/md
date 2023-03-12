# linux 命令行

``ctrl + alt + T``  
打开终端  

## cd
> change directory
- **进入文件**

`` cd ``
`` cd /``
相对路径  
绝对路径


`` cd .. ``
 返回上级目录


`` cd ~ ``
`` cd ``
 回到home

`` cd - ``
回到上一次地址


## pwd
> print working directory
- **显示路径**

## ls
> list
- 显示文件列表

`` ls ``
正常显示

`` ls -a ``
显示全部

`` ls -l ``
`` ls -lh ``
显示详细信息

`` ls -ahl ``
`` ls -la ``
`` ll ``
`` ll -h ``
全部详细信息

` ls filename ` 
查看当前文件信息

` ls a* ` 以a开头  
` ls *a `以a结尾  
` ls a? ` ` ls a?b?s ` 缺?字符
` ls a[abcd]d ` ` ls a[a-d]d ` []中匹配任意一个
` ls \*a ` 查找*a


#### abirdlikefish abirdlikefish
> 用户名 用户组名

#### drwxrwxr-x
> d rwx rwx r-x
1. `d` 文件夹
    `-` 文件
2. `r` 可读
   `w` 可写
   `x` 可执行
   `-` 不可读/写/执行
3. 操作权限
   |rwx|rwx|r_x
   |---|-----|-----
   |当前用户|本组用户|全部用户

---

> 任何文件夹下有隐藏文件`` . ``   `` .. ``  
> `` .  ``  当前文件夹  
> `` .. ``  上级文件夹

---

## chmod
>
更改权限

## mkdir
> make directory

- 创建新文件夹

``` mkdir filename ```
``` mkdir /home/user/Desktop/filename ```
创建filename文件夹

``` mkdir filename1 filename2 filename3```
创建多个文件夹

``` mkdir /home/user/Desktop/filename1/filename2/filename3 -p```
创建多重文件夹

``` mkdir .filename```
创建隐藏文件夹  

``` mkdir /home/user/Desktop/{filename1,filename2,filename3}```
在指定目录下创建多个文件夹

## touch
- 创建空文件
  
用法同```mkdir```  
无```-p```



## gedit

- 打开记事本

``` gedit ```
``` gedit a.txt ```
``` gedit a ```


## rm
> remove

- 删除文件

` rm hello.txt `
` rm hello1.txt hello2.txt`
删除文件

` rm filename -r `
删除文件夹

` rm * `
删除全部文件 除文件夹与隐藏文件

` rm * -r `
删除全部文件 除隐藏文件

## mv

> move
- 移动文件

` mv hello.txt hello1.txt `
改名

` mv filename yrp/filename `
移动文件

` mv hello.txt hello2.txt -v`
显示进度

`  mv hello.txt hello.txt -i `
显示交互


## cp
> copy

- 复制

` cp hello.txt yrp/hello.txt `
复制

` cp hello.txt yrp/hello.txt -v `
显示进度

` cp hello.txt yrp/hello.txt -a `
复制全部信息

` cp hello.txt yrp/hello.txt -i `
显示交互

` cp filename1 filename2 -r `
复制文件夹

## > 
- 重定向

` ls > hello.txt `
将结果写入txt,覆盖

` ls >> hello.txt `
将结果写入txt，不覆盖



## cat

- 显示文件内容

` cat hello.txt `
将hello.txt里内容显示在shell

` cat hello.txt hello1.txt`
将 hello.txt 与 hello1.txt 显示在shell

## more

- 从头显示文件内容

` more hello.txt `
显示文件内容  
`enter` ` ` 向下翻页
`b` 向上翻页
`q` 退出

## |
- 管道

` ls -alh | more `
将左侧输出给右侧处理

## clear
- 清空命令行


## ctrl+c

- 结束命令行

