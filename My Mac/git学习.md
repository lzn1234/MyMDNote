### git 相关学习



#### 构建本地版本库







#### 工作区和版本库的概念



##### 什么是工作区（Working Directory）？

顾名思义，工作区就是你工作时使用的部分，一般你看到的目录都是工作区的文件



##### 什么是版本库（Repository）？

在使用 git 进行版本管理时，你的项目中一般会有一个隐藏的 `.git` 文件，这就是版本库。

这个版本库主要由 **暂存区（stage）**、**分支（master）**组成。同时在分支中有一个**HEAD指针**，它指向的当前项目对应的版本。



##### 添加文件到版本库的过程

- 第一步使用 `git add filename` 命令把 *工作区* 里的文件添加到 *暂存区* 中
- 第二步使用 `git commit -m "commit detail"` 将 *暂存区* 里的文件提交到 *master* 分支中

你每次的 **commit** 操作都相当于*游戏中的存档*，即保存当前项目的版本，但和存档有些不同的是，commit 不会覆盖掉之前的版本，而是将每次提交的版本都按照提交时间存储在了 master 中。



![0](/Users/zhennan/Public/Typora Project/0.jpeg)

##### 

#### 常用命令

##### git add

添加文件到暂存区

```bash
// 添加指定文件到暂存区
git add filename

// 添加所有文件到暂存区
git add .				 
```



##### git commit

将暂存区的文件提交到分支上

```bash
git commit -m "commit detail"
```



##### git status

 做两次比较，工作区 VS 暂存区，暂存区 VS 分支版本

```bash
git status 
```



##### git diff

- 但暂存区为空时，进行 **工作区 VS 分支版本**
- 当暂存区部位空时，比较 **工作区 VS 暂存区**

```bash
git diff
```



