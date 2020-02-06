---
title: 使用 Github Pages 和 Hexo 搭建个人博客记录
date: 2019-07-12 14:28:11
comments: true
tags: 
- gitpages
- hexo
- Next
- CI
categories:
- github
---

【持续更新】记录个人博客使用过程中的一些配置信息

<!--more-->

#### 一. Github Pages 配置

Github Pages 分为两类：用户主页和项目主页。

- 用户主页

  只需创建一个名称为`{username}.github.io`的项目仓库即可，这里的`username`务必于 Github 用户名相同。Github 会自动识别并将该仓库认定为用户主页仓库。

- 项目主页

  需要在对应的项目仓库中设置：`Setting -> Options -> Github Pages` Source 选项，该项目就可以通过`{username}.github.io/{repo.name}`访问。 

#### 二. 使用 Hexo + Next 生成博客

详情请参考：[【Hexo 文档】](https://hexo.io/zh-cn/docs/)，[【Next 文档】](https://theme-next.org/docs/)；

基本步骤如下：

```shell
# 安装 Hexo
npm install -g hexo-cli
# 生成 Hexo 项目
hexo init [blog-demo]
# clone 用户主页项目
git clone https://github.com/{username}/{username}.github.io.git
# clone & 配置 Next 主题
git clone https://github.com/theme-next/hexo-theme-next themes/next
# 生成项目
hexo generate && hexo deploy
```

持续集成会在后续 CI 详述。

#### 三. 配置

1. 站点 _config.yml

   ```yml
   # 首页文章显示设置
   index_generator：
   	order_by: -date # 按文章创建时间倒序排列
   	per_page: 10    # 10 篇分页
   ```

2. 主题 _config.yml

#### 四. 写

1. Archives

   ```shell
   hexo new post "文章标题"
   ```

   

2. Categories

   1. 生成 categories 页

   ```shell
   hexo new page categories
   # 添加type: "categories"到内容中
   vim source/categories/index.md
   ```

   2. 修改 scaffolds/post.md 添加 "categories:"
   3. 文章中添加分类

3. Tags

   配置方式与 Categories 相同

   ```shell
   hexo new page tags
   # 添加type: "tags"到内容中
   vim source/tags/index.md
   ```

4. About

5. 其他

   - Read more >>

     `<!--more-->` 

#### 五. CI

