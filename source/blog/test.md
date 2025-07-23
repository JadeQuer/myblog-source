---
title: test
date: 2025-03-01 19:25:28
tags:
mathjax: true
mermaid: true
---

这篇文章用于测试markdown的内容显示是否正确

# 标题测试

# 这是一级标题

## 这是二级标题

### 这是三级标题

#### 这是四级标题

##### 这是五级标题

###### 这是六级标题

# 列表测试

+ 无序列表项1
  + 嵌套无序列表项 1.1
    + 嵌套无序列表项 1.1.1
    + 嵌套无序列表项 1.1.2
  + 嵌套无序列表项 1.2
+ 无序列表项2

1. 有序列表项 1
2. 有序列表项 2

# 引用测试

普通测试块

> Hexo is a fast, simple and powerful blog framework.

嵌套测试块

> Hexo is a fast, simple and powerful blog framework.
>
> > Hexo is a fast, simple and powerful blog framework.
>
> Hexo is a fast, simple and powerful blog framework.

特殊测试块

# 代码测试

```python
def hello_world():
	print("hello world!")
```

给代码块的左上角增加 ”复制“ 按钮：

修改**根目录下**的`_config.next.yml`:

```yml
copy_button:
  enable: true
```

# 链接测试

[点击这里访问Hexo官网](https://hexo.io/)

# 图片测试

<img src="https://img.lingshunlab.com/image-20240124231957517.png?imageView2/0/q/75|watermark/2/text/TGluZ1NodW5sYWIuY29tIOWHjOmhuuWunumqjOWupA==/font/5b6u6L2v6ZuF6buR/fontsize/260/fill/IzAwMDAwMA==/dissolve/66/gravity/SouthEast/dx/10/dy/10|imageslim" alt="img" style="zoom:33%;" />

# 流程图测试

```mermaid
graph LR
	A --> B
```

# 表格测试

| 标题1 | 标题2 | 标题3 |
| ----- | ----- | ----- |
| 内容1 | 内容2 | 内容3 |
| 内容4 | 内容5 | 内容6 |
| 内容7 | 内容8 | 内容9 |

# 文本测试

**这是粗体文本**

*这是斜体文本*

***这是粗体加斜体文本***

~~这是删除线文本~~

<u>这是下划线文本</u>

# 公式测试

$$
\frac{x+y}{y+z} \\
\lim_{\substack{x \to \infty \\ y \to 0}} \\
\sum_{y \to 0}^{x \to +\infty} \frac{x}{y} \\
\int_{0}^{\infty} x \, dx \\
\frac{\partial x}{\partial y}
$$
在**根目录下**的`_config.next.yml`中 :

```yml
math:
  # Default (false) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in front-matter.
  # If you set it to true, it will load mathjax / katex script EVERY PAGE.
  every_page: false

  mathjax:
    enable: true #把这里更改为true
    # Available values: none | ams | all
    tags: none

  katex:
    enable: false
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: false
```

# 分割线测试

下面是分割线

---



## 任务列表测试
- [x] 已完成任务（显示勾选框）
- [ ] 未完成任务（显示空选框）
- [ ] 支持多层级
  - [x] 子任务 1
  - [ ] 子任务 2

# 折叠测试

<details>
  <summary>点击查看详细内容</summary>
  这是折叠内容
</details>
