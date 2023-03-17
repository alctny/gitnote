# 修改已提交 Git 相关新息

## 取消托管部分文件

### 保留本地文件

当你不小心上传了仓老师的照片，现希望 Git 能取消托管这张照片，但是有想要保留本地文件此时可以使用下面的命令

```bash
git rm --cached kuraki_mai.jpg
```

然后使用 `git commit` 再一次提交，复盖掉之前的提交即可

### 不保留本地文件

如果你不需要保留本地文件只需要去掉 `--cached` 参数即可

```bash
git rm kuraki_mai.jpg
```
