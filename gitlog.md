# 链接github
## 创建SSH Key
```
$ ssh-keygen -t rsa -C "youremail@example.com"
```
key会保存到用户的`.ssh`目录下。.ssh目录，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥，可以放心地告诉任何人。


把一个以有的本地仓库与github仓库关联。

```
$ git remote add origin git@github.com:yourgitacount/yourgitdir.git
```
远程库的名字就是`origin`，这是Git默认的叫法，也可以改成别的，但是`origin`这个名字一看就知道是远程库。

### 克隆远程库
```
git clone git@github.com:yourgitacount/yourgitdir.git
```

### git远程推送
```
git push -u origin master
git push origin master
```

## 使用多个ssh key
在后台启动ssh-agent
```
$ eval $(ssh-agent -s)
> Agent pid 59566
```
Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace `id_rsa` in the command with the name of your private key file.
```
$ ssh-add ~/.ssh/id_rsa
```

```
$ git config --global user.name "user name"
$ git config --global user.email "email@example.com"
```

查看工作区状态用
```
$ git status
```

如果有状态改变用`diff`查看区别
```
$ git diff
```

用`git log`来查看历史提交记录`--pretty=oneline`参数将历史记录放到一行里
输出
```
$ git log
$ git log --pretty=oneline
```

在Git中用`HEAD`表示当前版本，上一个版本就是`HEAD^`,上上个版本就是`HEAD^^`.
上100个版本写成`HEAD~100`

`commit id`由一串数字和字符来表示版本号。用以下命令可以在不同版本间转换
```
git reset --hard HEAD^
```

```
git reset --hard commit id
```

用`git reflog`来查看历史命令


当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`

当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

## 分支
建立分支并切换到`dev`
```
$ git checkout -b dev

```
或者
```
$ git switch -c dev
```

切换分支`$ git checkout dev`或`$ git switch master`
这两个命令实现的功能是相同的，只是语法上略有不同。$ git switch -b dev 在 Git 2.23 版本之前使用较多，而 $ git switch -c dev 是新的语法。

查看分支
```
$ git branch
```
合并某分支到当前分支`$ git merge <name>`，如出现冲突需要手动更改。

删除分支
```
$ git branch -d dev
```

以图形方式查看分支合并情况`$ git log --graph --pretty=oneline --abbrev-commit`

不使用`Fast forward`试式合并`$ git merge --no-ff -m "merge with no-ff" dev`
