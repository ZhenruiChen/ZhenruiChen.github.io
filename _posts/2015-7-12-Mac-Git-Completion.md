---
layout: post
tags:  git Mac
title: Mac 上配置 git 自动补全
---

Mac 上使用 git 时，自动补全无法使用。需要借助 [Homebrew][] 来下载必要的文件并且重新配置。[Homebrew] 可以轻松地下载 OS X 系统缺失的文件。

[Homebrew]: http://brew.sh/

安装 Homebrew

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

安装 bash-completion 和 git

```
brew update
brew install bash-completion
brew reinstall git # OS X 自带的 git 不是最新的
``` 

配置 bash-completion

```
brew info bash-completion
vim ~/.bash_profile
```

把下面的语句添加到 ~/.bash_profile

```
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```
 
下载 git 源码


```
git clone https://github.com/git/git.git
```

把 git-completion.bash 复制到根目录

```
cp git/contrib/completion/git-completion.bash ~/.git-completion.bash
```

在 ~/. profile 中添加下面的语句，terminal 在启动时会依次遍历下面四个文件。

```
source ~/.git-completion.bash
```

使上面的配置生效

```
source ~/. profile
```
