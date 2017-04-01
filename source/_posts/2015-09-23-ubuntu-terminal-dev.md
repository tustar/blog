---
layout: post
title: "Ubuntu高效开发终端打造"
date: 2015-09-23 15:34:01
description: ""
category:
summary: "打造类似Mac的开发终端"
tags: [Ubuntu, Terminal]
---

### 安装[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)
```
sudo apt-get install zsh git
sudo shutdown -r now
zsh --version
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.zshrc ~/.zshrc.orig
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
chsh -s /bin/zsh
```

### 安装[autojump](https://github.com/wting/autojump)
```
git clone git://github.com/joelthelion/autojump.git ~/.autojump 
cd .autojump
python install.py
在~/.zshrc或者～/.bash_profile中配置
[[ -s $HOME/.autojump/etc/profile.d/autojump.sh ]] && source $HOME/.autojump/etc/profile.d/autojump.sh
autoload -U compinit && compinit -u
```

### 安装[rvm](https://github.com/rvm/rvm)
```
curl -L https://get.rvm.io | bash -s stable
出错了则执行
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
接着继续
curl -L https://get.rvm.io | bash -s stable
最后运行下面命令，让配置生效
source /home/tustar/.rvm/scripts/rvm
在~/.zshrc或者～/.bash_profile中配置
export PATH="$PATH:$HOME/.rvm/bin"
```

### 安装[ruby](https://www.ruby-lang.org/en/)
```
rvm install ruby
```

###  安装[rubygems](https://rubygems.org/)
```
sudo-get install gem
查看当前使用的源地址
gem sources
删除默认的源地址
gem sources -r url地址
添加淘宝的源地址
gem sources -a http://ruby.taobao.org/
更新源的缓存
gem sources -u
```

### 安装[repo](https://dl-ssl.google.com/dl/googlesource/git-repo/repo)
```
mkdir ~/.repo
curl "http://php.webtutor.pl/en/wp-content/uploads/2011/09/repo" > ～/.repo/repo
在~/.zshrc或者～/.bash_profile中配置
#Repo
export PATH="$PATH:$HOME/.repo/repo"
```

### 安装[gradle](http://www.gradle.org)
```
sudo apt-get remove gradle
下载地址为 http://www.gradle.org/downloads
sudo unzip gradle-2.6-all.zip -d ~/.gradle
在~/.zshrc或者～/.bash_profile中配置
#Gradle
export PATH="$PATH:$HOME/.gradle/gradle-2.7/bin"
```

### 安装[nodejs](https://nodejs.org/en/)
```
从官网下载https://nodejs.org/en/压缩包node-v4.1.1-linux-x64.tar.gz
tar -xzvf  node-v4.1.1-linux-x64.tar.gz 
mv node-v4.1.1-linux-x64 ~/.node
在~/.zshrc或者～/.bash_profile中配置
#NodeJS
export PATH="$PATH:$HOME/.node/bin"
```

### 安装[jekyll](http://jekyllcn.com/)
```
gem install therubyracer
gem install jekyll-sitemap
gem install jekyll
```

### 安装[sqlite3](http://www.sqlite.org/)
```
终端安装命令工具
sudo apt-get install sqlite3
图形界面软件
sudo apt-get install sqlitebrowser
sudo apt-get install  sqliteman
```

### 安装其他命令行
```
sudo apt-get install ant
sudo apt-get install python
sudo apt-get tree
```

### 参考资料
+ [ubuntu 14.04下配置on my zsh](http://blog.csdn.net/eclipse_c/article/details/38801549)
+ [如何修改Ruby的gem源(gem sources)](http://jingyan.baidu.com/article/4853e1e51c770f1909f726fe.html)
+ [Ubuntu之安装Gradle](http://blog.csdn.net/stwstw0123/article/details/47809189)
+ [Ubuntu下Sublime Text 3解决无法输入中文的方法](http://jingyan.baidu.com/article/f3ad7d0ff8731609c3345b3b.html)
+ [unbutu下安装repo并下载源码](http://yinger-fei.iteye.com/blog/1300144)
