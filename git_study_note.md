# 1.Git结构

![image-20211209164354730](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209164354730.png)

# 2.Git安装

# 3.Git命令行操作

## 3.0选择文件夹目录或新建一个文件夹

1.选择文件夹目录：前往指定的文件夹，点击右键，运行 “Git  Bash  Here” 指令。

![image-20211207211827368](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211207211827368.png)

2.在任意处，点击右键，运行 “Git  Bash  Here” 指令。再前往指定的的目录。

3.新建文件夹

​	指令：mkdir   文件夹名字

​	效果：

![image-20211207212134632](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211207212134632.png)



## 3.1本地库初始化

指令：git  init

效果：

![image-20211207212438795](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211207212438795.png)

注意：.git 目录中存放的是本地库相关的子目录和文件，不要删除，也不要胡乱修改。



## 3.2设置签名

作用：区分不同开发人员的身份。

辨析：这里设置的签名和登录远程库(代码托管中心)的账号、密码没有任何关系。

形式：

​	用户名：Lucifer

​	邮箱：1355589361@qq.com

命令：

​	项目级别/仓库级别：仅在当前本地库范围内有效

​			git config user.name Lucifer_git_study

​			git config user.email 1355589361@qq.com

![image-20211207213054359](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211207213054359.png)

​			信息保存位置：./.git/config 文件

![image-20211207213449693](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211207213449693.png)

​	系统用户级别：登录当前操作系统的用户范围 

​			git config --global user.name Lucifer

​			git config --global user.email 1355589361@qq.com

![image-20211207213707314](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211207213707314.png)

​			信息保存位置：~/.gitconfig 文件

![image-20211207213831915](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211207213831915.png)

级别优先级：

​	就近原则：项目级别优先于系统用户级别，二者都有时采用项目级别的签名

​	如果只有系统用户级别的签名，就以系统用户级别的签名为准

​	二者都没有不允许

## 3.3基本操作

### 3.3.1状态查看

​	命令：git  status

​	描述：可用于查看工作区、暂存区状态。

### 3.3.2添加至暂存区

​	命令：git  add  [file  name]

​	描述：将工作区的 “新建/修改”添加到暂存区。 

### 3.3.3从暂存区撤销

​	命令：git  rm  --cached  [file  name]

​	描述：将文件从暂存区撤出，恢复至未添加至暂存区前的状态。

### 3.3.4提交至本地库

​	命令：git  commit  -m  "[commit  message]"  [file  name]

​	描述：将暂存区的内容提交到本地库。

### 3.3.5查看历史记录

​	命令：git  log

![image-20211209173433370](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209173433370.png)

​	当历史记录特别特别的多时，屏幕无法一次之内显示全部的历史记录，此时控制屏幕翻页的操作为：

​			b：向前翻页

​			空格：向后翻页

​			q：退出

​	或采用一下指令显示部分历史信息：

​	①只显示索引及提交信息：git  log  --pretty=oneline

![image-20211209175107968](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209175107968.png)

​	②只显示索引末尾几位及提交信息：git  log  --oneline

![image-20211209175144446](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209175144446.png)

​	③只显示索引末尾几位、指针移动步数信息及提交信息：git reflog

![image-20211209175207754](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209175207754.png)

​		HEAD@{移动到当前版本需要多少步}

3.4版本前进后退

​	本质：指针移动

![image-20211209191406364](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209191406364.png)

​	①基于索引值操作（推荐）：git reset --hard  [局部索引值]

​	![image-20211209191600727](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209191600727.png)

​	②使用^符号（只能后退）：git  reset  --hard  HEAD^

![image-20211209191913587](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209191913587.png)

​		注：一个^表示后退一步，n 个表示后退 n 步。

​	③使用~符号（只能后退）：git reset --hard HEAD~n

​		注：n表示后退 n 步。

### 3.3.6reset命令的三个参数对比

①--soft：

​	仅仅在本地库移动HEAD指针。

![image-20211209193733420](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209193733420.png)

②--mixed：

​	在本地库移动HEAD指针。

​	重置缓存区。

![image-20211209193809598](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209193809598.png)

③--hard

​	在本地库移动HEAD指针。

​	重置缓存区。

​	重置工作区。

![image-20211209193914409](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209193914409.png)

### 3.3.7删除文件并找回

前提：删除前，文件存在时的状态提交到了本地库。

操作：git  reset  --hard  [指针位置] 

​		删除操作已经提交到本地库：指针位置指向历史记录。

​		![image-20211209200315134](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209200315134.png)

​		删除操作尚未提交到本地库：指针位置使用 HEAD。

​		![image-20211209200541577](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209200541577.png)

### 3.3.8比较文件差异

将工作区中的文件和暂存区进行比较：git  diff  [文件名]

<img src="C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209202017876.png" alt="image-20211209202017876"  />

将工作区中的文件和本地库历史记录比较：git  diff  [本地库中历史版本]  [文件名] 

![image-20211209202445131](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209202445131.png)

不带文件名比较多个文件：git  diff

![image-20211209202655423](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209202655423.png)

比较两个历史版本：git  diff  [本地库中历史版本]  [本地库中历史版本]

![image-20211209202855253](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209202855253.png)

# 4.分支管理

## 4.1什么是分支

在版本控制过程中，使用多条线同时推进多个任务。 

## 4.2分支的好处

同时并行推进多个功能开发，提高开发效率。

各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。 

## 4.3分支操作

### 创建分支

​	操作：git  branch  [分支名]

![image-20211209210406370](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209210406370.png)

### 查看分支 

​	操作：git  branch  -v

![image-20211209210422945](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209210422945.png)

