# 声明 
本文是学习[来自南亚的金刚象组织VajraEleph. ](https://siduwenku.com/view/55038?f=new_2023)而整理的学习笔记,分享出来希望更多人受益,如果存在侵权请及时联系我们
  
  
# 事件概要  
  
2022年2月，奇安信病毒响应中心移动安全团队关注到自2021年6月起至今，一个来自南亚某国背景的APT组织主要针对巴基斯坦军方展开了有组织、有计划、针对性的军事间谍情报活动。经过短短9个月的攻击，该组织已影响数十名巴基斯坦军方人员。这部分受害人员主要为巴基斯坦国家的边防军（FC）和特种部队（SSG），尤其是俾路支省边防军（FC BLN）；此外还包含少量的联邦调查局（FIA）和警察（Police）。另攻击还影响了少量的尼泊尔人员，但我国国内用户不受其影响。  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/401b8ccc77c6e375de6a4f8c219c2dbf.png)  
  
图1.1 受影响的国家分布情况图  
  
该组织通常使用公开的社交平台找到关注的目标后，结合色情话术等聊天诱导目标用户安装指定的诱饵聊天攻击应用进行钓鱼攻击。此外，攻击者还曾在国外某知名应用商店平台发布该恶意聊天应用，但目前相关链接已无法访问。  
  
截至本报告发布之时，我们已经截获的该组织所有攻击活动，都是通过Android平台进行的，尚未发现任何通过Windows平台进行的攻击。累计捕获恶意应用下载服务器8个，服务器上至少可以下载到5个不同的Android平台攻击样本。所有样本均为含有恶意代码的专用聊天软件。我们将所有这些捕获的恶意样本命名为VajraSpy。  
  
综合攻击活动特征、样本编码方式、C2服务器架构方式等多方面线索分析显示，该组织具有南亚某地区性大国政府背景，但又与该地区活跃的其他APT组织，如响尾蛇SideWinder、蔓灵花Bitter、肚脑虫Donot等没有显著关联（仅与肚脑虫Donot存在少量相似性），具有很强的独立性和独立特征。因此，我们判定该组织为活跃在南亚地区的新APT组织。我们将其命名为金刚象，英文名为VajraEleph，组织编号APT-Q-43。金刚象是奇安信独立发现并率先披露的的第15个APT组织。  
  
# 载荷投递  
  
通过奇安信病毒响应中心移动安全团队与奇安信威胁情报平台（https://ti.qianxin.com/） 的联合追踪分析发现，金刚象组织最早的活动可以追溯到2021年6月。 下图为我们截获的该组织最早的载荷服务器信息。  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/cb9bb7fbd3974fcc97505adeaac2bb09.png)  
  
图2.1 发现的最早域名载荷服务器相关截图（采用NameSilo注册商域名）  
  
该组织早期的攻击，通常会将攻击载荷下载地址的的“短链接”，通过Facebook、Whatsapp等社交软件发送给攻击目标。后期，随着各大社交平台对相关链接进行封禁，该组织转为将短链接以图片方式向目标人进行投递。  
  
| **载荷短链地址**             | **对应实际下载地址**                                    |  
|-----------------------------|---------------------------------------------------------|  
| https://cutt.ly/qIrgCKo     | https://appz.live/ichfghbtt/crazy.apk                   |  
| https://bit.ly/3BrCxNU      | https://appzshare.digital/coufgtdjvi/ZongChat(Beta).apk |  
| https://bit.ly/39roCMd      | https://apzshare.club/poahbcyskdh/cable.apk             |  
| https://rebrand.ly/Cable_v2 | https://appzshare.club/poahbcyskdh/cable.apk            |  
  
表1 已发现的载荷投递短链及其对应的实际下载地址  
  
该组织采用的载荷域名服务器注册时间均不到一年，注册商主要是NameSilo和NameCheap。这与近期在南亚活跃的另一个高级攻击组织肚脑虫的活动相似。  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/1830692eaf3cbe388e4c4840019acb05.png)  
  
图2.2 部分域名载荷服务器whois情况  
  
# 攻击目标  
  
金刚象组织具有明显的军事情报窃取意图，主要针对巴基斯坦军方人员，影响已涉及数种部队的数十名军方人员。以下是我们从攻击者C2服务器上截获的，部分受害者手机被窃取的照片和资料。  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/99abd3ad1b7d060c6e4d83d9b3be7a88.png)图3.1 巴基斯坦边防军（FC ，Frontier Corps）人员被窃照片  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/778362fb12dee24246384ffdd7de4417.jpeg)  
  
图3.2 巴基斯坦俾路支省边防军（ FC BLN ，FC Balochistan）人员被窃照片  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/e04f482b73f2cafb105fa79113959ffd.png)  
  
图3.3 俾路支省边防军人员被窃资料  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/21eb37b18e6022c2f969ae9f71fbfe60.jpeg)  
  
图3.4 巴基斯坦特种部队（SSG ，Special Service Group）人员被窃照片  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/0970199930f450bb7a4b5075095cd7dc.jpeg)  
  
图3.5 巴基斯坦警察被窃照片  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/82bed46601864fe42857cb2c1829f66a.png)  
  
图3.6 巴基斯坦警察被窃资料  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/daf66b6541010f17f9b9c0eb1653d23b.png)  
  
图3.7 巴基斯坦联邦调查局（FIA，Federal Investigation Agency）人员被窃照片  
  
![siduwenku.com 专注免费分享高质量文档](http://public.host.github5.com/media/a8fa56bf9bf016ca93158f297363c322.png)  
  
图3.8 关于陆军参谋长（COAS，Chief of Army Staff）的被窃资料  
  

# 延伸阅读 
 更多内容 可以[ 来自南亚的金刚象组织VajraEleph. ](https://siduwenku.com/view/55038?f=2023)进一步学习

# 联系我们
[T-FSI 086—2022 六氟异丙醇.pdf](http://github5.com/view/58638?f=new)
