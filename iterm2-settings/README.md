# New Mac iterm2配置方案

参考:
> [Mac终端配置，DIY你的Terminal （iTerm 2 + Oh My Zsh）](https://segmentfault.com/a/1190000012786464)
> [Mac终端iTerm2 Solarized主题配置](https://wangwang4git.github.io/blog/2017/04/22/mac-iterm2-solarized-theme-config/)

## 安装iterm2

首先确保已安装git并配置本机公钥到GitHub.
使用HomeBrew安装iterm2.

```
brew cask search iterm2
brew cask install iterm2
```

## 安装oh-my-zsh

官方GitHub: [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

- 使用curl安装
官方推荐curl和wget方式安装, 我使用了curl方式.

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## 配置配色

下载`solarized`配色, [GitHub配色方案地址](git clone https://github.com/altercation/solarized.git)

若只是配置iterm2, 此处可以选择不clone整个git目录, 只选择`iterm2-colors-solarized`目录下的配色方案即可, 该git工程提供了多个配色内容, 如IntelliJ IDEA配色方案和vim配色方案等.

本人将clone项目放置于专门配置mac环境的MacConfig目录下, 同时在本仓库做了文件备份.

将配色方案导入iterm并启用的步骤如下:

1. iterm2中打开preferences, 
2. `Profiles`选项中选择`Colors`，`Color Presets`选项中选择`import...`,
3. 导入clone目录中iterm2-colors-solarized下的配色方案,
4. `Color Presets`下拉列表中勾选`Solarized Dark`, 
5. 重新打开iterm2窗口即可生效.

## 配置oh-my-zsh主题

- 安装oh-my-zsh完成后, 打开.zshrc文件, 修改ZSH_THEME="agnoster", 将主题修改为"agnoster".
- agnoster主题需要依赖特殊字体支持, 因此在不安装特定字体情况下会有乱码, 安装[Meslo](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf)字体(字体名称应该是`Meslo LG M Regular for Powerline.ttf`, 已fork到自己仓库), 下载完成后双击安装, 将其应用到系统字体册.

- iterm2中应用字体: 
> 1. iterm2打开preferences,
> 2. Profiles中选择Text, Change Font,
> 3. Collections中选择all fonts, family中选择Meslo LG M for Powerline,

- 重新打开iterm2窗口即可生效.

## 配置自动提示与命令补全

配置比iterm2自带的更强大的命令提示与补全功能.

1. 克隆git仓库代码到本地~/.oh-my-zsh/custom/plugins路径下:

```
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

编辑.zshrc文件, 修改 plugins=(git z)为plugins=(zsh-autosuggestions git z)

重新打开iterm2窗口, 输入几个命令查看是否生效, 若提示结果不明显, 可使用如下方法修改字体亮度:

```
cd ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
vi zsh-autosuggestions.zsh
# 修改ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=10'
```

## 配置语法高亮效果

- 使用homebrew包管理工具安装 zsh-syntax-highlighting 插件:

```
brew search zsh-syntax-highlighting
brew install zsh-syntax-highlighting
```

安装完成后, 安装进度中会有类似提示:

```
==> Caveats
To activate the syntax highlighting, add the following at the end of your .zshrc:
  source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

- 将`To activate the syntax highlighting, add the following at the end of your .zshrc`给出的source命令配置到.zshrc文件中, 
- 保存之后加载.zshrc配置: `source ~/.zshrc`
- 重新打开iterm2窗口, 即可生效.

##  扩展

### iterm2如何切换bash方案:

1. 切换为zsh: `chsh -s /bin/zsh`,
2. 切换为原bash: `chsh -s /bin/bash`
3. 如何卸载oh-my-zsh: `uninstall_oh_my_zsh`

### agnoster主题的路径前缀过长的问题解决:

编辑`~/.oh-my-zsh/themes/agnoster.zsh-theme`主体文件，将里面的`build_prompt`下的`prompt_context`字段在前面加#注释掉即可.





