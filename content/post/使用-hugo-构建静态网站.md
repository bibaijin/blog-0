+++
title = "使用 hugo 构建静态网站"
date = "2017-05-13T13:35:22+08:00"
categories = ["技术"]
tags = ["blog","hugo"]
+++

## 介绍

hugo 是一个静态网站生成器。它使用 go 语言编写，运行时依赖少，跨平台支持好；
社区庞大，主题样式丰富，是生成博客或文档的好选择。

## 安装

只要[下载对应平台的二进制文件](https://github.com/spf13/hugo/releases)即可运行。

## 生成静态网站

### 新建工程

```
hugo new site ${project-name}
```

### 安装主题

```
cd ${project-name}
git submodule add https://github.com/mgjohansen/hucore.git themes/hucore
```

### 添加博客

```
cd ${project-name}
hugo new post/<FILENAME>.<FORMAT>
# 编辑 post/<FILENAME>.<FORMAT>，保存
```

### 本地预览

```
cd ${project-name}
hugo server
```

### 生成

```
cd ${project-name}
hugo  # 生成的网站默认保存在 public/ 目录下
```

## 部署到 Github Pages

Github Pages 是一个免费的静态页面服务，可以将博客部署在上面。以下使用工程的
`docs/` 目录部署静态页面。

### 新建 Github 仓库

- 在 https://github.com 新建仓库
- 在本地工程里配置 git 远程分支：
  `git remote add origin git@github.com:${username}/${project-name}.git`

### 生成网站

首先，把 hugo 的生成目录改为 `docs`，即

```
cd ${project-name}
echo 'publishDir = "docs"' >> config.toml
```

然后，生成网站，并将工程文件推送到 Github，

```
cd ${project-name}
hugo  # 生成网站
git push origin master  # 将源代码推送到 github
```

### 设置 Github Pages

- 在 Github 对仓库进行设置，选择 `master branch /docs folder` 作为 Pages 的源。

现在，应该可以在 https://${username}.github.io/${project-name}
访问我们的静态网站了。
