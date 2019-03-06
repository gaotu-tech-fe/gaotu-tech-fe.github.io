# 博客源文件

# 使用：
## 1. 安装
```bash
git clone git@github.com:gaotu-tech-fe/gaotu-tech-fe.github.io.git
```

切换至`dev`分支（master存放编译完后文件），安装依赖
```bash
cd gaotu-tech-fe.github.io
git checkout dev 
npm install
```

## 2. 写文章
1. 新建md
```bash
hexo new post 你的文章标题
```
2. 编辑md  
详细语法自行搜索  
```yml
---
title: 文章的标题
date: 创建日期 （文件的创建日期）
tags: 标签
categories: 分类
---

# 此处是你的内容
```
## 3. 合并到dev提交
## 4. 在dev上发布
1) 先清理
```bash
hexo clean
```
2) 再编译
```bash
hexo g
```
3) 如需要在本地预览
```bash
hexo s
```
3) 发布
```bash
hexo d
```
## end