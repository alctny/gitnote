# submodule 的使用

## 添加子模块

```bash
git submodule add https://github.com/example/repo.git libs/repo
```

## 初始化和更新子模块

第一次克隆包含子模块的项目时需要初始化和更新子模块

```bash
git submodule init
git submodule update
git submodule update --init --recursive  # 递归更新
```

## 查看子模块状态

```bash
git submodule status
```

## 更新子模块

```bash
git submodule update --remote
```

## 提交子模块更新

进入子模块目录，并提交子模块的的修改

```bash
cd libs/repo
git add .
git commit -m "Update submodule"
```

回到主仓库并提交子模块的修改

```bash
cd ../..
git add libs/repo
git commit -m "Update submodule reference"
```

## 移除子模块

1. 删除子模块条目：

```bash
Copy code
git submodule deinit -f -- path/to/submodule
```

2. 删除子模块目录：

```bash
Copy code
rm -rf .git/modules/path/to/submodule
```

3. 从 .gitmodules 文件中移除子模块配置：

```bash
Copy code
git config -f .gitmodules --remove-section submodule.path/to/submodule
```

4. 从主仓库中删除子模块路径：

```bash
Copy code
git rm -f path/to/submodule
```