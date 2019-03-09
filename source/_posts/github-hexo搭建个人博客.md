---
title: github+hexo搭建个人博客
date: 2019-03-09 15:23:01
tags:
  - github
  - hexo
categories: hexo
---

# GitHub+Hexo 搭建个人博客
**Github Pages**就是github提供的一个静态服务器，可以通过github给你提供的的二级域名来访问你的文件。

## 启用github page  
1. 新建仓库。名称为**你的用户名.github.io**的仓库。（一定要是你的github名！）,记得勾选readme
<img src="https://test-interactive.gaotu100.com/febook/assets/create_github_page.png" width="500px">
2. 就好了，新建一个`index.html`，访问[pangjunpeng.github.io](https://pangjunpeng.github.io)试试看吧  

总之就是可以放一个静态的html上去，你就可以访问了  

而**hexo**，就是一个可以让你写markdown，然后编译为静态html的工具

## Hexo
一个主要关注内容，而不用让你花太多心思在界面设计上的利器。  
<!-- more --> 
### 安装hexo
```bash
$ npm install -g hexo-cli # 如果安不上用sudo
```

### 初始化博客
cd到你喜欢的目录
```bash
$ hexo init <你的博客的文件夹的名字>
```
初始化完之后
```bash
$ cd <你的博客的文件夹的名字>
$ npm install
```
就好了，本地启动一下试试看吧
```bash
$ hexo s
```

### 上传到github  
1. 在github添加你的`ssh key` （如已添加可以跳过）（遇到问题往下翻）
    ```bash
    $ cd ~/.ssh
    $ ls
    ```
    看有没有xxx.pub（一般叫id_dsa.pub），复制里面的内容
    ```bash
    $ pbcopy < ~/.ssh/id_rsa.pub
    ```
    打开github的settings，添加key
    ![](https://test-interactive.gaotu100.com/febook/assets/setting-ssh-key.png)  

    ![](https://test-interactive.gaotu100.com/febook/assets/add-ssh-key.png)  

2. 需要安装`hexo-deployer-git`插件才能上传至github
    ```bash
    $ npm install hexo-deployer-git --save
    ```
    然后在`_config.yml`中添加
    ```bash
    deploy:
    type: git
    repository: https://github.com/xxx/xxx.github.io.git # 需要上传到目标仓库地址
    branch: master # 需要上传到目标仓库分支（github page默认是master，所以这块就写master，当然可以自定义）
    ```
3. 编译上传
    ```bash
    $ hexo clean # 记得清理下上次编译后的文件
    $ hexo g    # 编译生成html文件
    $ hexo s    # 如果要在本地预览
    $ hexo d    # 发布到github上
    ```
4. 查看效果
    输入网址`xxx.github.io`看吧

# 写博客  
1. 新建文章
```bash
$ hexo new post 文章标题
```
2. 编辑md  
详细语法自行搜索  

    ```
    ---
    title: 文章的标题
    date: 创建日期
    tags: 标签
    categories: 分类
    ---
    此处是你的文章内容，用markdown格式编写
    ```
3. 发布  
写完之后
```bash
$ hexo clean    # 清理下上次编译后的文件
$ hexo g        # 编译生成html文件
$ hexo s        # 如果要预览
$ hexo d        # 发布
```

# 建议  
+ 默认主题有点丑，可去[Themes](https://hexo.io/themes/)挑选喜欢的主题并配置
+ 推荐安装`hexo-browsersync`插件来热更新

# 注意  
1. 新建仓库必须添加`readme.md`
2. 添加ssh如果提示`Key is already in use`，参考[此文章](https://blog.csdn.net/itmyhome1990/article/details/42643233)或[这篇](https://liyiye012.github.io/2018/08/21/Hexo+github%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%E9%97%AE%E9%A2%98%E6%80%BB%E7%BB%93/)解决