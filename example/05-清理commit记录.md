# 清理提交记录

## 回滚

最开始因为不懂 Git 导致 Commit 记录一团糟糕，那么你可以使用 [回滚](../04-回滚.md) 中所说的 reset 来对历史记录进行清理

- Step-1: 查询提交历史

使用 `git log` 查询你想回到的最早的一次 commit，并复制其 hash。

```sh
git log
```

- Step-2: reset

将代码回滚到指定的 commit，但是保留文件变更（回滚了记录，但没有回滚文件）。

```sh
git reset <hash>
```

## 交互式回滚

- Step-1: 查询提交历史

使用 `git log` 查询你想回到的最早的一次 commit，并复制其 hash。

```sh
git log
```

- Step-2: 使用 -i 参数进入交互式

```sh
git rebase -i <hash>
```

在弹出的文本编辑器中，将你想要合并的 commit 前面的 pick 改为 squash 或者 s（表示 squash）。保存并关闭编辑器。然后在下一个弹出的编辑器中，编辑合并后的提交信息。保存并关闭编辑器后，Git 就会将这些 commit 合并为一个，并且你可以编辑合并后的提交信息

## squash

如果你知道要合并的 commit 相邻并且是最近的几次提交，你也可以使用 git merge --squash 命令。首先，确保你在要合并的分支上，然后执行：

```sh
git merge --squash <branch_name>
```

这将把 <branch_name> 分支上的所有提交合并到当前分支，并把它们作为未提交的更改暂存。然后你可以通过 git commit 来创建一个新的提交，它包含了所有这些更改。

## 把当前修改追加到上一次 commit

用于当前的修改已经 add 到暂存区，但还没有 commit，使用下面的命令可以把当前的修改添加到上次的 commit 记录，然后修改 comit 日志

```sh
git commit --amend
```