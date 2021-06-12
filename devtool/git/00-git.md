# :page_with_curl: Git操作

## 一、Git 基本操作

Git 常用的是以下 6 个命令：**git clone**、**git push**、**git add** 、**git commit**、**git checkout**、**git pull**

![](E:\MyDocument\devtool\git\01-git.assets\git-command.jpg)

**说明：**

- workspace：工作区
- staging area：暂存区/缓存区
- local repository：版本库或本地仓库
- remote repository：远程仓库

## 二、本地上传GtiHub

~~~ shell
# 1、打开项目位置，右键选择git bash here
# 2、初始化git
git init
# 3、添加远程仓库地址
git remote add origin https://仓库地址/helloworld.git
# 4、添加要上传的文件(注意最后的符号，表示全提交)
git add .
# 5、添加提交信息
git commit -m '提交信息'
# 6、提交（第一次提交需要添加 -u）
git push -u origin master
~~~

## 三、下载GitHub项目

~~~ shell
git clone https://仓库地址/helloworld.git
~~~

## 四、项目修改后提交

~~~ shell
# 1、更新项目
git pull origin master
# 2、查看项目状态
git status
# 3、添加需要提交的项目
git add 文件
# 4、填写提交信息
git commit -m '提交信息'
# 5、提交
git push origin master
~~~

## 五、查看远程仓库地址

~~~ shell
# 1、查看所有远程仓库地址
git remote
# 2、查看指定远程仓库地址
git remote show origin
# 3、添加远程仓库地址
git remote set-url origin xxx(新的仓库地址)
# 4、删除远程仓库地址
git remote rm origin
~~~

## 六、操作Git分支

~~~ shell
# 1、查看本地所有分支
git branch
# 2、查看远程分支
git branch -r
# 3、创建分支
git branch amazing_new_feature
# 4、获取远程分支（远程分支创建后，如果本地没有对应的分支）
git fetch origin 分支名称
# 5、切换分支
git checkout 分支名称
# 6、合并分支（如果要合并到master,需要先切换到master分支）
git checkout master
git merge 被合并的分支
# 7、删除分支
git branch -d 分支名称
# 	提交删除远程分支
git push origin --delete 分支名称

~~~

## 七、内容添加到暂存区

~~~ shell
# 1、添加单个新增文件
git add test.txt
# 2、提交被新增或者修改的文件，不包含被删除的文件
git add .
# 3、提交所有变化的文件
git add -U --update
# 4、提交已被修改和已被删除文件，但是不包括新的文件
git add -A --all
~~~

## 八、删除文件

~~~ shell
# 1、删除缓存区和本地的文件
git rm -r 文件夹
git rm 文件
# 2、删除缓存区文件
git rm -r --cached 文件夹
git rm --cached 文件
# 3、删除完之后要记得提交
~~~

## 九、版本回退

​	git reset 命令语法格式如下：

>  git reset [--soft | --mixed | --hard] [HEAD]

​	**--mixed** 为默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交(commit)保持一致，工作区文件内容保持不变。

~~~ shell
# 回退所有内容到上一个版本
$ git reset HEAD^
# 回退 hello.php 文件的版本到上一个版本
$ git reset HEAD^ hello.php
# 回退到指定版本
$ git  reset  052e           
~~~

​	**--soft** 参数用于回退到某个版本

~~~ shell
git reset --soft HEAD^1
~~~

​	**--hard** 参数撤销工作区中所有未提交的修改内容，将暂存区与工作区都回到上一次版本，并删除之前的所有信息提交

~~~ shell
# 回退上上上一个版本 
$ git reset –hard HEAD~3  
 # 回退到某个版本回退点之前的所有信息
$ git reset –hard bae128  
 # 将本地的状态回退到和远程的一样
$ git reset --hard origin/master   
~~~

​	**注意：**谨慎使用 –hard 参数，它会删除回退点之前的所有信息。

​	**HEAD 说明：**

- HEAD 表示当前版本
- HEAD^ 上一个版本
- HEAD^^ 上上一个版本
- HEAD^^^ 上上上一个版本
- 以此类推...

可以使用 ～数字表示

- HEAD~0 表示当前版本
- HEAD~1 上一个版本
- HEAD^2 上上一个版本
- HEAD^3 上上上一个版本
- 以此类推...

## 十、比较文件的不同

​	git diff 命令比较文件的不同，即比较文件在暂存区和工作区的差异。

​	git diff 命令显示已写入暂存区和已经被修改但尚未写入暂存区文件对区别。

​	git diff 有两个主要的应用场景。

- 尚未缓存的改动：**git diff**
- 查看已缓存的改动： **git diff --cached**
- 查看已缓存的与未缓存的所有改动：**git diff HEAD** 
- 显示摘要而非整个 diff：**git diff --stat** 

1、显示暂存区和工作区的差异:

~~~ shell
git diff [file]
~~~

2、显示暂存区和上一次提交(commit)的差异:

~~~ shell
$ git diff --cached [file]
或
$ git diff --staged [file]
~~~

3、显示两次提交之间的差异:

~~~ shell
$ git diff [first-branch]...[second-branch]
~~~

##  十一、查看日志

​	Git 提交历史一般常用两个命令：

- **git log** - 查看历史提交记录。

![](E:\MyDocument\devtool\git\01-git.assets\git-1.png)

- **git blame <file>** - 以列表形式查看指定文件的历史修改记录。

![](E:\MyDocument\devtool\git\01-git.assets\git-2.png)

