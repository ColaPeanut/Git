## **一、简介**

首先安装Git, 然后再需要工作的地方右键鼠标，选择git bash进入工作区

## **二、安装和配置**

## **三、基本命令**

### **.gitignore文件**

添加要忽略的、不进行管理的文件

```
*.[oa]  # 忽略.o或.a结尾的文件
!lib.a  # lib.a文件除外（不忽略该文件）
*~  # 忽略所有以波浪线~结尾的文件
/TODO # 仅仅忽略项目根目录下的TODO 文件，不包括subdir/TODO
build/ # 忽略build/ 目录下的所有文件
doc/*.txt # 会忽略doc/notes.txt 但不包括doc/server/arch.txt
```

### **入门**

### **git add**

> 根据文件状态不同，作用不同：跟踪新文件把已跟踪的文件放到暂存区用于合并时把有冲突的文件标记为已解决状态

> 注：后三种用法具体差异未明确

#### **git add 1.txt**

把文件1.txt添加到暂存区（stage）

#### **git add 1.txt 2.txt**

添加多个文件到暂存区

#### **git add .**

添加所有修改、新添加的未跟踪文件到暂存区，不包括删除的文件

#### **git add -u**

添加所有已经被add（tracked）的变化的文件，包括修改、删除

#### **git add -A**

git add –all 的缩写，是上面两个功能的和

### **git commit**

直接运行会进入编辑器，要输入提交说明

#### **git commit -m "提交说明"**

提交并添加说明

#### **git commit --amend**

重新提交

#### **git commit -a -m 'added new benchmarks'**

跳过暂存区，直接从工作区提交所有已经跟踪的文件

### **git push**

#### **git push -u origin master**

第一次推送master分支时，由于远程库是空的，加上-u参数，把本地master分支推送到远程origin主机，同时指 定origin为默认主机，关联起本地和远程分支

#### **git push、git push origin master**

git push 假定已经为该分支定义了remote repository，在这种情况下，将使用默认的远程 origin git push origin master 表示您要推送到特定的远程设备，在本例中为`origin`;

master指定了要推送到的远程分支

这仅在您在代码库中创建了多个远程存储库的情况下才重要。如果您只提交到一个远程存储库(在这种情况下，只是您的GitHub存储库)，那么两者之间没有任何区别。

### **git remote**

#### **git remote**

查看远程仓库名字

#### **git remote -v**

查看远程仓库名字和地址

#### **git remote remove origin**

取消本地仓库和远程仓库的关联

#### **git remote rename origin new_origin**

修改远程仓库别名

#### **git remote add origin [git@gitlab.os.adc.com](mailto:git@gitlab.os.adc.com):AI-Tech/PracticeGit.git**

关联本地和远程仓库

#### **git remote rm new**

删除远程仓库

#### **git remote add [name] [url]**

添加一个远程仓库，并命名

### **git log**

查看历史记录

> -p  # 展示每次提交的内容差异-n  # 只显示最近n次更新

### **git status**

查看当前文件所处状态

### **git diff**

查看当前工作目录文件和暂存区文件的具体差异

### **git branch**

#### **git branch**

查看当前分支

#### **git branch -a**

查看所有分支

#### **git branch dev**

创建dev分支

#### **git branch -d dev**

删除dev分支

#### **git branch -D dev**

强行删除dev分支

#### **git branch -f main HEAD^3**

强制将main分支移动到往前三笔提交的位置

### **git checkout**

#### **git checkout dev**

切换到分支dev

#### **git checkout commitId**

切换到某次提交

#### **git checkout --1.txt**

取消对文件1.txt的修改

#### **git checkout -b dev**

创建分支dev，并切换到该分支，相当于以下两条命令

> git branch dev  # 创建分支（复制当前所在分支的内容）git checkout dev  # 切换分支

### **git switch**

#### **git switch -c dev**

表示创建分支dev，并切换到该分支

#### **git switch master**

切换到master分支

### **git merge**

#### **git merge dev**

合并dev分支到当前分支-b

### **git reset**



### **git revert**



### **git cherry-pick**



### **git rebase**



#### **git rebase -i HEAD~3**

交互式rebase

#### **git rebase side1 side2**



### **git fetch**



#### **git fetch [remote-name]**

到远程仓库中拉取所有你本地仓库中还没有的数据



### **git pull**

git pull = git fetch + git merge

#### **git pull --rebase**

git pull --rebase = git fetch + git rebase

### **git tag**

列出现有标签

