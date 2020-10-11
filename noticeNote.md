如果有什么我无法正常的推送的情况，先从远程拉一遍。
另，直接`git pull` & `git push`有可能遇到各种问题，在pull和push的时候，最好写明自己要往哪里push和pull。

我刚才又下意识的想要用tree，然而windows怎么可能给我用tree呢？也许这是妄想——且慢，连vim都能用，为什么不能tree呢？

方法很简单，我百度到了两个其中一个需要修改环境变量，我修改了，但没用。
第二个不需要修改环境变量，而且有用，想必第一个方法是过时了吧。

方法是，在官网下载tree.exe，复制到`git/usr/bin` 下,然后现在，可以tree了，我之后还可以找找有没有什么其他的命令支持windows，一并复制到git/usr/bin下，那这个gitbash就将变得很好用了。

另外，我之前一直很纳闷如果需要管理的文件非常多的话，git如何添加呢？难道一个一个手动添加？事实上，git有办法，使用下面两个命令即可
`git add .`
`git add -A`
这两个命令可以批量添加工作区的变化。

现在我那这个文件试一试git的合并功能。命令是
`git merge fearute1`

操作完毕，得到经验：
1、在switch的时候，要把工作区暂存一下，不然可能丢失进度
2、这点很重要，在merge之前，应该add和commit一下。

现在开始学习bug分支的内容，目前已经将学过的内容梳理一遍，bug分支之后就是新内容了。

现在开始试试stash。

现在开始试试`cherry-pick`命令.

yes


注意：
当我们这样写的时候，发生了什么？

`git push origin master` 将本地的master和远程同名的master合并。
相当于`git push origin master:master`

`git pull origin master` 这只是将远程的origin master拉取并且合并到**当前**的分支。
相当于`git pull origin master:<当前分支>`
