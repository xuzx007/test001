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
