![](https://www.youtube.com/watch?v=emEBm8Gw2wI)

**《部署教程说明》**

通过Cloudflare零成本部署 **VLESS/Trojan** 免费节点！一键部署永久免部署(**解决修改或设置变量自动部署出现1101错误问题**),最新版本可以实现 **VLESS/Trojan合成一套部署生成两类型节点** 、 **0变量设置** 、 **解决IP跳动** 、并可以 **优选IP区域** 指定 **优选反代IP区域** 实现固定优选IP的落地IP,实现解锁ChatGPT、Netflix、TikTok等网站，还能轻松观看4K视频，永久免费。教程简单易懂，适合所有人，赶紧上手试试吧！

> **💡优势** ： **无限流量**,再也不用担心流量不够用,全免费不用VPS就可以部署。

- VLESS/Trojan二合一节点项目地址： [https://github.com/amclubs/am-cf-tunnel](https://github.com/amclubs/am-cf-tunnel)
- Trojan免费节点项目地址： [https://github.com/amclubs/am-cf-trojan](https://github.com/amclubs/am-cf-trojan)

## 一、需要准备的前提资料

### 1、注册免费cloudflare帐号(邮箱就可以免费注册)

- 注册地址： [https://cloudflare.com](https://cloudflare.com/) [\[点击观看视频教程\]](https://youtu.be/ITeuSbHVQ2E)

### 2、Cloudflare标准 端口 知识 点击观看优选IP视频教程

- 80系端口(HTTP)：80，8080，8880，2052，2082，2086，2095
- 443系端口(HTTPS)：443，2053，2083，2087，2096，8443
- [IP落地测试工具地址](https://ip.sb/)

## 二、开始部署Cloudflare免费节点

### 一、Workers 部署方法 视频教程

点击展开/收起
1. 部署 Cloudflare Worker：
	- 在 Cloudflare Worker 控制台中创建一个新的 Worker。
	- 将 [\_worker.js](https://github.com/amclubs/am-cf-tunnel/blob/main/_worker.js) 的内容粘贴到 Worker 编辑器中。
2. 给 workers绑定 自定义域： [免费域名申请教程](https://www.youtube.com/playlist?list=PLGVQi7TjHKXZGODTvB8DEervrmHANQ1AR)
	- 在 workers控制台的 `设置` 选项卡 -> 点击 `域和路由` -> 右方点击 -> `添加` -> 选择 `自定义域` 。
	- 填入你已转入 CloudFlare 域名 ([amclubss.com](http://amclubss.com/)) 解析服务的次级域名，例如:`vless.amclubss.com` 后 点击 `添加域` ，等待证书生效即可。
3. 给UUID设置KV存储桶(可选项，推荐设置)：
	- 在 CloudFlare主页的左边菜单的 ` 存储和数据库` 选项卡 -> 展开选择点击 `KV` -> 右方点击 -> `创建` -> 填入 `命名空间名称` (此名称自己命名) 后 -> 点击 `添加` 。(此步已有可忽略)
	- 在 workers控制台的 `设置` 选项卡 -> 点击 `绑定` -> 右方点击 -> `添加` -> 选择 `KV 命名空间` -> 变量名称 填入 `amclubs` (此名称固定不能变) -> KV 命名空间 选择 在上面创建的 `命名空间名称` 后 -> 右下方点击 `部署` 。
4. 访问订阅内容：
	- 访问 `https://[YOUR-WORKERS-URL]/[UUID]` 即可获取订阅内容（默认UUID是：d0298536-d670-4045-bbb1-ddd5ea68683e）。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?sub` 就是你的通用自适应订阅地址(Quantumult X、Clash、singbox、小火箭、v2rayN、v2rayU、surge、PassWall、SSR+、Karing等)。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?base64` Base64订阅格式，适用PassWall,SSR+等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?clash` Clash订阅格式，适用OpenClash等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?singbox` singbox订阅格式，适用singbox等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?sub&IP_URL=https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/ipUrl.txt` 自动义变量等参数。
5. 修改默认UUID变量，使用KV存储桶(可选项，推荐修改，防止别人用你节点)：
	- 访问 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e/ui` 即可进入修改UUID页面
	- 在UUID页面UUID项 -> 填入 `新的UUID` 后,[在线获取UUID](https://1024tools.com/uuid) -> 点击 `Save` 。
	- 保存成功后，原UUID已作废不能访问，用新UUID访问 `https://vless.amclubss.com/新的UUID` 即可获取订阅内容。

### 二、Pages 上传 部署方法 最佳推荐!!! 视频教程

点击展开/收起
1. 部署 Cloudflare Pages：
	- 下载 [\_worker.js.zip](https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/_worker.js.zip) 文件，并点上 Star!!!
	- 在 Cloudflare Pages 控制台中选择 `上传资产` 后，为你的项目取名后点击 `创建项目` ，然后上传你下载好的 [\_worker.js.zip](https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/_worker.js.zip) 文件后点击 `部署站点` 。
2. 给 Pages绑定 CNAME自定义域：\[无域名绑定Cloudflare部署视频教程\]-> [免费域名教程1](https://youtu.be/wHJ6TJiCF0s) [免费域名教程2](https://youtu.be/yEF1YoLVmig) [免费域名教程3](https://www.youtube.com/watch?v=XS0EgqckUKo&t=320s)
	- 在 Pages控制台的 `自定义域` 选项卡，下方点击 `设置自定义域` 。
	- 填入你的自定义次级域名，注意不要使用你的根域名，例如：  
		您分配到的域名是 `amclubss.com` ，则添加自定义域填入 `vless.amclubss.com` 即可，点击 `激活域` 即可。
3. 给UUID设置KV存储桶(可选项，推荐设置)：
	- 在 CloudFlare主页的左边菜单的 ` 存储和数据库` 选项卡 -> 展开选择点击 `KV` -> 右方点击 -> `创建` -> 填入 `命名空间名称` (此名称自己命名) 后 -> 点击 `添加` 。(此步已有可忽略)
	- 在 workers控制台的 `设置` 选项卡 -> 点击 `绑定` -> 右方点击 -> `添加` -> 选择 `KV 命名空间` -> 变量名称 填入 `amclubs` (此名称固定不能变) -> KV 命名空间 选择 在上面创建的 `命名空间名称` 后 -> 右下方点击 `部署` 。
	- 在 `设置` 选项卡，在右上角点击 `创建部署` 后，重新上传 [\_worker.js.zip](https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/_worker.js.zip) 文件后点击 `保存并部署` 即可。
4. 访问订阅内容：
	- 访问 `https://[YOUR-WORKERS-URL]/[UUID]` 即可获取订阅内容（默认UUID是：d0298536-d670-4045-bbb1-ddd5ea68683e）。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?sub` 就是你的通用自适应订阅地址(Quantumult X、Clash、singbox、小火箭、v2rayN、v2rayU、surge、PassWall、SSR+、Karing等)。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?base64` Base64订阅格式，适用PassWall,SSR+等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?clash` Clash订阅格式，适用OpenClash等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?singbox` singbox订阅格式，适用singbox等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?sub&IP_URL=https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/ipUrl.txt` 自动义变量等参数。
5. 修改默认UUID变量，使用KV存储桶(可选项，推荐修改，防止别人用你节点)：
	- 访问 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e/ui` 即可进入修改UUID页面
	- 在UUID页面UUID项 -> 填入 `新的UUID` 后,[在线获取UUID](https://1024tools.com/uuid) -> 点击 `Save` 。
	- 保存成功后，原UUID已作废不能访问，用新UUID访问 `https://vless.amclubss.com/新的UUID` 即可获取订阅内容。

### 三、Pages GitHub 部署方法 视频教程

点击展开/收起
1. 部署 Cloudflare Pages：
	- 在 Github 上先 Fork 本项目，并点上 Star!!!
	- 在 Cloudflare Pages 控制台中选择 `连接到 Git` 后，选中 `am-cf-tunnel` 项目后点击 `开始设置` 。
	- 在 `设置构建和部署` 页面下方，后点击 `保存并部署` 即可。
2. 给 Pages绑定 CNAME自定义域：\[无域名绑定Cloudflare部署视频教程\]-> [免费域名教程1](https://youtu.be/wHJ6TJiCF0s) [免费域名教程2](https://youtu.be/yEF1YoLVmig) [免费域名教程3](https://www.youtube.com/watch?v=XS0EgqckUKo&t=320s)
	- 在 Pages控制台的 `自定义域` 选项卡，下方点击 `设置自定义域` 。
	- 填入你的自定义次级域名，注意不要使用你的根域名，例如：  
		您分配到的域名是 `amclubss.com` ，则添加自定义域填入 `vless.amclubss.com` 即可，点击 `激活域` 即可。
3. 给UUID设置KV存储桶(可选项，推荐设置)：
	- 在 CloudFlare主页的左边菜单的 ` 存储和数据库` 选项卡 -> 展开选择点击 `KV` -> 右方点击 -> `创建` -> 填入 `命名空间名称` (此名称自己命名) 后 -> 点击 `添加` 。(此步已有可忽略)
	- 在 workers控制台的 `设置` 选项卡 -> 点击 `绑定` -> 右方点击 -> `添加` -> 选择 `KV 命名空间` -> 变量名称 填入 `amclubs` (此名称固定不能变) -> KV 命名空间 选择 在上面创建的 `命名空间名称` 后 -> 右下方点击 `部署` 。
	- 在 `设置` 选项卡，在右上角点击 `创建部署` 后，重新选择 `部署` 即可。
4. 访问订阅内容：
	- 访问 `https://[YOUR-WORKERS-URL]/[UUID]` 即可获取订阅内容（默认UUID是：d0298536-d670-4045-bbb1-ddd5ea68683e）。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?sub` 就是你的通用自适应订阅地址(Quantumult X、Clash、singbox、小火箭、v2rayN、v2rayU、surge、PassWall、SSR+、Karing等)。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?base64` Base64订阅格式，适用PassWall,SSR+等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?clash` Clash订阅格式，适用OpenClash等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?singbox` singbox订阅格式，适用singbox等。
	- 例如 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e?sub&IP_URL=https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/ipUrl.txt` 自动义变量等参数。
5. 修改默认UUID变量，使用KV存储桶(可选项，推荐修改，防止别人用你节点)：
	- 访问 `https://vless.amclubss.com/d0298536-d670-4045-bbb1-ddd5ea68683e/ui` 即可进入修改UUID页面
	- 在UUID页面UUID项 -> 填入 `新的UUID` 后,[在线获取UUID](https://1024tools.com/uuid) -> 点击 `Save` 。
	- 保存成功后，原UUID已作废不能访问，用新UUID访问 `https://vless.amclubss.com/新的UUID` 即可获取订阅内容。

## 四、变量说明 视频教程

| 变量名 | 示例 | 必填 | 备注 | YT |
| --- | --- | --- | --- | --- |
| UUID | d0298536-d670-4045-bbb1-ddd5ea68683e（默认） | ✅ | 支持Cloudflare的KV存储桶设置 [在线获取UUID](https://1024tools.com/uuid) 如果是Trojan节点的变量是：PASSWORD |  |
| PROT\_TYPE | 默认空 | ❌ | 默认空,就是生成vless和trojan节点，vless(只生成vless节点)，trojan(只生成trojan节点) |  |
| IP\_URL | [https://raw.github…/ipUrl.txt](https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/ipUrl.txt) | ❌ | （推荐）优选(ipv4、ipv6、域名、API)地址(支持多个之间`,`或 换行 作间隔)，支持文件连接后里带PROXYIP参数，可以实现不同区域优先IP使用不同的PROXYIP固定区域，解决IP乱跳问题 | [教程](https://www.youtube.com/watch?v=4fcyJjstFdg&t=349s) |
| IP\_URL\_TXT | [https://raw.github…/ipv4.txt](https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/ipv4.txt) | ❌ | （不推荐）优选ipv4、ipv6、域名、API地址(支持多个之间`,`或 换行 作间隔) | [教程](https://youtu.be/dzxezRV1v-o) [教程](https://youtu.be/vX3U3FuuTT8) |
| IP\_URL\_CSV | [https://raw.github…/ipv4.csv](https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/ipv4.csv) | ❌ | （不推荐）优选ipv4/6的IP测速结果(支持多元素, 元素之间使用`,`作间隔) | [教程](https://youtu.be/vX3U3FuuTT8) |
| IP\_LOCAL | `icook.hk:2053#官方优选域名` | ❌ | （不推荐）本地优选域名/优选IP(支持多元素之间`,`或 换行 作间隔) |  |
| PROXYIP | [proxyip.amclubs.kozow.com](http://proxyip.amclubs.kozow.com/)   或   [https://raw.github…/proxyip.txt](https://raw.githubusercontent.com/amclubs/am-cf-tunnel/main/proxyip.txt) | ❌ | 访问CloudFlare的CDN代理节点(支持多PROXYIP, PROXYIP之间使用`,`或 换行 作间隔),支持端口设置默认443 如: [proxyip.amclubs.kozow.com:2053](http://proxyip.amclubs.kozow.com:2053/) ，支持远程txt或csv文件 | [教程](https://youtu.be/pKrlfRRB0gU) |
| SOCKS5 | user:password@127.0.0.1:1080 | ❌ | 优先作为访问CFCDN站点的SOCKS5代理 | [教程](https://youtu.be/Bw82BH_ecC4) |
| DNS\_RESOLVER\_URL | [https://cloudflare-dns.com/dns-query](https://cloudflare-dns.com/dns-query) | ❌ | DNS解析获取作用，小白勿用 |  |
| NO\_TLS | true/false | ❌ | 默认false,是否开启TLS系列端口，只有workers部署才可以使非用TLS系列端口 |  |
| SL | 5 | ❌ | `CSV` 文件里的测速结果满足速度下限 |  |
| SUB\_CONFIG | [https://raw.github…/ACL4SSR\_Online\_Mini.ini](https://raw.githubusercontent.com/amclubs/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | ❌ | clash、singbox等 订阅转换配置文件 |  |
| SUB\_CONVERTER | [url.v1.mk](http://url.v1.mk/) | ❌ | clash、singbox等 订阅转换后端的api地址 |  |
| SUB\_NAME | AM科技 | ❌ | 订阅名称 |  |
| CF\_EMAIL | [test@gmail.com](https://vercel.amclubss.com/) | ❌ | CF账户邮箱(要和 `CF_KEY` 同时填才生效, 订阅信息将显示请求使用量, 小白别用) |  |
| CF\_KEY | c6a944b5c9c18c235288bced8b85e | ❌ | CF账户Global API Key(要和 `CF_EMAIL` 同时填才生效, 订阅信息将显示请求使用量, 小白别用) |  |
| TG\_TOKEN | 6823456:XXXXXXX0qExVUhHDAbXXXqWXgBA | ❌ | 发送TG通知的机器人token |  |
| TG\_ID | 6946912345 | ❌ | 接收TG通知的账户数字ID |  |

## 五、已适配订阅工具 点击进入视频教程 点进进入karing视频教程

- Mac（苹果电脑）
	- [v2rayU](https://github.com/yanue/V2rayU/releases) | [clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev/releases) | [Quantumult X](https://apps.apple.com/us/app/quantumult-x/id1443988620) | [小火箭](https://apps.apple.com/us/app/shadowrocket/id932747118) | [surge](https://apps.apple.com/us/app/surge-5/id1442620678) | [karing](https://karing.app/download) | [sing-box](https://github.com/SagerNet/sing-box/releases) | [Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu/releases) | [openclash](https://github.com/vernesong/OpenClash/releases) | [Hiddify](https://github.com/hiddify/hiddify-next/releases)
- Win（win系统电脑）
	- [v2rayN](https://github.com/2dust/v2rayN/releases) | [clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev/releases) | [sing-box](https://github.com/SagerNet/sing-box/releases) | [Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu/releases) | [openclash](https://github.com/vernesong/OpenClash/releases) | [karing](https://karing.app/download) | [Hiddify](https://github.com/hiddify/hiddify-next/releases)
- IOS（苹果手机）
	- [clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev/releases) | [Quantumult X](https://apps.apple.com/us/app/quantumult-x/id1443988620) | [小火箭](https://apps.apple.com/us/app/shadowrocket/id932747118) | [surge](https://apps.apple.com/us/app/surge-5/id1442620678) | [sing-box](https://github.com/SagerNet/sing-box/releases) | [Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu/releases) | [karing](https://karing.app/download) | [Hiddify](https://github.com/hiddify/hiddify-next/releases)
- Android（安卓手机）
	- [v2rayNG](https://github.com/2dust/v2rayNG/releases) | [clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev/releases) | [sing-box](https://github.com/SagerNet/sing-box/releases) | [Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu/releases) | [karing](https://karing.app/download) | [Hiddify](https://github.com/hiddify/hiddify-next/releases)

