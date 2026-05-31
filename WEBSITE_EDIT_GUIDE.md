# Website Edit Guide

这份说明用于以后快速修改本站。项目根目录是：

`/Users/qingyu/Desktop/github/QingyuLiu0521.github.io`

## 最常改的文件

| 想修改的部分 | 修改文件 |
| --- | --- |
| 首页正文、各个板块内容 | `_pages/about.md` |
| 左侧侧边栏姓名、头像、邮箱、地点、GitHub 等 | `_config.yml` 里的 `author:` |
| 顶部导航栏菜单 | `_data/navigation.yml` |
| 网站标题、简介、仓库信息 | `_config.yml` 顶部 `title`、`description`、`repository` |
| 头像图片 | `images/QingyuLiu_images.jpg` |
| CV、论文 PDF、Poster 等文件 | `assets/` |
| 页面整体样式、字体、颜色变量 | `_sass/_variables.scss`、`_sass/_base.scss`、`_sass/_page.scss` |
| 侧边栏样式 | `_sass/_sidebar.scss` |
| 顶部导航样式 | `_sass/_masthead.scss`、`_sass/_navigation.scss` |

## 修改首页各板块

首页内容都在：

`_pages/about.md`

当前主要板块：

| 板块 | 在文件里找 |
| --- | --- |
| About Me | `id='about-me'` |
| Education and Intern | `# Education and Intern` |
| Publications | `# Publications` |
| Honors and Awards | `# Honors and Awards` |

新增一个板块时：

1. 在 `_pages/about.md` 里新增标题，例如 `# News`。
2. 在标题附近加锚点，例如 `<span class='anchor' id='news'></span>`。
3. 如果希望顶部导航出现它，再改 `_data/navigation.yml`，加 `url: "/#news"`。

## 修改侧边栏

侧边栏资料来自：

`_config.yml`

主要改这里：

```yml
author:
  name: "Qingyu Liu (刘庆宇)"
  avatar: "images/QingyuLiu_images.jpg"
  bio: "Johns Hopkins University"
  location: "Baltimore, MD, USA"
  employer: "CLSP, Johns Hopkins University"
  email: "qliu91@jh.edu"
  uri: "https://qingyuliu0521.github.io/"
  github: "QingyuLiu0521"
```

如果要换头像：

1. 把新图片放进 `images/`。
2. 修改 `avatar:` 路径，例如 `avatar: "images/new-avatar.jpg"`。

## 修改顶部导航栏

顶部导航在：

`_data/navigation.yml`

格式示例：

```yml
main:
  - title: "Publications"
    url: "/#publications"
```

`title` 是导航显示的文字，`url` 是跳转位置。`url` 里的 `#publications` 要和 `_pages/about.md` 里的 `id='publications'` 对应。

## 添加论文或项目链接

论文列表在：

`_pages/about.md` 的 `# Publications` 部分

PDF、Poster、CV 这类本地文件放在：

`assets/`

Markdown 链接写法：

```md
[[PDF](assets/example.pdf)] [[Code](https://github.com/example/repo)]
```

## 本地预览

在项目目录运行：

```bash
bundle exec jekyll serve --host 127.0.0.1 --port 4000 --livereload
```

然后打开：

`http://127.0.0.1:4000`

如果 shell 没有使用 rbenv 的 Ruby，可以先运行：

```bash
eval "$(rbenv init - zsh)"
```

## 不建议直接改的文件

这些是模板框架文件，除非你要改布局结构，否则先别动：

| 文件 | 作用 |
| --- | --- |
| `_layouts/default.html` | 页面总布局 |
| `_includes/sidebar.html` | 侧边栏结构 |
| `_includes/author-profile.html` | 侧边栏作者信息渲染 |
| `_includes/masthead.html` | 顶部导航结构 |
| `assets/js/main.min.js` | 模板脚本 |

## 打开和关闭本地预览

如果想在本地查看网页效果，先进入项目目录：

```bash
cd /Users/qingyu/Desktop/github/QingyuLiu0521.github.io
```

如果你的终端没有自动使用 rbenv 的 Ruby，先输入：

```bash
eval "$(rbenv init - zsh)"
```

然后启动本地预览：

```bash
bundle exec jekyll serve --host 127.0.0.1 --port 4000 --livereload
```

启动成功后，在浏览器输入这个链接查看网页：

`http://127.0.0.1:4000`

如果看到类似下面的信息，就说明启动成功：

```text
Server address: http://127.0.0.1:4000
Server running... press ctrl-c to stop.
```

关闭本地预览的方法：

在运行 `jekyll serve` 的终端窗口里按：

```text
Control + C
```

也就是键盘上的 `Ctrl` 和 `C` 同时按下。关闭后，再访问 `http://127.0.0.1:4000` 就不会打开网页了。

如果忘记在哪个终端启动了服务，可以用下面命令查找占用 `4000` 端口的进程：

```bash
lsof -nP -iTCP:4000 -sTCP:LISTEN
```

如果确认要强制关闭，把查到的 `PID` 替换进下面命令：

```bash
kill PID
```
