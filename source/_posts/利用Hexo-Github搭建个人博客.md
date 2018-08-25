---
title: 利用Hexo+Github搭建个人博客
date: 2018-08-23 20:38:56
tags: Tools
categories: 工具
---
### 一、初始化Node.js
直接去[Node.js官网](https://nodejs.org/en/)下载对应的安装包，直接在电脑上安装即可。

### 二、安装Hexo
使用npm命令来安装Hexo

```
npm install -g hexo
```

然后在桌面上创建一个文件夹，如Blog，cd进入该文件夹执行以下命令，即可在目标文件夹内建立网站所需的所有文件。

```
hexo init
```
然后安装依赖包

```
npm install
```
在博客的对应文件夹中执行以下命令，然后在浏览器输入 http://localhost:4000/ 就可以查看，此时这个博客是本地的，下面我们在将其部署到github上。

```
hexo generate
hexo server
```
### 三、部署本地博客到Github上
#### 1.创建一个仓库，名称必须是 用户名.github.io。
比如：我的用户名是yywolf,仓库名就是yywolf.github.io

#### 2.同步到github上
在博客的本地文件夹中，编辑_config.yml,最底部的deploy

```
deploy:
  type: git
  repo: git@github.com:yywolf/yywolf.github.io.git
  branch: master
```
```
npm install hexo-deployer-git --save

```
3.输入以下命令，然后在浏览器中输入yywolf.github.io就可以访问了。

```
hexo clean
hexo generate
hexo deploy
```
### 四、发布博客
执行
```
hexo new post '文章标题'
```

然后在本地博客目录下的source->_posts路径下可找到新建的文章，然后用MacDown编译器编辑即可。

编译完成之后，执行命令，即可发布到github上。

```
hexo clean
hexo generate
hexo deploy
```

----

### 更换博客主题
1. 在本地博客目录中删除默认的主题文件夹themes。
2. git clone 主题github地址，成功后会出现新的themes文件夹，里面就是新的主题。
3. 修改当前目录下的_config.yml配置文件，找到theme,修改为我们下载的主题文件夹名称。
4. 调试,在 http://localhost:4000 中即可看到效果

```
hexo server --debug
```
5. 确认无误后即可输入命令发布到github上

```
hexo clean
hexo generate
hexo deploy
```


