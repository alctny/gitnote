# 清理提交记录

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
