## 1\. 前期准备工作

1. [Node](https://nodejs.org/en) （ **必备** ）
2. [Git](https://git-scm.com/downloads) （ **必备** ）
3. [VSCode](https://code.visualstudio.com/) （ **可选** ）
4. 域名，建议配置一个域名以避免被防火墙阻挡，推荐购买链接： [https://spaceship.sjv.io/limin](https://spaceship.sjv.io/limin)
5. 配置 Cloudflare，托管域名： [托管教程](https://youtu.be/3a6ImhcizcU?si=axjlZmba3q9wtTEN)
6. 创建免费图床： [图床搭建教程](https://youtu.be/ah5szwr4JxM?si=18c42iG8NqIcHJLX)
7. 注册cloudflare怕被扣费，推荐用myfine有50张虚拟卡（需要护照），教程链接： [注册教程](https://youtu.be/gg3Ji4WDszs?si=fqtFwTMjsnoUExxG)
8. Hexo官方主题展示： [点击跳转](https://hexo.io/themes/)

---

### 2.1. 安装 Node

1. 从 [Node 官网](https://nodejs.org/en) 下载适合自己系统的版本。
2. 完成安装，Windows电脑建议使用默认目录 `C:/Program Files/nodejs/` ，苹果电脑无所谓。
3. 验证安装成功，在命令行中输入 `node -v` 检查版本信息。  
	[![示例图片](https://13fe9ff.webp.li/2024/10/2a18b0579664e643e4363fc93d47c842.png)](https://13fe9ff.webp.li/2024/10/2a18b0579664e643e4363fc93d47c842.png)
4. 苹果用户可通过右键文件夹，选择“服务”，新建终端窗口以便操作。

### 2.2. 安装 Git

1. 从 [Git 官网](https://git-scm.com/downloads) 下载适配的 Git 版本。  
	[![示例图片](https://13fe9ff.webp.li/2024/10/3957eda9a3c4ec8422eecc672b059d42.png)](https://13fe9ff.webp.li/2024/10/3957eda9a3c4ec8422eecc672b059d42.png)
2. Windows 用户可使用默认目录安装 Git，Mac 用户则按提示在终端操作。
3. 验证安装完毕后，Windows 用户会在开始菜单中看到 `Git Bash` 等应用。

## 2\. 配置 Git 密钥并连接至 Github

常用 Git 命令:

```bash
bashgit config -l

git config --system --list

git config --global --list
```

#### 3.1. 配置用户名和邮箱

```bash
bashgit config --global user.name "你的用户名"

git config --global user.email "你的邮箱"
```

通过 `git config -l` 验证是否成功。  
[![abd](https://13fe9ff.webp.li/2024/10/1d37926686d18e0ac468ce6d00c07a50.png)](https://13fe9ff.webp.li/2024/10/1d37926686d18e0ac468ce6d00c07a50.png)

#### 3.2. 配置公钥连接 Github

1. 生成 SSH 公钥：
```bash
bashssh-keygen -t rsa -C "你的邮箱"
```

一路回车生成密钥，进入 `.ssh` 文件夹复制 `id_rsa.pub` 公钥内容，配置到 Github 的 SSH 设置中。  
[![abm](https://13fe9ff.webp.li/2024/10/d2ec687d4c21887ffc96e96687630d7d.png)](https://13fe9ff.webp.li/2024/10/d2ec687d4c21887ffc96e96687630d7d.png)

## 3\.在苹果电脑上，如果你知道文件的路径，可以通过以下几种方式快速找到文件：

打开Finder。  
按下 Command + Shift + G，在弹出的对话框中输入文件路径，然后按 Enter。这样可以直接跳转到该路径下的文件。  
[![abm](https://13fe9ff.webp.li/2024/10/1efba3fa54bedcba6059cc88a8daf717.png)](https://13fe9ff.webp.li/2024/10/1efba3fa54bedcba6059cc88a8daf717.png)

### 在windows电脑上：

打开C盘下用户文件夹下的.ssh的文件夹，会看到以下文件  
id\_rsa 私钥  
id\_rsa.pub 公钥

找到公钥匙，并复制，打开GitHub开始配置  
[![abm](https://13fe9ff.webp.li/2024/10/0557c8ce136c6e43f4c1541d31beba62.png)](https://13fe9ff.webp.li/2024/10/0557c8ce136c6e43f4c1541d31beba62.png)

1. 将 SSH KEY 配置到 GitHub  
	进入github，点击右上角头像 选择settings，进入设置页后选择 SSH and GPG keys，名字随便起，公钥填到Key那一栏。  
	[![abm](https://13fe9ff.webp.li/2024/10/84b777a4f0b9a8a290e1472087ce30e2.png)](https://13fe9ff.webp.li/2024/10/84b777a4f0b9a8a290e1472087ce30e2.png)

[![abm](https://13fe9ff.webp.li/2024/10/ab0ad8dba8ff5ace69b12e9ffa5d8b9d.png)](https://13fe9ff.webp.li/2024/10/ab0ad8dba8ff5ace69b12e9ffa5d8b9d.png)

1. 测试连接：
```bash
bashssh -T git@github.com
```

第一次连接会提示Are you sure you want to continue connecting (yes/no/\[fingerprint\])?，输入yes即可  
[![abm](https://13fe9ff.webp.li/2024/10/db87e8d1e4767b675c03a907c06ecdda.png)](https://13fe9ff.webp.li/2024/10/db87e8d1e4767b675c03a907c06ecdda.png)

#### 3.3. 创建 GitHub.io 仓库

1. 点击右上角的 `+` 按钮，选择新建仓库，命名格式为 `<用户名>.github.io` ，(注意：前缀必须为用户名)选择公开 `Public` 。
2. 点击 Creat repository 进行创建即可。  
	[![abm](https://13fe9ff.webp.li/2024/10/aff632548c5c460783916a88a187e76a.png)](https://13fe9ff.webp.li/2024/10/aff632548c5c460783916a88a187e76a.png)

[![abm](https://13fe9ff.webp.li/2024/10/6a6a086ab644e9f9ac5820570686e62c.png)](https://13fe9ff.webp.li/2024/10/6a6a086ab644e9f9ac5820570686e62c.png)

## 4\. 初始化 Hexo 博客

1. 创建文件夹保存博客源码：

### 苹果用户随意创建好文件夹后，在文件夹右击，选择“服务”选择“新建终端窗口以便操作”

### Windows用户可以（例如 D:/Hexo-Blog），在该文件夹内启动 Git Bash 或终端。

1. 安装 Hexo：
```bash
bashnpm install -g hexo-cli && hexo -v
```

出现此页面代表安装成功  
[![abm](https://13fe9ff.webp.li/2024/10/09dfd08bc762f761b61b4666ac383b99.png)](https://13fe9ff.webp.li/2024/10/09dfd08bc762f761b61b4666ac383b99.png)

1. 初始化 Hexo 项目安装依赖：
```bash
bashhexo init blog-demo

cd blog-demo

npm i
```

[![abm](https://13fe9ff.webp.li/2024/10/d17588a07ad38a5285fc42d4c781f9cd.png)](https://13fe9ff.webp.li/2024/10/d17588a07ad38a5285fc42d4c781f9cd.png)

现在你的文件夹会有这些内容  
[![abm](https://13fe9ff.webp.li/2024/10/94f0f93b98c067b27d235830032d56ae.png)](https://13fe9ff.webp.li/2024/10/94f0f93b98c067b27d235830032d56ae.png)

1. 启动项目并验证：
```bash
bashhexo cl && hexo s
```

在浏览器中访问 [http://localhost:4000/](http://localhost:4000/) 以查看效果。

[![abm](https://13fe9ff.webp.li/2024/10/5f1f08bb49c8f8d7f63c0bee92e3587b.png)](https://13fe9ff.webp.li/2024/10/5f1f08bb49c8f8d7f63c0bee92e3587b.png)

## 5\. 将静态博客挂载到 GitHub Pages

1. 修改 `_config.yml` 文件，配置 `repository` 为你的 GitHub 地址，分支改为 `main` ：
```yaml
yamldeploy:

  type: git

  repository: git@github.com:你的用户名/你的用户名.github.io.git

  branch: main
```
1. 安装 `hexo-deployer-git` ：
```bash
bashnpm install hexo-deployer-git --save
```
1. 部署到 GitHub：
```bash
bash// Git BASH终端

hexo clean && hexo generate && hexo deploy  

// 或者

// VSCODE终端

hexo cl; hexo g; hexo d
```

访问 `https://<用户名>.github.io/` 以查看博客。

## 6\. 将静态博客挂载到 Cloudflare Pages

1. 通过 Cloudflare Pages 连接 Git 仓库。
2. 登录 GitHub，点击保存并部署。
3. 部署成功后，访问 Cloudflare 提供的链接。

如有自定义域名，可以在 Cloudflare Pages 中绑定。没有建议去申请，这样博客就不被墙了。

## 如何使用

### 新建一篇博文

```bash
bashhexo new 这是一篇新的博文
```

编辑 `_posts` 文件夹中的新建文章，使用 Markdown 语法编写内容。

### 本地预览

```bash
bashhexo cl && hexo s
```

### 推送到 GitHub

```bash
bashhexo cl && hexo g && hexo d
```

## 进阶教程预告

接下来会介绍 Hexo 主题美化 文章写作 赶紧订阅我吧！

## 解决 VSCODE 报错

如果首次执行 VSCODE 终端出现报错，可以使用管理员身份打开 PowerShell，并执行以下命令：

```bash
bashSet-ExecutionPolicy RemoteSigned
```