### 切换分支 

​	操作：git  checkout  [分支名]

![image-20211209210508482](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209210508482.png)

### 合并分支

第一步：切换到接受修改的分支（被合并，增加新内容）上。

​	操作：git  checkout  [被合并分支名]

第二步：执行 merge 命令 

​	操作：git  merge  [有新内容分支名]

![image-20211209211207902](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209211207902.png)

### 解决冲突

冲突的表现：

![image-20211209211809896](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209211809896.png)

冲突的解决：

​	第一步：编辑文件，删除特殊符号。

![image-20211209213013417](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209213013417.png)

![image-20211209213103757](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209213103757.png)

​	第二步：把文件修改到满意的程度，保存退出。

![image-20211209213228892](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209213228892.png)

​	第三步：git  add  [文件名]。

![image-20211209213252636](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209213252636.png)

​	第四步：git  commit  -m "日志信息"（注意：此时 commit 一定不能带具体文件名！！！）。

![image-20211209213350152](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211209213350152.png)

# 5.Git基本原理

## 5.1哈希

![image-20211210105554733](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210105554733.png)

​		哈希是一个系列的加密算法，各个不同的哈希算法虽然加密强度不同，但是有以下 几个共同点：

①不管输入数据的数据量有多大，输入同一个哈希算法，得到的加密结果长度固定。 

②哈希算法确定，输入数据确定，输出数据能够保证不变。

③哈希算法确定，输入数据有变化，输出数据一定有变化，而且通常变化很大。

④哈希算法不可逆 Git 底层采用的是 SHA-1 算法。 哈希算法可以被用来验证文件。

​		原理如下图所示：

![image-20211210105727923](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210105727923.png)

​		Git 就是靠这种机制来从根本上保证数据完整性的。

## 5.2Git版本管理机制

### 	5.2.1集中式版本控制工具的文件管理机制

​		以文件变更列表的方式存储信息。这类系统将它们保存的信息看作是一组基本 文件和每个文件随时间逐步累积的差异。

​		![image-20211210111334903](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210111334903.png)

### 	5.2.2Git 的文件管理机制

​		Git 把数据看作是小型文件系统的一组快照。每次提交更新时 Git 都会对当前 的全部文件制作一个快照并保存这个快照的索引。为了高效，如果文件没有修改， Git 不再重新存储该文件，而是只保留一个链接指向之前存储的文件。所以 Git 的 工作方式可以称之为快照流。

​		![image-20211210111430618](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210111430618.png)

### 	5.2.3Git 文件管理机制细节

​			Git 的“提交对象”：

​			![image-20211210111542529](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210111542529.png)

​			提交对象及其父对象形成的链条：

​			![image-20211210111615654](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210111615654.png)

## 5.3Git分支管理机制

### 		5.3.1分支的创建

​		本质：新建一个指针，指向同一块地址。

​		![image-20211210112151713](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210112151713.png)

### 		5.3.2分支的切换

​		本质：改变HEAD指针指向的地址。

​		![image-20211210112351212](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210112351212.png)

### 		5.3.3分支的管理

​			本质：不同的分支指向不同的指针。

​			![image-20211210112541308](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210112541308.png)



​			![image-20211210112634698](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210112634698.png)

# 6.GitHub

## 6.1创建远程库

![image-20211210133507966](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210133507966.png)

![image-20211210133950275](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210133950275.png)

## 6.2创建远程库地址别名

查看当前所有远程地址别名：git  remote  -v  

![image-20211210134733694](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210134733694.png)

设置某个远程库地址的别名：git  remote  add  [别名]  [远程地址]

![image-20211210134753969](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210134753969.png)

## 6.3推送

​	操作：git  push  -u  [别名/远程地址]  [分支名]

![image-20211210143508614](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210143508614.png)

## 6.4克隆

​	操作：git  clone  [远程地址]

![image-20211210143230577](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210143230577.png)

​	效果：

​		①完整的把远程库下载到本地。

​		②创建远程地址别名。

​		③初始化本地库。

## 6.5拉取

​	操作：git  pull  [远程库地址别名]   [远程分支名]

​	pull=fetch+merge

​	git  fetch  [远程库地址别名]   [远程分支名]

​	git  merge  [远程库地址别名/远程分支名]

​	![image-20211210161114577](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210161114577.png)

## 6.6解决团队协作冲突

​	如果不是基于 GitHub 远程库的最新版所做的修改，不能推送，必须先拉取。

​	拉取下来后如果进入冲突状态，则按照“分支冲突解决”操作解决即可。

## 6.7SSH免密登录

1.进入当前用户的家目录

​	命令：$  cd  ~

2.删除.ssh目录

​	命令：$ rm  -rvf.ssh

3.运行命令生成.ssh密钥目录

​	命令：$ ssh-keygen  -t  rsa  -C  [登录邮箱]

​	（注意：这里-C 这个参数是大写的 C）

4.进入.ssh目录查看文件列表

​	命令：$  cd  .ssh 

​	命令：$  ls  -lF

5.查看 id_rsa.pub 文件内容 

​	命令：$ cat  id_rsa.pub

6.复制 id_rsa.pub 文件内容，登录 GitHub，点击用户头像→Settings→SSH and GPG keys

7.点击New SSH Key

![image-20211210163610868](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210163610868.png)

8.输入复制的密钥信息

![image-20211210163723211](C:\Users\hp\AppData\Roaming\Typora\typora-user-images\image-20211210163723211.png)

9.回到 Git bash 创建远程地址别名

​	命令：git  remote  add  [别名]  [SSH链接]

10.推送文件进行测试

