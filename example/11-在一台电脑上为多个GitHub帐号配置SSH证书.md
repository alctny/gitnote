# 在同一台电脑上为多个 GitHub 帐号配置 SSH 证书

> 1. 首先不同的 GitHub 帐号不允许配置相同的 SSH 证书，所以你需要为你的多个帐号生成不同的证书
> 2. 同一个 GitHub 帐号可以配置多个 SSH 证书，所以工作帐号和个人帐号并没有分离并不需要如此配置

1. 为两个帐号生成不同的证书

```bash
ssh-keygen -f work
ssh-keygen -f life
```

2. 配置证书

```
Host github.com
User git
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/life
Port 443

Host github.wrk
Hostname ssh.github.com
User git
Port 443
PreferredAuthentications publickey
IdentityFile ~/.ssh/work
```

Host 只是一个别名，Hostname 才是真正的托管地址，所以 Host 可以用来区分工作用的 GitHub 和个人使用。

3. 替换仓库关联地址

按照上面的配置个人用的帐号 GitHub 完全不受影响，一切按照原来的使用方式继续使用即可，但是工作用的 GitHub 仓库地址中的 github.com 需要替换为 Host 后面的内容（github.wrk）

```
# 假设原本的项目地址是 git@github.com:google/go.git
# 则在关联远程仓库的时候需要使用如下地址进行替换
git remove add origin git@github.wrk:google/go.git 
```

4. 在 GitHub 上将两个证书分别添加到各自的帐号

