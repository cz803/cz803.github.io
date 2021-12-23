---
title: 'hello,Hexo（一）'
date: 2021-12-22 20:19:55
tags: hexo+github，个人博客搭建
---

【本篇文章解决的事情：
		- 搭建hexo博客，并部署到github；
		- 博客源文/源码提交github管理】

- 坑先知： 
	- [hexo官网](https://hexo.io/zh-cn/docs/)查看与node.js的版本对应
	- 重要：github新建的仓库必须用[github用户名].github.io（例如：zhangsan.github.io）,并选择 README 初始化
	- Git Push报错:remote: error: GH007: Your push would publish a private email address. 解决方案：github账户下取消勾选，setting->emails->Keep my email address private

1、准备（可以直接看[hexo官网文档](https://hexo.io/zh-cn/docs/)，全面；也可参照下面这，简洁）
1.1、注册安装
- [官网注册github](https://github.com/)并创建一个新仓库myblog，注意上面提到的命名格式（建议用户名短一点，博客的访问会用上），创建一个新分支blog
- [下载git](https://git-scm.com/)，并安装
- [下载node.js](https://nodejs.org/en/download/)，并安装

1.2、验证
	右键选择Git Bash Here，验证上面两个是否安装成功。

```bash
$ git --version
$ node -v
$ npm -v
```
1.3、配置github信息(用注册的用户名，邮箱)

```bash
$ git config --global user.name 'user name'
$ git config --global user.email 'email.com'
# 检查配置
$ git config --list
```

2、根据[hexo官网文档](https://hexo.io/zh-cn/docs/)建站
	找到一个路径，右键选择Git Bash Here
```bash
# clone仓库
$ git clone 仓库地址
$ mkdir myblog
$ cd myblog
# 安装hexo
$ npm install -g hexo-cli
# 验证
$ hexo -v
```
2.1、建站
```bash
# 在建站的路径下右键打开git命令行
# 初始化
$ hexo init
$ npm install
```
2.2、本地部署测试
```bash
# 编译
$ hexo g
# 本地部署
$ hexo s
```
浏览器打开http://localhost:4000 ，如果没出来，大概率端口占用了
Tips:修改端口号

```bash
$ hexo server -p 端口号
```

3、Hexo和Github Pages绑定（为了别人也可以访问）
3.1、本地生成密钥
```bash
# 用github注册那个邮箱，三个回车，生成密钥id_rsa和id_rsa.pub（默认存储路径是：C:\Users\Administrator\.ssh）
$ ssh-keygen -t rsa -C "email.com"
# 切换目录
$ cd ~/.ssh
$ ls
# 添加密钥到ssh-agent
$ eval "$(ssh-agent -s)"
# 添加生成的SSH key到ssh-agent
$ ssh-add ~/.ssh/id_rsa
```
3.2、登录github网站，头像下settiongs-->SSH and GPG keys-->SSH keys-->New SSH key

将id_rsa.pub文件里的内容复制上去

3.3、测试ssh添加结果
```bash
$ ssh -T git@github.com
```

3.4、hexo中的配置文件_config.yml
```bash
deploy:
  type: git
  # 创建的github的新仓库的ssh地址
  repository: git@github.com:用户名/用户名.github.io.git
  # 对应的新建的仓库的非default分支
  branch: blog
```

4、部署
```bash
# 在博客路径下安装一个扩展
$ npm install hexo-deployer-git --save
```

```shell
# 新建一篇博客，可在cmd中（没配就在博客所在路径下操作）
> hexo new post "title"
```

使用编辑器写好文章，我使用的Typora
```shell
# 生成部署
>hexo d -g
```
5、访问
http://用户名.github.io
https://cz803.github.io/

6、更新博客
6.1、博客更新
```bash
$ hexo clean
$ hexo g
$ hexo d -g
```
6.2、博客源码更新
```bash
$ git pull
$ git add .
$ git status
$ git commit -m "description"
# main是对应的新建的仓库的default分支
$ git push origin main
```

后续计划：
	增加coding，gitee等国内源的部署与源码托管，使访问速度更快
	修改设置博客主题风格，更加个性化，美观
	增加评论功能，站点统计等功能
	添加到谷歌，百度，等引擎的搜索

拓展：
可自定义主题美化，参考hexo官网

参考文献：
[个性化配置，搜索引擎来提高访问](https://www.cnblogs.com/quellanan/p/11613109.html)
[用码云来替代github，访问更快更稳定](https://blog.csdn.net/u012294515/article/details/83045860)
[用码云管理](https://blog.csdn.net/qq_35938621/article/details/107592297)
[增加个性化功能，评论功能等](https://blog.csdn.net/qq_35117024/category_7904399.html)