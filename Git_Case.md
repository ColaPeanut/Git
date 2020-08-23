# Git操作案例

## 一、	入门篇
### 如何创建本地仓库？

1.	在需要创建仓库的文件目录下右键打开Git Bash，输入命令：
* git init

​       对应的仓库目录下会出现 .git 文件
2.	直接从远程仓库中克隆某个代码仓库
* git clone 远程仓库地址

### 如何创建远程仓库？

直接到Github上创建一个仓库

### 如何为远程仓库创建别名/如何关联本地和远程仓库？ 

* git remote add 别名 远程仓库地址
  git remote add origin git@github.com:***

### 如何查看远程仓库信息？

* git remote

### 如何修改远程仓库的别名？

* git remote rename 原别名 新别名
  git remote rename orgin new

 

### 如何删除远程仓库？
* git remote rm 远程仓库名
  git remote rm new

### 如何删除本地仓库？

* rm -rf .git

### 如何向远程仓库提交文件？
首先要建立本地仓库和远程的仓库的关联，然后

1.	git add 文件名
把工作目录的某个文件添加到暂存区（stage）
git add 文件名1 文件名2
添加多个文件
git add .
添加所有变化的文件
git add -u 
添加所有已经被add（tracked）的变化的文件
git add -A 
即git add –all的缩写，是上面两个功能的和
2.	git commit -m “提交信息”
把暂存区的所有文件提交到版本库当前分支
3.	git push -u 仓库名/别名 分支
git push -u origin master
把本地库的内容推送到远程仓库
第一次push的时候加上-u参数，Git会把本地分支和远程的分支关联起来，以后就不需要加上-u参数了
git push origin master
	在过程中可以使用git status命令来查看当前的状态

### 如何撤销已经加入暂存区的文件？
	git reset HEAD 文件名
撤销指定文件


	git rm --cached 文件名
撤销指定文件


	git HEAD
撤销所有



### 如何撤销已经commit的文件？
使用git log查看提交日志，找到需要回退到的那次提交的哈希值，即commit_id
回退到某个版本：
git reset --hard commit_id

回退到上个版本
git reset --hard HEAD^

--soft 保留已撤销commit的代码变更，不会撤销git add， 
--mixed 保留已撤销commit的代码变更，撤销git add， 
--hard 删除已撤销commit的代码变更，撤销git add，工作空间回到上一次commit状态

撤销中间的某个commit
git rebase

### 如何撤销已经push到远程仓库的文件？

1.	首先撤销本地分支的提交
2.	git push -f 强制提交，否则会失败，因为本地版本号更小