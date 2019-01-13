# Mac上使用Git

## 安装Git

- 使用HomeBrew安装Git

```
brew install git
```

- 查看安装的git目录

```
brew list git
```

brew的默认目录为`/usr/local/Cellar`, git的目录一般为`/usr/local/Cellar/git/${version}`

- 查看当前使用的Git版本

使用`Git --version`查看当前启用的Git版本.

- 启用下载的Git

假如下载的版本为2.20.1, 在`.bash_profile`或`.zshrc`文件中添加:

```
 export GIT_PATH=/usr/local/Cellar/git/2.20.1
 export PATH=$GIT_PATH/bin:$PATH
```

保存后加载配置:`source .zshrc`即可生效.

## .gitconfig文件基本配置

```
/* 
 * Set up your Git configuration 
 */

git config --global user.email "you@yourdomain.com"

git config --global user.name "Your Name"

git config --global core.editor "vim"

git config --global color.ui true

git config --global core.quotepath false

git config --global credential.helper osxkeychain

git config --global alias.hist "log --graph --pretty=format:'%Cred%h%Creset %s%C(yellow)%d%Creset %Cgreen(%cr)%Creset [%an]' --abbrev-commit --date=relative"

/* 
 * See Git configuration 
 */

git config --list
```

## 生成ssh key

- 查看是否已经有了ssh密钥：cd ~/.ssh

如果没有密钥则不会有此文件夹, 有则备份删除.

- 生成密钥:

```
ssh-keygen -t rsa -C “you@yourdomain.com”
按3个回车, 密码为空.

nter file in which to save the key (/Users/tilkai/.ssh/id_rsa):
Created directory '/Users/tilkai/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/tilkai/.ssh/id_rsa.
Your public key has been saved in /Users/tilkai/.ssh/id_rsa.pub.
The key fingerprint is:
...
```

GitHub上添加的是生成的`id_rsa.pub`.



