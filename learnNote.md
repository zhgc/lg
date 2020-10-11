+ 设置git参数
    - `$ git config --global user.name "Your Name"`
    - `$ git config --global user.email "email"`  
    - 设置git参数，
    - `--global`表示应用于所有git仓库
+ 设置仓库
    - `$ mkdir learngit`
    - `$ cd learngit`
    - 创建目录，并进入目录
    - `$ git init`
    - 初始化仓库
+ 添加文件
    - 创建一个文件readme.txt
    - `$ git add readme.txt`
    - `$ git commit -m "wrote a readme file"`
    - `git add`表示添加一个文件到仓库，`git commit`表示提交这次修改。
+ 查看状态
    - `$ git status`
    - `$ git diff`
    - `git status`是查看工作区状态，是否有文件被修改过，而`git diff`则是用来查看具体有什么内容被修改了。
+ 查看日志
    - `$ git log`
    - 显示所有版本
    - `$ git log --pretty=oneline`
    - 一个版本显示一行
+ 版本回退
    - `$ git reset --head HEAD^`
    - 在HEAD^的位置写commit_id，即可快速前往版本，但是如果我没有记住commit_id怎么办呢？可以查看操作日志，其中记录下了我们对git的每一次操作，可以在其中找回commit id。
    - `$ git reflog`查看操作日志
    - 通过查看提交历史`git log`,确定要前往那个过去，通过查看命令历史`git reflog`可以确定要回到未来的哪个版本。
    - hard这个单词我记得是努力的，硬的意思，在这里看到hard做参数，我就去查了一下词典，发现hard居然还有“接近地”的意思，大概在这里是取这个意思吧
+ 工作区、版本库
    - 工作区（working directory）就是我们正在使用的目录
    - 版本库（repository）就是工作区目录下的一个`.git`隐藏目录。
+ 删除、撤销
    - git restore <file> 代表撤销上一次的修改，包括对文件内的行修改，也包括直接删除文件。
    - git rm <file>代表从版本库中删除文件，一旦使用了此命令，虽然能从历史中恢复文件，但是将失去上一次的修改
    - 一旦执行 `git rm` 在没有删除文件的情况下，等于同时执行了 `rm`命令。
+ 注意，虽然现在很多地方能输入中文了，比如vi编辑文件时，但也有很多地方对中文输入的支持很不好，比如`commit`提交时的-m消息栏。
+ 远程仓库：创建公钥和私钥，将公钥添加到github主页的ssh key中，私钥在本地不能泄露，然后就可以远程拉取，上传，克隆仓库了
    - `cd ~/.ssh` 进入用户目录下的.ssh目录
    - `ssh-keygen -t rsa -C "邮箱" `通过此命令创建密钥
    - 将公钥添加到github账户，用来确认操作是我干的
    - 将本地仓库上传到github。
        * `git remote add origin git@github.com:<我的用户名>/<想上传到gibhub的仓库>.git`   #这一步是建立远程仓库和本地仓库的关联关系
        * `git push -u origin master` # 这一步将本地内容推送到远程，同时创建本地master和远程master的关联。
        * `git push origin master` #第一次设置了-u参数之后，便可以直接推送了。
    - Note: 如果遇到什么需要警告之类的，输入yes，y即可。他只是再确认是不是你自己在操作。
    - 克隆仓库：
        * 在本地随便什么目录下进行操作，准备好一个远程目录
        * `git clone git@github.com:<我的用户名>/<我想复制的远程仓库名>.git` # 这条命令直接创建目录并将其与远程仓库关联。
+分支管理:
    - `git log --graph` 这个命令可以以可视化的形式查看git 分支与合并情况。
    - `git checkout -b dev` #创建并切换到一个叫dev的分支。其中-b参数表示创建并切换。
    - 上面一条命令相当于两条命令的合写：
        * `git branch dev` #创建分支dev
        * `git checkout dev` #切换到分支dev
    - `git branch` #这条命令相当于查看存在的所有分支。其中当前的分支会被用`*`标记。
    - i can't insert chinese in 9se termux environment,within gboard
    - `git checkout -b dev` equal the two step.
    - use merge command make two branchs to one.
    - `git merge dev` made dev to this branch.
    - 如果我想要以noFastforward模式合并分支，也就是说，避免在删除分支之后丢失分支信息的形式。
        * `git switch -c dev`创建并切换到新的分支dev。
        * `git add <随便什么文件>` 这一步在新分支上随便做点什么。
        * `git switch master` 切换回主分支
        * `git merge --no-ff -m "以非快速模式合并两个分支" dev` 这一步合并两个分支，但使用非快速模式，因此不会丢失分支信息。同时，该模式会生成一个commit，所以需要使用 -m 参数。
    - what im writing .my eng is to bad.
    - a new way to switch branchs
        * `git switch -c dev` mean create and switch to a new branch dev.
        * `git switch -d dev` mean delate branch dev.    - made,wohaishiganlezhebishi,woyihoukendingjuishenbaimingliede.
    - `git stash` 该命令表示储存当前工作区的内容，待处理完其他分支之后再回来处理该分支。
    - `git stash list` 该命令展示所有暂存的工作区内容。通过下面两个命令来恢复。
        * `git stash apply` 该命令应用了储存的工作区内容，但是并不删除stash内容，如果想要删除的话，要通过`git stash drop`命令来删除。
        * `git stash pop` 该命令恢复stash，并且将其删除。
        * `git stash apply stash@{0} `这条命令表示指定恢复储存的工作区内容编号stash@{0}，在stash中可以储存多个工作区内容，这也就是为什么要使用`git stash list`这个命令的原因。
    - 如果我在一个分支上修复了bug，但是同时，我想到，还有很多同源的分支存在这个bug，那么我应该怎么办呢？难道在所有的分支上都修一遍吗？万一有一千条分支存在这个bug呢？
    - 答案是使用cherry-pick命令
    - `git cherry-pick <commitID>`使用该命令即可快速将某个commit的修改在本分支再应用一遍。
    - 在使用merge和cherry-pick的时候，经常出现两边文件合不上的问题。此时必须修改文件内容。因为git会进入一个特殊的模式叫做merging或cherring。
        * 办法1，先将两边文件矛盾的地方修改完毕。
        * 办法2，先使用--quit参数来退出merging模式，然后使用`git branch -D <分支名>`
	* 注意：git add 和git commit这两个命令需要常用，在合并和cherry-pick的时候，或者stash命令，总之，在merge和cherry的时候应该保持工作区是干净的。
    - 有的时候，有一些分支我们已经废弃不用了，但它还有内容没有合并到主分支里，这个时候，如果要删除它，git是会提醒我们，这个操作不行的。因为分支没有被合并，一旦删除就会丢失内容，此时就需要强行删除 用 -D参数
    - 多人开发：好的，以后我打算在dev分支上进行git学习。
    - `git remote -v`
    - `git push origin <branchName>`
    - `git switch -c <newBranchName>`
    - `git branch --set-upstream <branchName> origin/<branchName>`

