# commit 的拆分和合并

## 合并 commit

```txt
🦚>git dog
* a06a129 (HEAD -> main) sss
* 447a478 a
* 6ce446a main.txt
* 93b1c9a demo.txt
* 6db24bb init
```

如果 commit 的颗粒度太小需要合并可以通过 `git reabse -i` 实现。加入你需要合并 6ce446a 和 447a478，那么你可以如下进行操作：

1. 使用 `git rebase -i  6db24bb` 进入交互模式

这个地方的 `6db24bb` 是你需要合并的最早的 commit 的之前的 commit（只要比需要合并的 commit 都早即可，不必刚好是前一个）。这时候你会进入编辑模式，在你需要合并的 commit 前把 pick 修改为 s（**只能合并相连的 commit**）。

类似于下面这样

```txt
p 93b1c9a demo.txt
s 6ce446a main.txt
s 447a478 a
p a06a129 sss
```

2. 保存并填写新的 commit 信息

保存修改并退出会进入一个新的编辑页面，可以修改之前的 commit 信息。修改 commit 信息并保存退出即可完成 rebase，既完成多个 commit 的合并.

## 拆分 commit

> 下面的 6db24bb 指的是需要拆分的 commit 的前一个 commit

1. 使用 `git rebase -i 6db24bb` 进入交互式 rebase 模式
2. 在需要拆分的 commit 前把 pick 修改为 e
3. 保存并退出编辑模式(此时 HEAD 已经移动到 `6db24bb` 的下一个 commit)
4. 使用 `git reset HEAD^ --mixed` 将记录回滚到 `6db24bb`
5. 使用 `git add`,`git commit` 重新提交文件
6. 使用 `git rebase --continue` 继续 rebase
7. 结束
