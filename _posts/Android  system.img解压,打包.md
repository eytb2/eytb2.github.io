## Android  system.img解压,打包

#### 		android4.0之后，system.img文件格式为ext4，如果需要修改system.img文件，该如何做：

###### ubuntu系统，准备工具make_ext4fs、simg2img、mkusering.sh。

###### make_ext4fs、simg2img、mkusering.sh这三个工具可以在源码编译之后的 out/host/linux_x86/bin目录下获取，并将这三个命令复制到ubuntu系统/usr/bin目录。 

###### 解压system.img为system.img.ext4 

```命令：simg2img system.img system.img.ext4 ```

###### 创建system.img.ext4挂载目录tmp 

```命令：mkdir tmp ```

######  挂载system.img.ext4到tmp目录 

```命令：mount -t ext4 -o loop system.img.ext4 tmp ```

###### 进入tmp目录，根据需求修改tmp中的目录 

###### 将tmp目录打包为新的system.img 

```命令：make_ext4fs -s -l 239M -a system system.img tmp ```

###### 关于make_ext4fs、simg2img、mkusering.sh的参数含义可以在终端中直接输入命令，并回车查看。