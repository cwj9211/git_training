# Git Training
>这里是我们到第一节课，讲述的是Git到使用

[这里是详细到Git教程，可以参考它学习更多内容](https://github.com/hengtian/git/blob/master/zh/SUMMARY.md)

### 1. 初始化一个Git支持的项目
```bash
mkdir git_test
cd git_test
git init
```
初始化结果,如下图：
```bash
andy@wenhaoli-pc:~/git/git_test$ git init;ll
总用量 12
drwxrwxr-x 3 andy andy 4096  1月  4 22:00 ./
drwxrwxr-x 6 andy andy 4096  1月  4 21:05 ../
drwxrwxr-x 8 andy andy 4096  1月  4 22:08 .git/

```

### 2. 增加文件到本地仓库中

如果你有N个文件，你可以使用到下面命令来添加他们。

```git add newfile1 newfile2 newfile3 ... newfileN```

Note: 使用命令```git add -h```，可以查看帮助信息。

如果你想要把目录下的文件一次性全部添加，你可以使用：

``` git add . (.代表当前目录)```

你可以使用下面到命令来查看添加后的状态。

```git status```

结果如下：
```bash
andy@wenhaoli-pc:~/git/git_test$ git status
位于分支 master
要提交的变更：
  （使用 "git reset HEAD <文件>..." 撤出暂存区）

	新文件:       newfile3
	新文件:       newfile4

未跟踪的文件:
  （使用 "git add <文件>..." 以包含要提交的内容）

	newfile5
	newfile6
	newfile7

```
newfile3, newfile4是已经添加到暂存区到文件，newfile5,6,7是新建立还没有添加到暂存区到文件。

### 3. 提交改动到本地暂存区

提交改动的部分文件:
```bash

andy@wenhaoli-pc:~/git/git_test$ git commit -m 'test commit' newfile1 newfile2
[master （根提交） 55045b0] test commit
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 newfile1
 create mode 100644 newfile2

```

提交全部有改动的文件:

```git commit -a -m "comments"```

结果如下：

```bash
andy@wenhaoli-pc:~/git/git_test$ git commit -a -m "comments"
[master 2903ce9] comments
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 newfile3
 create mode 100644 newfile4
```

Note: 确保你的提交信息能够包含足够的描述信息，让你可以搞清楚你想要回退到哪个版本。

### 4. 查看历史

现在你需要一个查看旧版本的方法。为了查看提交信息和该次提交的hash值（代表版本的一串数字）可以使用如下命令，使其以每行一个版本的方式输出

```git log --pretty=oneline```

如下：
```bash
andy@wenhaoli-pc:~/git/git_test$ git log --pretty=oneline
2903ce978c30c3c57a9a0d8d64a92a1cb7192879 comments
55045b052b426c0d8d8ffa2d663b26e7d58bb024 test commit
```
注意，你同样可以使用```git log```来输出一个更冗长的信息，每个版本信息占用多行,如下：
```bash
andy@wenhaoli-pc:~/git/git_test$ git log
commit 2903ce978c30c3c57a9a0d8d64a92a1cb7192879
Author: jingxuan1990 <jingxuan2046@126.com>
Date:   Mon Jan 4 22:25:04 2016 +0800

    comments

commit 55045b052b426c0d8d8ffa2d663b26e7d58bb024
Author: jingxuan1990 <jingxuan2046@126.com>
Date:   Mon Jan 4 22:05:42 2016 +0800

    test commit

```

而且,你可以使用```git log --pretty=oneline newfile1```来查看某个具体文件的改动

```bash
andy@wenhaoli-pc:~/git/git_test$ git log --pretty=oneline newfile1
55045b052b426c0d8d8ffa2d663b26e7d58bb024 test commit

```

### 5. 恢复旧版本

想要恢复之前版本的文件，你只需要使用hash值的前几个数字（要保证足够的区分度，请确保该值唯一）：

```git checkout <hash> filename```

比如,```git checkout 179e59467039 filename```

这样会把文件filename的内容回退到179e59467039...这个状态。

### 6. 查看改动

查看文件当前版本和历史版本的区别，你需要指明历史版本的hash值：

```git diff —```

你同样可以比较两个历史版本的差别：```git diff —```
