# Git教程

## git的介绍

### 什么是git

git是世界上最先进的分布式版本控制系统。
git能够显示每次的文件改动

### 分布式管理系统和集中式管理系统的区别

* 集中式管理系统就是将自己的文件上传到中央处理器中，使用的时候将文件下载下来，要求每次都要联网

* 分布式管理系统表示每个人的电脑上都有一个完整的版本库，安全性比较高。另外，分布式版本控制系统也能使得一个计算机充当中央服务器，用来推送交换大家的修改。

* 如果一台电脑想要使用之前电脑上的历史版本只要同步另一台电脑上的完整历史版本，中央处服务器就像Github一样，我们可以将本地的版本库上传到中央服务器上让其他人下载。

## Git安装

### 使用Git创建版本库

什么是版本库？
版本库就是一个git的仓库，作为我们的工作环境使用，创建仓库的方法：

```git
mkdir learngit
cd learngit
pwd
git init
```

这里mkdir创建一个新的文件夹
cd改变工作目录
pwd查看当前的工作目录
git init 命令就是将当前目录变成一个仓库

* 注意git只能跟踪纯文本方式编写的文件。word是二进制编写的。

* 建议使用UTF—8编写

* 不要使用windows自带的记事本进行编写

## Git的基本操作

### 文件提交的两个过程

1. 首先使用 git add 文件名
这种格式的语句向仓库中添加一个文件，只要文件是在我们的仓库或者子目录下的都可以

2. 使用add命令向仓库中添加了文件之后使用
git commit -m "wrote a readme file"
这种语句向仓库提交修改，其中commit表示将刚才进行的添加上传到记录历史中，之后的引号的内容表示我们对这次修改的说明。之后方便我们使用说明查找到这次的记录。

### 修改文件之后提交文件和查看文件的修改

1. 首先我们对目录下的文件进行修改之后可以使用命令： git status 查看进行的修改
status能够展示我们当前的仓库状态，这个命令就能显示我们的那些文件被修改过以及这个修改我们还没有提交。
2. 对于我们进行了什么还没有提交的修改我们可以使用git diff readme.txt进行查看。
就能显示修改的内容。
3. 之后再次使用add 命令向仓库中添加文件
4. 使用commit命令提交本次修改。

## 实现版本的回溯

1. 首先修改一次文件，之后重新提交

2. 使用git log命令可以查看历史记录中的所有历史记录

3. 如果觉得git log显示的内容太复杂的话可以在后面加上 --pretty=oneline就能显示的比较简洁了。

    ```markdown
    说明我们可以看到很多的字符，这些字符都是我们修改记录的版本号，git使用这些版本号来表示每次的修改，不适用简单的数字，因为数字很可能在之后的多人项目中冲突。
    ```

4. 回到之前的版本，使用命令：git reset --hard HEAD^
这里的head^表示上一个版本如果再加一个^就表示上上个版本，如果是上一百个版本的话就使用HEAD~100来表示。

5. 可以使用cat readme.txt来查看文件的内容

6. 注意我们回溯了之后git log命令就不能显示之后的修改记录了。
    * 如果想要恢复之前的修改的话就要使用版本号了，可以查看之前的log内容找到版本号，使用命令git reset --hard 1094a就能回到之前的版本了，这里的版本号我们不用写全，因为git会自动的查找

    * 如果没有版本号的话，可以使用git reflog命令查看之前的修改记录。来找回版本号。

### 工作区和暂存区

对于一个git工程一共有两个区，一个是工作区一个是版本库，版本库中有两个库一个是暂存区一个是master分支。
在git创建的工作区中有一个git的文件，这个文件是git的版本库，版本库可以看作是stage的暂存区。同时git还会为我们创建一个分支master和一个指向master的指针HEAD.
这里对之前的文件添加过程进行一个讲解：

1. 第一步使用的git add 方法能够实现，将文件修改添加到暂存区中

2. git commit能够实现创建一个master的分支,然后将暂存区中的内容添加到新的master分支中。

### 管理修改

对于每次进行的修改每次进行完修改都要将修改添加到暂存区才行，比如：
第一次修改文件->git add -> 第二次修改文件 ->git commit 这种操作是不会实现将文件添加到分支当中的，因为第二次的修改没有添加到暂存区中只在目前的工作区中。
第一次修改文件->git add -> 第二次修改文件 ->git add -> git commit
使用这种方式修改才能实现对文件的修改。

