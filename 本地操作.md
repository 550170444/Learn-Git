# Learn-Git-本地操作

## 分布式的优势
1、没有中央服务器

2、安全性高

## Git配置
```shell
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
创建版本库
```shell
$ git init
```
## 文件提交
第一步，用命令git add告诉Git，把文件添加到仓库：
第二步，用命令git commit告诉Git，把文件提交到仓库：
```shell
$ git add readme.txt
$ git commit -m "wrote a readme file"
```
## 查看状态
```shell
$ git status
```
## 查看修改内容
git diff顾名思义就是查看difference，显示的格式正是Unix通用的diff格式，可以从上面的命令输出看到，我们在第一行添加了一个distributed单词。
```shell
$ git diff readme.txt 
```
## 版本回退
在Git中，我们用git log命令查看历史记录：
```shell
$ git log
```
### 版本回退方法
首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交1094adb...（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100
```shell
$ git reset --hard HEAD^
```

### 版本回退后，当前版本以后的log会丢失，可以使用reflog查看所有log
```shell
$ git reflog
```
### 使用版本号进行版本切换
```javascript
$ git reset --hard 1094a
// 后边添加版本号
```
## 工作区-暂存区-版本库-远程仓库
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

[不同区域解释](https://www.liaoxuefeng.com/wiki/896043488029600/897271968352576)

## 撤销修改
git checkout -- file可以丢弃工作区的修改
```shell
$ git checkout -- readme.txt
```
命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：

一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次git commit或git add时的状态。
## 如果已经add了如何撤销
1、用命令git reset HEAD <file>可以把暂存区的修改撤销掉（unstage），重新放回工作区：
```shell
$ git reset HEAD readme.txt
Unstaged changes after reset:
M	readme.txt
```
之后再取消工作区的修改
```shell
$ git checkout -- readme.txt

$ git status
On branch master
nothing to commit, working tree clean
```
# 删除文件
## 1、确定删除
本地删除之后commit
## 2、误删

```shell
$ git checkout -- test.txt
```
git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
##  注意：从来没有被添加到版本库就被删除的文件，是无法恢复的!