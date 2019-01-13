# JRebel

## 认证服务搭建

- 服务器安装docker服务;
- 下载docker镜像`docker pull qinjiangbo/jrebel-server`;
- 启动容器`docker run -d -p 8081:8081 imageId`;
- 访问`http://服务器IP:8081/`;
- 访问`https://www.guidgen.com/`生成uuid;

## Mac安装JRebel并在Idea中使用

以下关于JRebel的配置可能仅应用于Spring boot + JRebel实现热部署，并不适应所有的项目配置。

### 安装JRebel

`Preferences`-`Plugins`搜索`JRebel`安装`JRebel for IntelliJ`

`Preferences`-`JRebel`-`Chane lisense`更改激活信息

`Preferences`-`JRebel`-`Startup`勾选`Run via IDE`

### 配置JRebel使用

JRebel需要项目编译后才能启用，所以针对Idea需要进行自动编译或快捷键编译的设置。

介绍使用宏进行自定保存编译的快捷键设置：

* `Edit`-`Macros`-`Start Macro Recording`开始宏录制

* 进行宏的录制`Ctrl + s`(保存)-`Ctrl + F9`(编译)

* `Edit`-`Macros`-`Stop Macro Recoriding`结束宏录制

给该宏进行命名，如`JRebel-autoSaveAndMake`

`Preferences`-`Keymap`-`Macros`-`JRebel-autoSaveAndMake`右键`Add Keyboard Shortcut`键入`Ctrl+s`

启用该配置，此时自动保存编译的宏生效。

### 使用JRebel启动Spring boot

`Application.java`右键`Debug with JRebel`

启动工程后，每次修改或添加删除方法之后，只需使用快捷键`Ctrl+s`就可以实现热部署。

