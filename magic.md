# Learn-Git

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
