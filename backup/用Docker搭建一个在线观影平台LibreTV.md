## 前言

关于在线影视类的项目之前给大家推荐苹果CMS的搭建教程，那么今天给大家分享一个类似的在线观影项目-LibreTV  

![image-1746002765471](https://www.ywsj365.com/upload/2025/04/image-1746002765471.png)

一个轻量级、免费的在线视频搜索与观看平台，提供来自多个视频源的内容搜索与播放服务。无需注册，即开即用，支持多种设备访问。项目采用纯前端技术构建，可轻松部署在各类静态网站托管服务上。

## 主要特性：

🔍 多源视频搜索功能，覆盖电影、电视剧等内容

📱 响应式设计，完美支持电脑、平板和手机

🌐 聚合多个视频源，自动提取播放链接

🔄 支持自定义API接口，灵活扩展

💾 本地存储搜索历史，提升使用体验

🚀 纯静态部署，无需后端服务器

🛡️ 内置广告过滤功能，提供更干净的观影体验

API兼容性  
LibreTV 支持标准的苹果 CMS V10 API 格式。添加自定义 API 时需遵循以下格式：

搜索接口: [https://example.com/api.php/provide/vod/?ac=videolist&wd=关键词](https://example.com/api.php/provide/vod/?ac=videolist&wd=%E5%85%B3%E9%94%AE%E8%AF%8D)  
详情接口: [https://example.com/api.php/provide/vod/?ac=detail&ids=视频ID](https://example.com/api.php/provide/vod/?ac=detail&ids=%E8%A7%86%E9%A2%91ID)  
添加 CMS 源:

在设置面板中选择"自定义接口"  
接口地址只需填写到域名部分: [https://example.com](https://example.com/) （不要包含/api.php/provide/vod部分）

## 准备条件

1）一台服务器  
我们使用VPS来演示  
vps  
[莱卡云官网](https://www.lcayun.com/aff/PQCSKOCK)  
2）本项目使用到的github  
[https://github.com/LibreSpark/LibreTV](https://github.com/LibreSpark/LibreTV)  

![image-1746003004324](https://www.ywsj365.com/upload/2025/04/image-1746003004324.png)

  
目前已经2.5k stars  
更多功能可以访问GitHub  
3）域名(可选)  
域名可以根据自己的需求绑定

## 一、Docker环境部署

在vps安装docker和docker-compose  
Docker官方安装文档（英文）  
[https://duan.yyzq.eu.org/docker-001](https://duan.yyzq.eu.org/docker-001)  
Docker-Compose官方安装文档（英文)  
[https://duan.yyzq.eu.org/docker-002](https://duan.yyzq.eu.org/docker-002)  
Centos安装Docker和Docker-compose（中文）  
[https://duan.yyzq.eu.org//03](https://duan.yyzq.eu.org//03)  
Ubuntu安装Docker和Docker-compose（中文）  
[https://duan.yyzq.eu.org//04](https://duan.yyzq.eu.org//04)

==推荐直接用一键脚本==

## docker安装脚本

```
bash <(curl -sSL https://cdn.jsdelivr.net/gh/SuperManito/LinuxMirrors@main/DockerInstallation.sh)
```

## docker-compose安装脚本

```
curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose
```

## 二、创建docker-compose.yml文件

```
mkdir libretv;cd libretv #创建一个目录，并进入此目录
```

然后再新建docker-compose.yml

```
vim docker-compose.yml
```

```
services:
  libretv:
    image: bestzwei/libretv:latest  # 使用 libretv 的最新镜像
    container_name: libretv         # 容器名称为 libretv
    ports:
      - "8899:80"                   # 将主机的 8899 端口映射到容器的 80 端口
    environment:
      - PASSWORD=123456             # 设置访问密码（留空表示不启用密码保护）
    restart: always                 # 容器异常退出后自动重启
```

## 三、执行容器运行命令

```
docker-compose up -d #运行容器
```

```
docker-compose ps  #查看是否开启成功
```

==正常启动如下所示==

```
docker-compose ps
NAME      IMAGE                     COMMAND                  SERVICE   CREATED        STATUS                  PORTS
libretv   bestzwei/libretv:latest   "/docker-entrypoint.…"   libretv   43 hours ago   Up 43 hours (healthy)   443/tcp, 0.0.0.0:8899->80/tcp, [::]:8899->80/tcp
```

## 四、打开web页面使用

成功以后需要打开自己相应的端口(8899)防火墙就可以web端访问了  
打开自己VPS的端口加ip进入初始化页面

```
http://ip:8899
```

有设置密码的自己输入  

![image-1746003196279](https://www.ywsj365.com/upload/2025/04/image-1746003196279.png)


搭建完没法直接看的需要设置下自带的数据源  

![image-1746003278314](https://www.ywsj365.com/upload/2025/04/image-1746003278314.png)


或者打开豆瓣  
![image-1746003332006](https://www.ywsj365.com/upload/2025/04/image-1746003332006.png)

## 五、绑定域名

如需绑定域名可以参考  
NginxProxyManager  
[https://duan.yyzq.eu.org//npm-ch](https://duan.yyzq.eu.org//npm-ch)  
绑定完域名配置好证书就可以用域名来访问了

==如果你没有服务器可以使用以下这几种方法搭建==

## Cloudflare Pages

1. Fork 或克隆本仓库到您的 GitHub 账户  
	![image](https://www.ywsj365.com/upload/2025/05/image.png)
2. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/) ，进入 Pages 服务  
	![image-1746528260026](https://www.ywsj365.com/upload/2025/05/image-1746528260026.png)
3. 点击"创建项目"，连接您的 GitHub 仓库  
	![image-1746528278862](https://www.ywsj365.com/upload/2025/05/image-1746528278862.png)
	  
	然后绑定自己的GitHub的项目  
	![image-1746528329573](https://www.ywsj365.com/upload/2025/05/image-1746528329573.png)
4. 使用以下设置：
	- 构建命令：留空（无需构建）
	- 输出目录：留空（默认为根目录）  
		![image-1746528403660](https://www.ywsj365.com/upload/2025/05/image-1746528403660.png)
5. 点击"保存并部署"  
	![image-1746528434477](https://www.ywsj365.com/upload/2025/05/image-1746528434477.png)
	  
	部署成功  
	![image-1746528509050](https://www.ywsj365.com/upload/2025/05/image-1746528509050.png)
	  
	需要等待一会才能访问  
	![image-1746528582152](https://www.ywsj365.com/upload/2025/05/image-1746528582152.png)
	  
	稍等片刻(5分钟左右)就可以访问了  
	![image-1746528706926](https://www.ywsj365.com/upload/2025/05/image-1746528706926.png)
6. 可选：绑定自己的域名  
	如果Cloudflare给你分配的域名无法使用也可以绑定自己的域名  
	![image-1746528558939](https://www.ywsj365.com/upload/2025/05/image-1746528558939.png)
	  
	新增一个CNAME即可  
	![image-1746528851749](https://www.ywsj365.com/upload/2025/05/image-1746528851749.png)
	image-1746528851749
	  
	等待一会即可使用自定义的域名访问  
	![image-1746529161785](https://www.ywsj365.com/upload/2025/05/image-1746529161785.png)

## Vercel

1. Fork 或克隆本仓库到您的 GitHub/GitLab 账户
2. 登录 [Vercel](https://vercel.com/) ，点击"New Project"
3. 导入您的仓库，使用默认设置
4. 点击"Deploy"
5. 可选：在"Settings" > "Environment Variables"中配置密码保护

## Netlify

1. Fork 或克隆本仓库到您的 GitHub 账户
2. 登录 [Netlify](https://app.netlify.com/)
3. 点击"New site from Git"，选择您的仓库
4. 构建设置保持默认
5. 点击"Deploy site"
6. 可选：在"Site settings" > “Build & deploy” > "Environment"中配置密码保护

