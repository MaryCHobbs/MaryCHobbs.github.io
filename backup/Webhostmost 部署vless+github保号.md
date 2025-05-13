前期准备

准备好一个域名，一个github账号（没有请自行注册）  
wbehostmost [项目地址](https://github.com/banfeng-git/Webhostmost-ws-nodejs) 
[github保活项目地址](https://github.com/banfeng-git/webhost)  
教程开始  
注册购买篇  
首先访问 [webhostmost](https://www.webhostmost.com/free-web-hosting) 点击Start For Free  
[![](https://free4.yunpng.top/2025/04/30/6811ca8c773c8.png)](https://free4.yunpng.top/2025/04/30/6811ca8c773c8.png)  
再选择I already own a Domain下面的域名随便填写然后点击use  
[![](https://free4.yunpng.top/2025/04/30/6811cd25a8bcc.png)](https://free4.yunpng.top/2025/04/30/6811cd25a8bcc.png)  
进入页面后选Server Location（服务器位置）看自己需要选择位置，选完后点击Conttinue  
[![](https://free4.yunpng.top/2025/04/30/6811cfcd38e8d.png)](https://free4.yunpng.top/2025/04/30/6811cfcd38e8d.png)  
跳转页面后往下拉填写注册信息除了邮箱和密码意外都可以用生成器生成，完成填写根据图片点击进行下一步  
[![](https://free4.yunpng.top/2025/04/30/6811d2837c99d.png)](https://free4.yunpng.top/2025/04/30/6811d2837c99d.png)  
结账后会出订单号上面会提示验证邮箱先到你邮箱里面去验证电子邮件随后点击Continue To Client Area就进入了登录界面输入你注册的账号密码登录即可此时账号注册过程结束  
[![](https://free4.yunpng.top/2025/04/30/6811d5406a618.png)](https://free4.yunpng.top/2025/04/30/6811d5406a618.png)  
部署篇  
登陆后即可看到服务器信息，点击 Go To Control Panel 跳转到后台管理页面，点击左栏 Domain Management ➡Domain Setup➡勾选域名➡点击Delete删除域名➡出现弹窗勾选Delete web data在点Confirm就删除掉了  
[![](https://free4.yunpng.top/2025/04/30/6811d79150326.png)](https://free4.yunpng.top/2025/04/30/6811d79150326.png)  
[![](https://free4.yunpng.top/2025/04/30/6811d9ef19eed.png)](https://free4.yunpng.top/2025/04/30/6811d9ef19eed.png)  
删除完成后在Domain出填写自己域名并解析好ip（ip在登录时后的服务器信息里面）➡点击Create保存域名  
[![](https://free4.yunpng.top/2025/04/30/6811dcafb6d9a.png)](https://free4.yunpng.top/2025/04/30/6811dcafb6d9a.png)  
下一步部署ssl依次点击Security Management➡SSL Certificates➡选择Get automatic certificate from ACME Provider➡勾选Force SSL with https redirect➡Save  
[![](https://free4.yunpng.top/2025/04/30/6811e1bfe5999.png)](https://free4.yunpng.top/2025/04/30/6811e1bfe5999.png)  
随后点击点击左栏 Files Management ➡File Management➡domains➡xxx.xxxxx.com➡public\_html. 将项目中的 app.js 和 package.json 上传到此目录下即可  

[![](https://free4.yunpng.top/2025/04/30/6811e264e17d6.png)](https://free4.yunpng.top/2025/04/30/6811e264e17d6.png)  
[![](https://free4.yunpng.top/2025/04/30/6811e2e778efd.png)](https://free4.yunpng.top/2025/04/30/6811e2e778efd.png)  
下一步回到面板点击左栏 Website Management➡NodeJs APP➡Create application➡CREATE先看图  
Node.js version➡v22  
Application root➡domains/xxx.xxxx.com/public\_html (替换自己的完整域名)切记不要填写错误  
Application startup file➡app.js  
点击Add variable添加环境变量  
DOMAIN➡你的域名  
PORT ➡端口（自己随便填写别人没用过的端口）  
UUID➡生成的uuid  
NEZHA\_SERVER➡哪吒探针地址（没有可以不填）  
NEZHA\_PORT ➡哪吒探针端口（没有可以不填）  
NEZHA\_KEY➡哪吒探针密钥（没有可以不填）  
[![](https://free4.yunpng.top/2025/04/30/6811e69dd76a0.png)](https://free4.yunpng.top/2025/04/30/6811e69dd76a0.png)  
[![](https://free4.yunpng.top/2025/04/30/6811e9a952dd9.png)](https://free4.yunpng.top/2025/04/30/6811e9a952dd9.png)  
此时创建完成 Node.js 应用后往下翻点击Run NPM install等待执行完毕  
[![](https://free4.yunpng.top/2025/05/03/681593de18f58.png)](https://free4.yunpng.top/2025/05/03/681593de18f58.png)  
等待完毕后点击 Run JS script弹出界面后点击start再点击Run JS script即可  
[![](https://free4.yunpng.top/2025/04/30/6811f078abee8.png)](https://free4.yunpng.top/2025/04/30/6811f078abee8.png)  
[![](https://free4.yunpng.top/2025/04/30/6811f0b83fd02.png)](https://free4.yunpng.top/2025/04/30/6811f0b83fd02.png)  
这时输入你的域名 /sub 即可获取节点如xxxx.xom/sub 并访问得到类似于dmxlc3M6Ly9iMmU3ODcwYi1mZGE1LTQzMGQtYmNhMC00ZjNmYTdlZjIwM2NAdnAuemhpeXUudXMua2c6NDQzP2VuY3J5cHRpb249bm9uZSZzZWN1cml0eT10bHMmc这样的将他导入到v2中在设置一下跳过脸书认证就可以了  
如果访问是503请更换端口或检查有无错误换端口请重新点击Run JS script  
github保活篇

[点击进入github查看教程](https://github.com/banfeng-git/webhost)  
