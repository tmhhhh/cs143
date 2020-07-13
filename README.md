##  SET UP THE ENVIRONMENT(Ubuntu)



[reference](https://courses.edx.org/courses/course-v1:StanfordOnline+SOE.YCSCS1+1T2020/6b750292e90d4950b895f621a5671b49/)



### 1

不用java就不需要装jdk

`sudo apt-get install flex bison build-essential csh openjdk-6-jdk libxaw7-dev`



### 2

```shell
sudo mkdir /usr/class
sudo chown $USER /usr/class
cd /usr/class
```



### 3 

`wget https://courses.edx.org/asset-v1:StanfordOnline+SOE.YCSCS1+1T2020+type@asset+block@student-dist.tar.gz`

or

直接在浏览器搜索`https://courses.edx.org/asset-v1:StanfordOnline+SOE.YCSCS1+1T2020+type@asset+block@student-dist.tar.gz`并用浏览器下载

(repo中也提供了对应的压缩包 `student-dist.tar.gz`)



### 4

`tar -xf student-dist.tar.gz` **注意通过链接下载的文件名很长，可以改成这条语句对应的文件名**

or

在Windows环境下用bannzip解压然后用xftp传送到虚拟机中 **注意当前的目录应该是`usr/class/(all the files)`，但是网站的教程中在class后多了一个文件夹cs143，为了统一，也加上**



### 5

在主目录下执行 **这步没看懂，因为目录下没有cool这个文件夹**

`ln -s /usr/class/cs143/cool ~/cool`



### 6

添加环境变量

```shell
vim ~/.profile	# 也可能是别的文件名
# 在最后一行加上
export PATH=/usr/class/cs143/bin:$PATH	# 同样，这里与官方教程不同，并没有cool目录而且bin目录直接在cs143下
```

退出命令行后重新打开

```shell
echo $PATH	# 查看是否设置成功
```



### 测试



[测试方法](https://courses.edx.org/courses/course-v1:StanfordOnline+SOE.YCSCS1+1T2020/9f961242edfb45eba0969a5a7592916d/)



#### 报错

[reference](https://github.com/afterthat97/cool-compiler#spim-no-such-file-or-directory)

##### spim: No such file or directory

- `sudo apt-get install libc6-i386`

##### libfl.so: undefined reference to 'yylex'

- Set the line `%option noyywrap` in the `cool.flex` file
- Remove the `-lfl` part of the `LIB=` line in the makefile