> git tag -l ""  #  可以执行搜索

#### **git tag v1 C1**

给提交C1打上tag为v1

### **git push origin v1.5**

推送标签到远程服务器

### **rm -rf .git**

删除本地仓库

### **其它命令**

#### **cat**

### **cat 1.txt**

查看文件1.txt？

### **vi**

### **vi 1.txt**

编辑文件1.txt

> i  # 进入编辑模式按esc  # 进入命令行模式:wq  # 保存并退出

### **git mv**

### **git mv A B**

重命名文件A为B

## **四、实战**

### **创建新的本地仓库**

### **1. 直接git clone已经存在的远程仓库**

> git clone [git@gitlab.os.adc.com](mailto:git@gitlab.os.adc.com):AI-Tech/PracticeGit.git

### **2. 新建本地仓库**

首先在github上建立一个空仓库

- 直接git clone到本地

  > git clone [git@gitlab.os.adc.com](mailto:git@gitlab.os.adc.com):AI-Tech/PracticeGit.git

  初始化仓库

  > cd PracticeGittouch README.mdgit add README.mdgit commit -m "add README"git push

- 在本地创建一个git仓库，再与github上的空仓库关联

  > 进入某个已存在的文件夹cd PracticeGit将某个文件夹变为git仓库git init将本地分支与远程分支相关联:git push --set-upstream origin master 或  git push -u origin mastergit add .添加目录下所有的文件git commit提交第一次pushgit push -u origin master  # 后面可以直接 git push

### **向远程仓库提交代码**

1. 把工作目录的某个文件添加到暂存区（stage）

   > git add [README.md](http://README.md)

2. 把暂存区的所有文件提交到版本库的当前分支

   > git commit -m "提交说明"

3. 把本地版本库的内容推送到远程仓库

   > git push -u origin master  # 第一次提交加上-u参数，把本地分支和远程的分支关联起来git push  # 关联后，后面提交可以直接 git push

### **撤销已经加入暂存区的文件**

- 撤销指定文件

  > git reset HEAD 1.txtgit rm --cached 1.txt

- 撤销所有

  > git reset HEAD .

### **撤销已经commit的文件**

- git reset --hard HEAD^ # 回退到上个版本

- 使用 git log 查看提交日志，找到需要回退到的那次提交的哈希值，即commit_id

  > git reset --hard commit_id  # 回退到某个版本

> --soft保留代码变更，不会撤销 git add--mixed  保留代码变更，撤销 git add--hard 删除代码变更，撤销git add，工作空间回到上一次commit状态实践：恢复到未改动时的状态（移除所有新增、修改）

### **撤销已经push到远程仓库的文件**

1. 首先撤销本地分支的提交

2. 强制提交

   > git push -f  # 如果commit失败，可能是项目设置了保护分支不允许强制提交

### **创建新的分支，并推送到远程**

1. 在本地创建新的分支

   > git checkout -b dev

2. 把新建的本地分支push到远程服务器，远程分支与本地分支同名（可以随意起名）

   > git push origin dev:dev前者为本地分支，后者为远程分支

3. 向远程dev分支提交本地修改

   > git push初次push到远程的分支尚未和本地分支建立联系，直接git push会失败git push origin dev这种提交方法是一次性的，无法绑定本地分支和远程分支git push --set-upstream origin dev建立当前本地分支和远程dev分支的联系，后续可以直接使用git push

### **不小心删除分支，恢复分支**

1. 找出要恢复的commitId

   > git log -g

2. 恢复对应提交到dev分支

   > git branch dev commitId

### **删除本地分支**

1. 查看当前所在分支

   > git branch

2. ...

   1. 如果当前所在分支和要删除的分支test相同，则先切换到别的分支

      > git checkout otherbranch

   2. 如果当前分支和要删除的分支不同，直接删除分支test

      > git branch -d test

### **删除远程分支**

- 推送空分支到远程分支dev

  > git push origin  :dev

- 指定删除远程分支dev

  > git push origin --delete dev

### **拉取指定分支的代码**

```
# git clone -b 分支名 项目地址
git clone -b midas-dev ssh://*
```

### **提交到远程出现冲突**

1. 试图推送本地分支到远程

   > git push

2. 如果推送失败，说明远程分支比我们的本地分支更新，需要先试图合并

   > git pull

3. 如果合并出现冲突，则打开文件解决冲突

4. 然后按照正常的流程add、commit、push提交代码到远程就能成功！

## **五、git原理**

## **end**