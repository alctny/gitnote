# 临时保存修改但不提交

如果你需要临时保存当前的修改然后去做其他事情（如 checkout, pull, rebase 等）,那么你可以使用 `git stash`

## 创建 stash

```bash
git stash save "message"
# 或 
git stash
```

创建一个新的 stash，存储当前的所有修改并添加额外信息，如果不需要这额外的信息也可以直接使用 `git stash`。这时所有代码都会回滚到上一次 commit 的状态，所有做出的修改则会被移动到 stash 当中。

## 查看创建的 stash

```bash
git stash list
```

## 恢复某次修改

```bash
git stash apply
# 或
git stash apply stash@{index}
# 或
git stash pop
```

前者可以直接使用上一次保存的 stash，后者可以使用特定的 stash，pop 则会将 stash 恢复后删除该 stash。

## 删除某个 stash

```bash
git stash drop stash@{index}
```