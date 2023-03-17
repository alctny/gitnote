# 同步 fork 仓库

如果你把一个远程仓库 A fork 到本地,作为仓库 B,你为 B 做出了修改的同时原作者对 A 也做出了修改,这时候你希望获取最新的 A 的代码就可以:

```bash
# 查看本地链接的远程仓库地址
git remote -v
# 添加上游仓库地址
git remote add upstream https://www.github.com/XXXX
# 同步上游仓库
git fetch upstream
# 查看远程分支
git branch -r
```
