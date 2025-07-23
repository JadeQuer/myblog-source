# Arctic's Blog Source Code

这是 Arctic's Blog 的源码仓库，使用 Hexo + NexT 主题搭建。

## 在新环境中设置博客

### 前置条件
- Node.js 16+ 
- Git
- SSH密钥配置（用于部署到GitHub Pages）

### 快速开始

1. **克隆仓库**
   ```bash
   git clone git@github.com:JadeQuer/myblog-source.git myblog
   cd myblog
   ```

2. **安装依赖**
   ```bash
   npm install
   npm install -g hexo-cli
   ```

3. **本地预览**
   ```bash
   hexo clean && hexo g && hexo s
   ```
   访问 http://localhost:4000

4. **部署到GitHub Pages**
   ```bash
   hexo clean && hexo g && hexo d
   ```

### 写作工作流

1. **创建新文章**
   ```bash
   hexo new post "文章标题"
   # 或创建页面
   hexo new page "页面名称"
   ```

2. **编辑文章**
   - 文章位于 `source/_posts/` 目录
   - 页面位于 `source/` 目录下相应文件夹

3. **本地预览**
   ```bash
   hexo s
   ```

4. **发布更新**
   ```bash
   # 提交源码到源码仓库
   git add .
   git commit -m "更新文章"
   git push origin main
   
   # 部署到GitHub Pages
   hexo clean && hexo g && hexo d
   ```

### 目录结构

```
myblog/
├── _config.yml          # 主配置文件
├── _config.next.yml     # NexT主题配置
├── package.json         # 依赖包配置
├── source/              # 源文件目录
│   ├── _posts/          # 博客文章
│   ├── about/           # 关于页面
│   ├── blog/            # 博客分类页面
│   └── index.md         # 首页
├── themes/              # 主题目录
└── scaffolds/           # 文章模板
```

### 重要配置

- **部署配置** (`_config.yml`):
  ```yaml
  deploy:
    type: git
    repo: git@github.com:JadeQuer/JadeQuer.github.io.git
    branch: main
  ```

- **主题配置** (`_config.next.yml`):
  - Mermaid图表支持已启用
  - 自定义菜单配置
  - 社交链接等

### 注意事项

1. **双仓库管理**:
   - 源码仓库: `myblog-source` (本仓库)
   - 部署仓库: `JadeQuer.github.io` (GitHub Pages)

2. **Mermaid语法**:
   ```markdown
   {% mermaid %}
   graph LR
   A --> B
   {% endmermaid %}
   ```

3. **备份重要**:
   每次修改后记得同时提交到源码仓库：
   ```bash
   git add . && git commit -m "更新" && git push
   ```

## 联系信息

如有问题，请联系 Arctic 或查看 [Hexo官方文档](https://hexo.io/zh-cn/docs/)。
