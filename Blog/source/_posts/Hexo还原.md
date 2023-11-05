---
title: Hexo还原
date: 2023-11-04 23:06:50
tags:
---
#### 一般只要推送这几个就行,其他的构建时候会生成
![](https://s2.loli.net/2023/11/04/nIVuFpmGP7hLzo8.png)
#### 从git仓库拉源码
```
git clone https://github.com/***/***.git
```
![](https://s2.loli.net/2023/11/04/2HplXEFq9ykMhf7.png)

#### 到第二级目录,我这里文件夹名字是`Blog`,需要进到这个目录下面需要下载一下`node`依赖包
```
npm install --force
```
#### 安装之后就能用`hexo`了 
- `hexo clean` 清理
- `hexo g` 根据源文件生成网站静态文件
- `hexo s` 本地起来 一般是在`http://localhost:8080/`,发布到`git page`前先可以本地预览一下
- `hexo d` 发布到`git page` 这样就能访问域名或者git hub 地址看见你的博客了
##### 一般的顺序是
> hexo clean >> hexo g >>  hexo d
> s 看个人需求