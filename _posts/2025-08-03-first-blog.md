---
layout: post
title:  "我的第一篇博客！"
author:  "solitern"
tags:	record
excerpt_separator: <!--more-->
---
既然是第一篇博客，那自然要记录一下第一篇博客诞生的过程。<!--more-->

## 起因

搭建博客最主观的原因就是买了个1块钱的域名，闲着也是闲着，干脆利用github提供的免费静态页面托管服务布置个博客，也能把这个没有其他作用的域名用上。

至于我一开始买这个域名的原因，并不是为了搭建博客所用。而是我在云服务器上部署了[Openlist](https://doc.oplist.org/)（一个支持多种存储的文件列表程序，能方便地管理多个云盘），每次访问都需要输入IP地址，想着弄个域名能更舒服一些。结果发现国内的服务器绑域名还要备案（ICP备案+公安备案），太麻烦了，于是我放弃了。

之后开始搭建博客，怎么搭建呢？反正我不会，那就询问gemini 2.5 pro好了。

它给出了十分详细的搭建教程，并推荐我使用Tale这个十分简洁的模板，于是我便开始了。

## 过程

### 1. 准备工作

开始之前，需要准备的有：

1. 一个 GitHub 账号。
2. 你的个人域名（例如 `yourdomain.com`）。
3. 在你的电脑上安装好 [Git](https://git-scm.com/downloads)。

### 2. 开始搭建

#### 第 1 步：Fork 模板仓库

1. 打开 [Tale 模板的 GitHub 仓库](https://github.com/chesterhow/tale)。
2. 点击页面右上角的 **"Fork"** 按钮。这会把整个模板仓库复制一份到你自己的 GitHub 账号下。

![fork](..\assets\fork.jpg)

#### 第 2 步：创建你的 GitHub Pages 仓库

1. 在你刚刚 Fork 好的仓库页面（`https://github.com/你的用户名/tale`），点击 **"Settings"**。

![](..\assets\set.jpg)

2. 在 "General" 设置页面，找到 "Repository name" 字段。
3. **这是最关键的一步**：将仓库名称修改为 `你的用户名.github.io`。例如，如果你的 GitHub 用户名是 `octocat`，那么就改成 `octocat.github.io`。
4. 点击 **"Rename"**。

![](..\assets\name.jpg)

重命名后，GitHub 会自动为你开启 GitHub Pages 功能。稍等一两分钟，访问 `https://你的用户名.github.io`，你应该就能看到一个和 Tale 模板一模一样的网站了！

#### 第3步：绑定个人域名

##### 1. 在 GitHub 端设置：

- 在你的 `你的用户名.github.io` 仓库页面，再次进入 **"Settings"**。
- 在左侧菜单中选择 **"GitHub Pages"**。
- 在 "Custom domain" 部分，输入你的域名（例如 `blog.yourdomain.com` 或 `www.yourdomain.com`），然后点击 **"Save"**。
- 保存后，页面下方会提示你需要在你的域名服务商那里配置 DNS 记录。同时，请**勾选 "Enforce HTTPS"**，GitHub 会为你的域名免费提供 SSL 证书。

![](..\assets\domin_name.jpg)

##### 2. 在你的域名服务商端设置 (例如阿里云、GoDaddy、腾讯云等)：

- 登录你的域名服务商的管理后台，找到 DNS 解析设置。
- 你需要添加几条解析记录，具体类型取决于你绑定的域名：
  - **如果你绑定的是顶级域名 (Apex Domain)**，如 `yourdomain.com`： 你需要添加 **A 记录**，指向 GitHub Pages 的服务器 IP。请添加以下**全部四条** A 记录：
    - `185.199.108.153`
    - `185.199.109.153`
    - `185.199.110.153`
    - `185.199.111.153`
  - **如果你绑定的是子域名 (Subdomain)**，如 `blog.yourdomain.com` 或 `www.yourdomain.com`： 你需要添加一条 **CNAME 记录**，将你的子域名指向你的 GitHub Pages 默认地址：
    - 记录类型：`CNAME`
    - 主机记录 (Host/Name)：`blog` 或 `www`
    - 记录值 (Value/Points to)：`你的用户名.github.io`

**等待生效**

- DNS 解析的修改通常需要几分钟到几小时才能在全球范围内生效。你可以喝杯咖啡，耐心等待。
- 生效后，访问你的个人域名，就能看到你的博客了！