### 修改的撤销

对于修改有三种情况：

1. 只是在工作区中进行了修改

2. 将工作区的修改提交到了暂存区但是没有commit

3. 将工作区的内容commit了但是没有提交到远程的服务器。

对于上面的三种情况我们可以对修改进行撤销

1. 对于工作区的修改，可以直接对文件进行修改，也就是将文件改回来。或者使用语句 git check --readme.txt
就能实现丢弃工作区的修改了。

2. 对于已经提交到暂存区的修改我们可以使用
`git reset HEAD <file>`就能实现文件的修改了。这个语句是实现将暂存区的内容退回到工作区中，所以还要使用之前的git check语句将工作区的修改取消

3. 对于已经提交的修改我们可以使用之前学的版本的回溯将文件回溯到之前的版本。

### 删除文件

删除工作区的文件：
rm test.txt就能删除工作区的文件了
这时候工作区和版本库就不一样了。
之后使用git rm就能将文件从工作区中删除，之后再git 
commit 就能将文件从版本库中删除

误删文件之后使用git checkout --test.txt语句可以将文件恢复。

可以恢复，文件因为我们的删除只是将这个分支中的文件删除了，但是之前版本库中的文件还没有删除所以我们可以通过回溯版本将这个文件找回但是注意的是我们进行恢复的话我们在那之后进行的其他文件的修改都会丢失的。

## 远程仓库

首先我们创建一个远程仓库，首先使用命令：
$ ssh-keygen -t rsa -C "your@email.com"
给我们的电脑创建一个key之后将这个key——pub和GitHub中的ssh进行关联。
之后使用github创建一个远程的仓库之后按照仓库的说明使用指令就能实现当前的目录和远程的GitHub的关联了，之后使用命令
git push -u origin master
就能实现我们现在的目录和再GitHub上仓库的关联已经同步了，我们可以发现仓库中变成和我们本地文件已经一样了。
注意我们首次关联仓库的时候使用的是会出现一个报错提示：

```markdown
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
RSA key fingerprint is xx.xx.xx.xx.xx.
Are you sure you want to continue connecting (yes/no)?
```

这里要输入yes之后再使用的时候就不会出现这个错误了。
所以我们要做的就是平时在本地进行开发，有网络的时候将我们的数据使用git push 的命令将文件同步到远程的GitHub仓库中去，实现一个远程的保存。

```git
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/Mr-several/Csharp.git
git push -u origin master
```

## git的分支管理

什么是分支：
我们使用分支可以创建一个自己的分支，之后我们可以在这个分支上独立的工作之后我们可以将这个分支合并到原来的分支上。这样既安全有能不影响别人的工作。

### 分支的创建和合并

*****
对于**分支的解释**：
首先HEAD指向当前的工作目录不管是master还是分支。
对于Git而言master表示主分支也就是主线，之前进行的操作都是在这个线上进行的。
使用HEAD来指向当前的工作区，没有修改的时候HEAD指向的是master也就是主线，之后我们创建新的分支dev，这时候HEAD的指针指向dev，不在指向master，dev的指向和master的指向是一样的，之后对dev分支进行修改
之后的修改就是在dev这个分支上的修改了，这时候master的指向位置不会改变，只是dev的指向位置向后移动了一格。
在dev的工作完成之后将dev分支合并到master上就是修改master的指向位置到dev的指向位置，之后可以删除dev指针了。
*****

1. `git checkout -b dev`
创建dev分支，使用check命令加上-b表示创建分支并且转换到分支上。相当于两个指令：
git branch dev
git checkout dev
这时候发现git bush的工作分支已经发生改变了。

2. `git branch`
可以查看所有的分支，并且在当前的分支前面会有一个*号

3. 之后在dev分支上使用add 命令和commit命令就能实现提交

4. `git checkout master`
可以实现转换回master上。但是这时候dev分支上的工作还没有提交到master上，所以要合并工作成果。

5. `git merge dev`
这是将dev分支上的工作合并到当前分支上也就是主分支master上。

6. `git branch -d dev`
删除dev分支，因为已经完成合并了。
再使用git branch查看分支现在就只剩下master分支了

7. `git switch -c dev`
创建并且切换到新的dev分支

8. `git switch master`
直接切换到已有的分支上


