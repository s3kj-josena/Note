**初始化一个Git仓库:**使用     git    init     命令。

**添加文件到Git仓库,分两步:**

* 第一步,使用命令     git    add    &lt;file&gt;,注意,可反复多次使用,添加多个文件;

* 第二步,使用命令     git    commit     ,完成。

**要随时掌握工作区的状态:**使用 git    status命令

* 如果 git    status 告诉你有文件被修改过,用 git diff  可以查看修改内容

**版本回退：**

* HEAD指向的版本就是当前版本,因此,Git允许我们在版本的历史之间穿梭,使用命令 git reset --hard    commit\_id    
* 穿梭前,用 git    log 可以查看提交历史,以便确定要回退到哪个版本
* 要重返未来,用 git    reflog 查看命令历史,以便确定要回到未来的哪个版本

**工作区和暂存区：**

* git add 命令实际上就是把要提交的所有修改放到暂存区\(Stage\)
* 然后,执行 git commit 就可以一次性把暂存区的所有修改提交到分支

**管理修改：**

* 每次修改，如果不add到暂存区，就不会加入到commit中

**撤销修改：**

* 场景1:当你改乱了工作区某个文件的内容,想直接丢弃工作区的修改时,用命令 git checkout -- file

* 场景2:当你不但改乱了工作区某个文件的内容,还添加到了暂存区时,想丢弃修改,分两步,第一步用命令 git reset HEAD file ,就回到了场景1,第二步按场景1操作

* 场景3:已提交了不合适的修改到版本库,想要撤销本次提交,参考版本回退一节,不过前提是没有推送到远程库

**删除文件：**

* 命令 git rm 用于删除一个文件

**远程仓库**

1. **添加远程库：**

2. 要关联一个远程库,使用命令 git remote add origin git@server-name:path/repo-name.git

```
git remote add origin git@github.com:s3kj-josena/learngit.git
```

* 关联后,使用命令 git push -u origin master 第一次推送master分支的所有内容
* 此后,每次本地提交后,只要有必要,就可以使用命令 git push origin master 推送最新修改

  1. **从远程库克隆：**

```
git clone git@github.com:s3kj-josena/server-name.git
git clone http://github.com/s3kj-josena/server-name.git
```

**分支管理：**

1. 创建与合并分支
2. 




