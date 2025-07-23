---
title: 基于Hexo的博客前端搭建
date: 2025-03-01 21:35:04
tags:
---

本文讲述了用Hexo搭建博客的全过程。

# 一、前言

首先说说我为什么心血来潮要写一个博客，是因为我有一个同学，他搭建了一个看起来非常高级的博客，使我觉得非常厉害。至于为什么用Hexo，是因为他说用Hexo会很方便，比较适合初学者上手，于是我就开始了第一次搭建博客的尝试。

# 二、搭建过程

## （一）安装

网上搜索hexo，进入它的[官网](https://hexo.io/)。按照[官方文档](https://hexo.io/zh-cn/docs/)进行安装。

这里简述安装过程：

1. 安装 Git 和 Node.js 

2. 安装Hexo

   ```
   npm install -g hexo-cli
   ```

3. Hexo安装完成后执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件

   ```
   hexo init <folder>
   cd <folder>
   npm install
   ```

## （二）预览和配置主题

### 1、预览

输入 `hexo s`，浏览器访问 `http://localhost:4000` 即可查看默认博客。

```
hexo clean && hexo g && hexo s 
```

以后每次运行上面这条命令就可以

### 2、配置主题

我不是特别喜欢默认的主题，于是查找了配置主题的方法（以 Butterfly 为例）

1. **下载主题**
   在博客根目录执行：

   ```
   git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
   ```

2. **启用主题**
   修改 `_config.yml` 中的 `theme` 字段：

   ```
   theme: butterfly
   ```

3. **安装主题依赖**

   ```
   npm install hexo-renderer-pug hexo-renderer-stylus --save
   ```

4. **自定义主题样式**
   修改 `themes/butterfly/_config.yml`，调整导航栏、背景图片、头像等（需参考主题文档）。

### 3、切换主题

Butterfly比较花里胡哨了，我喜欢更精简一点的主题，于是决定使用[NexT](https://theme-next.js.org/)。

按照[NexT的官方文档](https://theme-next.js.org/docs/getting-started/)进行安装，以下简述安装过程：

1. **Downloading NexT**

   在博客根目录执行：

   ```
   npm install hexo-theme-next
   ```

2. **Upgrading NexT**

   ```
   npm install hexo-theme-next@latest
   ```

3. **Enabling NexT**

   修改 `_config.yml` 中的 `theme` 字段：

   ```
   theme: next
   ```

### 4、自定义主页

由于NexT默认主页显示为所有博客的内容，我希望主页显示为一个菜单或者个人简介，因此需要自定义配置。

1. 在根目录的`source`目录下，新建一个`index.md`文档，并添加：

   ```markdown
   ---
   title: Welcome to Arctic's Blog!
   date: 2025-03-01
   layout: page
   ---
   ```

   或者通过以下命令新建：

   ```
   hexo new page --path index "Welcome to Arctic's Blog!"
   ```

2. 修改根目录下的`_config.yml`文件的`index_generator`项

   ```yml
   index_generator:
     path: /default-index/ #此处为修改部分
     per_page: 0
     order_by: -date
   ```

   修改的目的是使Hexo框架的默认主页指向一个无效值

### 5、配置菜单

```yml
menu:
  home: / || fa fa-home
  archives: /archives/ || fa fa-archive
  Docs: #显示在侧边
    default: /docs/ || fa fa-book
    Getting Started: #显示在顶部
      default: /getting-started/ || fa fa-flag
      Installation: /installation.html || fa fa-download #显示在顶部第二栏
      Configuration: /configuration.html || fa fa-wrench
    Third Party Plugins:
      default: /third-party-services/ || fa fa-puzzle-piece
      Math Equations: /math-equations.html || fa fa-square-root-alt
      Comment Systems: /comments.html || fa fa-comment-alt

```



## （三）写作

具体内容查看官网教程[writing部分](https://hexo.io/zh-cn/docs/writing)

1. 通过以下命令创建新文章/页面

   ```
   hexo new [layout] <title>
   ```

   我的配置中默认的 layout 是 post

2. Hexo 有三种默认布局：`post`、`page` 和 `draft`。 每个布局创建的文件会被保存到不同的路径。 新创建的帖子被保存到 `source/_post` 文件夹。

   | 布局类型  | 用途                    | 存放路径         | 生成规则                   | 常用命令                |
   | :-------- | :---------------------- | :--------------- | :------------------------- | :---------------------- |
   | **post**  | 正式发布的博客文章      | `source/_posts`  | 直接渲染为可访问的公开页面 | `hexo new post "标题"`  |
   | **page**  | 独立页面（如关于/归档） | `source` 根目录  | 生成独立 URL 的非文章页    | `hexo new page "标题"`  |
   | **draft** | 未完成的草稿文章        | `source/_drafts` | **默认不渲染**，需手动发布 | `hexo new draft "标题"` |

   通过post新建的文章，其地址就是_posts下的路径；

   通过page新建的文章，其地址就是source下的路径，需要在**根目录下**的`_config.next.yml`添加菜单项：

   ```yml
   menu:
     Home: /
     Archives: /archives/
     About: /about/  # 对应 page 路径
   ```

   

## （四）部署

以下是一键部署操作，如果要将源文件夹上传到 GitHub，参考官方文档中的[部署操作](https://hexo.io/zh-cn/docs/github-pages)。

1.  **创建 GitHub 仓库**
   新建仓库，命名为 `robotjiang1.github.io`

2. **配置 SSH 密钥**

   - 生成密钥：`ssh-keygen -t rsa -C "你的邮箱"`，将 `id_rsa.pub` 内容添加到 GitHub 的 SSH Keys 设置中。
   - 测试连接：`ssh -T git@github.com`。

3. **修改部署配置**
   在 `_config.yml` 末尾添加：

   ```yml
   deploy:
     type: git
     repo: git@github.com:robotjiang1/robotjiang1.github.io.git
     branch: main  # 或 master，根据仓库分支名调整
   ```

4. **安装部署插件并发布**

   ```yml
   npm install hexo-deployer-git --save
   hexo clean && hexo g && hexo d  # 清理、生成静态文件、部署
   ```

   完成后，访问 `https://robotjiang1.github.io` 即可查看在线博客。

   如果在本地更改设置后页面未及时刷新，`Ctrl + F5`刷新浏览器缓存。

