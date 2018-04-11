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
默认克隆的是远程仓库的 master 分支
```

**克隆远程非 master 分支：**

方法一：

```
git branch -r 查看远程分支
git branch -a 查看所有分支
git checkout origin/分支名 
```

方法二：

```
git branch 分支名  在本地建立一个分支
git checkout 分支名  切换到该本地分支
建立上游分支的关联：
    git pull
    git branch --set-upstream-to=origin/远程分支名 本地分支名
    git pull
add,commit,push.
```



**分支管理：**

1. **创建与合并分支 **

![](/assets/Git.png)![](/assets/Git1.png)

master 指向提交，HEAD 指向当前分支。

```
查看当前分支：git branch
                该命令会列出所有分支，当前分支前面会标一个*号
创建分支：git branch dev
切换分支：git checkout master ————> 切换回主分支
创建+切换分支：git checkout -b dev
                创建并切换到该分支，相当于git branch dev加上git checkout dev.
合并某分支到当前分支：git merge dev
删除分支：git branch -d dev
```

2.**解决冲突：**

当Git无法自动合并分支时,就必须首先解决冲突。解决冲突后,再提交,合并完成。

用 git log --graph 命令可以看到分支合并图。

```
git log --graph --pretty=oneline --abbrev-commit
```

3.**分支管理策略：**

通常，合并分支时，Git 会用 Fast forward 模式，但这种模式下删除分支会丢掉分支信息

如果要强制禁用 Fast forward 模式，Git 就会在 merge 时生成一个新的 commit

这样，从分支历史上就可以看出分支信息

```
合并：git merge --no-ff -m "merge with no-ff" dev
                --no-ff 参数表示禁用 Fast forward 模式
         因为本次合并要创建一个新的 commit ，所以加上 -m 参数，把 commit 描述写入
```

**分支策略：**

* master 分支非常稳定，仅用来发布新版本，平时不能在上面干活
* dev 分支不稳定，干活都在 dev 分支上，再把 dev 分支合并到 master 分支上

4.**Bug 分支：**

* 修复 bug 时，我们会通过创建新的 bug 分支进行修复，然后合并，最后删除
* 当手头工作没有完成时，先把工作现场 git stash 一下，然后去修复 bug 
* 修复后再 git stash pop ，回到工作现场

```
git status 查看是否有未提交的工作
    git stash 将当前工作现场“储藏”
        git status 查看工作区是干净的
            git checkout master 回到需要修复的分支
                git checkout -b issue-101 创建临时分支
修复 bug 
git add readma.txt && git commit -m "fix bug 101" 提交
    git checkout master 切换到 master 分支
        git merge --no-ff -m "merged bug fix 101" issue-101 合并
            git branch -d issue-101 删除临时分支     
修复完成
git checkout dev 回到原先分支继续干活
    git status 查看工作区是干净的
        git stash list 查看，工作现场还在
            git stash apply 恢复，恢复后 stash 内容不删除
            git stash drop 删除 stash 内容
                git stash pop 恢复的同时把 stash 内容也删除
                    git stash list 查看，stash 没有任何内容
```

可以多次 stash ，恢复的时候先用 git stash list 查看，然后恢复指定的 stash ：

```
git stash apply stash@{0}
```

5.**Feature 分支：**

每添加一个新功能，最好新建一个 feature 分支，在上面开发，完成后合并，最后删除该 feature 分支

假设要开发代号为 Vulcan 的新功能：

```
git checkout -b feature-vulcan 创建分支
git add vulcan.py 
git commit -m "add feature vulcan" 开发完后提交
git checkout dev 切回 dev ，准备合并
```

由于某种原因，该新功能要取消，该分支必须销毁：

```
git checkout -d feature-vulcan
销毁失败！因为 feature-vulcan 分支还没有被合并，如果删除将失掉修改
```

如果要强行删除，需要使用命令：

```
git branch -D feature-vulcan
删除成功！
```

6.**多人协作：**

当从远程仓库克隆时，Git 自动把本地 master 分支和远程 master 分支对应起来了

并且远程仓库的默认名称是 origin

```
git remote 查看远程仓库信息
git remote -v 显示更详细的信息
```

上面显示了可以抓取和推送的 origin 的地址，如果没有推送权限，就看不到 push 地址

**推送分支：**

把该分支上的所有本地提交推送到远程库

推送时要指定本地分支，Git 就会把该分支推送到远程库对应的远程分支上

```
git push origin master / git push origin dev
```

* master 分支是主分支，要时刻与远程同步
* dev 分支是开发分支，团队所有成员都要在上面工作，也要与远程同步
* bug 分支只用于本地修复 bug ，没必要推送
* feature 分支是否推送取决于你是否和你的小伙伴合作在上面开发

**抓取分支：**

多人协作时，大家都会往 master 和 dev 分支上推送各自的修改

如果你的小伙伴先推送了他的提交，而你碰巧对同一文件作了修改，则会推送失败

要先用 git pull 把最新的提交从 origin/dev 抓下来，在本地合并解决冲突，再推送

```
先设置本地 dev 分支和远程 origin/dev 分支的链接：
git branch --set-upstream dev origin/dev
再抓取：
git pull
手动解决合并冲突，提交
再推送：
git commit -m "..."
git push origin dev
```

因此，多人协作的工作模式通常是这样：

* 首先试图用 git push origin branch-name 推送自己的修改
* 如果推送失败，需要先用 git pull 试图合并
* 如果合并有冲突，则解决冲突，并在本地提交
* 再用 git push origin branch-name 推送

**标签管理：**

**创建标签：**

* 命令 git tag &lt;name&gt; 用于新建一个标签，默认为 HEAD ，也可指定一个 commit id
* git tag -a &lt;tagname&gt;  -m  "blablabla..." 可以用指定标签信息
* git tag -s &lt;tagname&gt;  -m  "blablabla..." 可以用 PGP 签名标签
* 命名 git tag 可以查看所有标签

**操作标签：**

```
git tag -d v0.1 删除本地标签
git push origin v1.0 推送某个标签到远程
git push origin --tags 推送全部未推送过的本地标签
删除远程标签：
    先从本地删除 git tag -d v0.9
    再从远程删除 git push origin :refs/tags/v0.9
```

**使用 GitHub：**

* 在 GitHub 上，可以任意 Fork 开源仓库
* 自己拥有 Fork 后的仓库的读写权限
* 可以推送 pull request 给官方仓库来贡献代码

**自定义 Git**

让 Git 显示颜色：

```
git config --global color.ui ture
```

**忽略特殊文件：**

、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、

