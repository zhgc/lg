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
+ 远程仓库
