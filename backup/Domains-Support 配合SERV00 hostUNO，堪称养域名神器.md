![](https://www.youtube.com/watch?v=gPJ7tjRKnzo)

## Domains-Support：养域名神器

大家好！欢迎来到我的博客。今天我将为大家介绍一个非常实用的项目—— **Domains-Support** ，它可以帮助你管理和维护免费域名，确保它们始终处于活跃状态，避免被回收。本文内容改编自我的视频教程，详细讲解了项目背景、功能以及部署步骤。

---

## 背景

相信很多朋友都拥有一些免费域名，比如 **Zone.ID** 或 **NYC** 域名。但你可能也发现了，越来越多的免费域名服务商要求域名必须保持“活跃状态”，否则就会被回收。

### 什么是活跃状态？

“活跃状态”指的是你的域名需要关联一个可访问的网站或服务。例如：

- **Zone.ID** 的条款明确规定：在域名到期前，系统会检查你的网站是否正常运行。如果网站无法访问或配置错误，子域名将被删除。
- **NYC** 域名也有类似要求：如果域名下的网站处于非活跃状态、无法访问或没有任何内容，可能会被直接删除，且不另行通知。

为了避免域名被回收，我们需要一个工具来管理域名，确保它们始终“活着”。这正是 **Domains-Support** 的用武之地。

---

## 项目介绍

**Domains-Support** 是一个基于 **Cloudflare Pages** 的域名管理系统，专为免费域名用户设计。它有以下核心功能：

- **监控域名状态和到期时间** ：实时查看域名是否正常运行以及何时到期。
- **Telegram 通知** ：到期前通过 Telegram 提醒你续期或采取行动。
- **结合 Serv00 托管网站** ：轻松将域名挂到免费托管平台 **Serv00** 上，确保活跃状态。

### 为什么选择 Serv00？

**Serv00** 是一个免费的网站托管平台，非常适合用来“养”域名：

- 免费版支持托管 **100 个网站** 。
- 付费版提供无限网站托管。
- 它专为网站托管设计，操作简单，非常适合普通用户。

通过 Domains-Support 和 Serv00 的结合，你可以轻松管理多个域名，避免因疏忽而丢失。

---

## 部署 Domains-Support

下面是详细的部署步骤，跟着操作即可快速上手。

### 1\. Fork 项目

1. 打开 [Domains-Support 的 GitHub 页面](https://github.com/frankiejun/Domains-Support)
2. 点击 **Fork** ，将项目复制到你自己的 GitHub 账号下。

### 2\. 在 Cloudflare Pages 上部署

1. 登录你的 **Cloudflare** 账号，进入 **Workers and Pages** 页面。
2. 点击 **Create** ，选择 **Pages** ，然后点击 **Connect to Git** 。
3. 连接你的 GitHub 账号，选择刚刚 Fork 的 **Domains-Support** 项目。
4. 设置构建配置：
	- **构建命令** ：从项目文档中复制（通常在 README 中），例如 ==`npm run build`== 。
	- **输出目录** ：设置为 ==`dist`== 。
5. 配置环境变量：
	- ==`USER`== ：设置登录用户名，例如 ==`admin`== 。
	- ==`PASS`== ：设置登录密码，例如 ==`password`== 。
	- ==`API_TOKEN`== ：自定义一个 API 令牌，例如 ==`ABC123`== 。
6. 点击 **Save and Deploy** 开始部署，等待几分钟即可完成。

### 3\. 创建和配置数据库

1. 在 Cloudflare Pages 的项目设置中，进入 **存储和数据库** ，选择 **D1 数据库** 。
2. 创建一个新数据库，命名为 ==`domains-support`== 。
3. 进入数据库控制台，打开项目中的 ==`schema.sql`== 文件，逐段执行 SQL 语句（不要一次性运行全部，避免报错），创建必要的表。
4. 返回项目设置，将数据库绑定到项目，变量名设为 ==`DB`== 。
5. 修改环境变量或绑定数据库后，需重新部署项目：点击 **重新部署** 。

### 4\. 在 Serv00 上配置

1. 登录你的 **Serv00** 账号。如果尚未安装 **Serv00-Play** ，先安装它。
2. **Serv00-Play** GitHub项目安装地址：[链接直达](https://github.com/frankiejun/serv00-play)
	- 安装命令  ==`bash <(curl -Ls https://raw.githubusercontent.com/frankiejun/serv00-play/main/start.sh) --install`==
3. 在 Serv00-Play 中选择 **Domains-Support** 选项（通常是选项 26）。
4. 配置以下信息：
	- **API Token** ：输入你在 Cloudflare 中设置的 ==`API_TOKEN`== ==ABC123== 。
	- **Domains-Support 服务域名** ：输入 Cloudflare 部署完成后生成的域名（例如 ==`your-project.pages.dev`== ）。
5. 添加域名：
	- 输入你的域名（例如 ==`example.zone.id`== ）。
	- 将域名通过 DNS 设置（A 记录）指向 Serv00 提供的 IP 地址。
6. 选择网站模板（提供 3 个默认模板）或自定义网站内容。
7. 可选择是否将域名信息录入数据库（见下文）。

### 5\. 管理域名

部署完成后，访问 Domains-Support 的管理界面（即 Cloudflare 提供的域名地址）：

- 使用设置的 ==`USER`== 和 ==`PASS`== 登录。
- 查看域名状态、到期时间等信息。
- 如果录入了域名信息，可以看到所有域名的详情，包括注册时间、到期时间、剩余天数等。

---

## 自定义网站

不喜欢默认模板？可以自定义网站内容：

1. 使用 **ChatGPT** 或其他工具生成静态网页。例如，要求生成“新手妈妈的育儿日记”，包含两篇简单文章。
2. 将生成的 HTML 文件保存到 Serv00 的指定目录（例如 ==`/home/username/domains-support/website/`== ）。
3. 在 Serv00-Play 中添加域名时，选择“自定义网站”，输入文件路径（例如 ==`/home/username/domains-support/website/mom-diary.html`== ）。

### 示例：自定义网页

假设你生成了以下内容：

```html
html

<html>

<head>

    <title>新手妈妈日记</title>

</head>

<body>

    <h1>新手妈妈的育儿日记</h1>

    <h2>第一天：迎接小生命</h2>

    <p>今天宝宝出生了，激动又紧张……</p>

    <h2>第二天：学习喂奶</h2>

    <p>喂奶比想象中难，但看到宝宝满足的眼神，觉得一切都值得……</p>

</body>

</html>
```

保存为 `mom-diary.html` ，然后在 Serv00 中指定路径即可。

---

## 设置 Telegram 通知

为了接收域名到期提醒：

1. 在 Domains-Support 管理界面中，进入设置页面。
2. 输入：
	- **Telegram Bot Token** ：从 Telegram 的 BotFather 获取。
	- **User ID** ：你的 Telegram 用户 ID。
	- **提前通知天数** ：例如，剩余 30 天时提醒。
3. 保存设置。
4. 如果没有 Serv00 账号，可以使用 [cron-job.org](https://cron-job.org/) 设置每日定时任务，检查域名状态并触发通知：
	- 注册账号，创建 cronjob。
	- 设置每天运行一次，调用 Domains-Support 的检查接口。

---

## 总结

通过 **Domains-Support** ，你可以轻松管理免费域名，确保它们始终处于活跃状态，避免被回收。结合 **Serv00** 的免费托管功能和 **Telegram** 通知，你再也不用担心忘记续期或域名丢失。

