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