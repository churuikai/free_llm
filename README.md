# 🌐 科学连接大模型教程

> 本教程帮助你解决 OpenAI、Google Scholar 等平台的注册、访问、封控、降智等问题

## 📋 目录

- [纯净的网络环境配置](#-1-纯净网络环境配置)
- [常用大模型平台注册与使用](#-2-常用大模型平台注册与使用)
- [大模型平台充值方法](#-3-常用大模型平台充值方法)
- [大模型API获取与使用](#-4-大模型api获取与使用)

## 🔒 1. 纯净网络环境配置

一般的科学上网无法解决问题；例如 OpenAI 封控、降智、禁止注册与充值，Google Scholar 频繁人机验证等。因为这些节点通常被诸多能人异士共享并污染，这里建议在普通节点之上自建纯净节点转发该类请求，从此无忧。

### 1.1 基础工具准备

1️⃣ **科学上网工具**

推荐 `Clash`
- [Clash 中文版](https://github.com/Z-Siqi/Clash-for-Windows_Chinese/releases) (一般下载 `Clash.for.Windows-0.20.39-Opt.1-win.7z` 即可)

2️⃣ **获取跳板节点**

纯净节点通常属于墙外网络，需要一个普通节点作为跳板。给出一些推荐：
- [魔戒](https://mojie.app/register?aff=6DpwXzur)（十分便宜，10元100G+流量）
- 如有推荐，欢迎提 issue

3️⃣ **获取纯净节点**

推荐使用`海外静态住宅代理`服务; 可几人共用，但不可太多人滥用。给出一些推荐：
- [Proxy302](https://share.proxy302.com/KNlOWp)（每月 7.99 美元）
- 如有推荐，欢迎提 issue
  
### 1.2 配置转发规则

4️⃣ **配置 Clash**

1. 点击配置 → 右键单击节点 → 点击设置 → 复制节点的 URL
2. 点击配置 → 右键单击节点 → 点击配置文件预处理 → 点击编辑解析器
3. 清空并粘贴以下内容（部分内容请按需调整）：

```yaml
parsers:
- reg: http*
    yaml:
    prepend-rules:
        # 拒绝 Adobe 软件更新
        - DOMAIN-KEYWORD,adobe.com,REJECT
        - DOMAIN-KEYWORD,adobelogin.com,REJECT
        - DOMAIN-KEYWORD,adobesc.com,REJECT
        - DOMAIN-KEYWORD,adobe.io,REJECT
        # 放通bing浏览器 
        - DOMAIN-KEYWORD,bing.com,DIRECT
        - DOMAIN-KEYWORD,pearcat.site,DIRECT
        # 放通deepseek
        - DOMAIN-KEYWORD,deepseek.com,DIRECT
        # 放通学术数据库
        - DOMAIN-KEYWORD,dl.acm.org,DIRECT
        - DOMAIN-KEYWORD,ieeexplore.ieee.org,DIRECT
        - DOMAIN-KEYWORD,springer.com,DIRECT
        # qwen 放通       
        - DOMAIN-KEYWORD,chat.qwenlm.ai,DIRECT
        # 部分内网放通
        - DOMAIN-KEYWORD,mermaid.ink,DIRECT
        # 放通 V3
        - DOMAIN-KEYWORD,api.gpt.ge,DIRECT
        - DOMAIN-KEYWORD,api.vveai.com,DIRECT
        - DOMAIN-KEYWORD,api.aaai.vip,DIRECT
        - DOMAIN-KEYWORD,api.v3,DIRECT
        # 火山引擎
        - DOMAIN-KEYWORD,console.volcengine.com,DIRECT
        # 魔戒
        - DOMAIN-KEYWORD,mojie.app,SELECT
        # openai 转发到纯净节点
        - DOMAIN,openaiapi-site.azureedge.net,relay
        - DOMAIN,openaicom-api-bdcpf8c6d2e9atf6.z01.azurefd.net,relay
        - DOMAIN,openaicomproductionae4b.blob.core.windows.net,relay
        - DOMAIN,production-openaicom-storage.azureedge.net,relay
        - DOMAIN-SUFFIX,chatgpt.com,relay
        - DOMAIN-SUFFIX,chat.com,relay
        - DOMAIN-SUFFIX,oaistatic.com,relay
        - DOMAIN-SUFFIX,oaiusercontent.com,relay
        - DOMAIN-SUFFIX,openai.com,relay
        - DOMAIN-SUFFIX,sora.com,relay
        - DOMAIN-SUFFIX,chatgpt.livekit.cloud,relay
        - DOMAIN-SUFFIX,host.livekit.cloud,relay
        - DOMAIN-SUFFIX,turn.livekit.cloud,relay
        - DOMAIN-SUFFIX,openai.com.cdn.cloudflare.net,relay
        - DOMAIN,o33249.ingest.sentry.io,relay
        - DOMAIN,openaicom.imgix.net,relay
        - DOMAIN,browser-intake-datadoghq.com,relay
        - DOMAIN-SUFFIX,coze.com,relay
        - DOMAIN-SUFFIX,ttwstatic.com,relay
        - DOMAIN-SUFFIX,byteoversea.com,relay
        - DOMAIN-SUFFIX,byteintlapi.com,relay
        # 谷歌学术 转发到纯净节点
        - DOMAIN-KEYWORD,scholar.google,relay
        # 谷歌 转发到纯净节点
        - DOMAIN-KEYWORD,google,relay
        # grok 转发到纯净节点
        - DOMAIN-KEYWORD,grok.com,relay
        - DOMAIN-KEYWORD,x.ai,relay
        # claude 转发到纯净节点
        - DOMAIN-KEYWORD,claude.ai,relay
        # cursor 转发到纯净节点
        - DOMAIN-KEYWORD,cursor,relay
        # 谷歌静态住宅代理
        - DOMAIN-KEYWORD,google,relay
        - DOMAIN-SUFFIX,0emm.com,relay
        - DOMAIN-SUFFIX,1ucrs.com,relay
        - DOMAIN-SUFFIX,2mdn.net,relay
        - DOMAIN-SUFFIX,466453.com,relay
        - DOMAIN-SUFFIX,abc.xyz,relay
        - DOMAIN-SUFFIX,adgoogle.net,relay
        - DOMAIN-SUFFIX,admeld.com,relay
        - DOMAIN-SUFFIX,admob.com,relay
        - DOMAIN-SUFFIX,adsense.com,relay
        - DOMAIN-SUFFIX,adsensecustomsearchads.com,relay
        - DOMAIN-SUFFIX,adsenseformobileapps.com,relay
        - DOMAIN-SUFFIX,advertisercommunity.com,relay
        - DOMAIN-SUFFIX,advertiserscommunity.com,relay
        - DOMAIN-SUFFIX,adwords-community.com,relay
        - DOMAIN-SUFFIX,adwords.com,relay
        - DOMAIN-SUFFIX,adwordsexpress.com,relay
        - DOMAIN-SUFFIX,amp.dev,relay
        - DOMAIN-SUFFIX,ampproject.com,relay
        - DOMAIN-SUFFIX,ampproject.net,relay
        - DOMAIN-SUFFIX,ampproject.org,relay
        - DOMAIN-SUFFIX,android.com,relay
        - DOMAIN-SUFFIX,androidify.com,relay
        - DOMAIN-SUFFIX,androidtv.com,relay
        - DOMAIN-SUFFIX,angulardart.org,relay
        - DOMAIN-SUFFIX,api.ai,relay
        - DOMAIN-SUFFIX,apigee.com,relay
        - DOMAIN-SUFFIX,app-measurement.com,relay
        - DOMAIN-SUFFIX,app-measurement.net,relay
        - DOMAIN-SUFFIX,appbridge.ca,relay
        - DOMAIN-SUFFIX,appbridge.io,relay
        - DOMAIN-SUFFIX,appbridge.it,relay
        - DOMAIN-SUFFIX,appspot.com,relay
        - DOMAIN-SUFFIX,apture.com,relay
        - DOMAIN-SUFFIX,area120.com,relay
        - DOMAIN-SUFFIX,asp-cc.com,relay
        - DOMAIN-SUFFIX,autodraw.com,relay
        - DOMAIN-SUFFIX,bandpage.com,relay
        - DOMAIN-SUFFIX,baselinestudy.com,relay
        - DOMAIN-SUFFIX,baselinestudy.org,relay
        - DOMAIN-SUFFIX,bazel.build,relay
        - DOMAIN-SUFFIX,bdn.dev,relay
        - DOMAIN-SUFFIX,beatthatquote.com,relay
        - DOMAIN-SUFFIX,blink.org,relay
        - DOMAIN-SUFFIX,blogblog.com,relay
        - DOMAIN-SUFFIX,blogger.com,relay
        - DOMAIN-KEYWORD,blogspot,relay
        - DOMAIN-SUFFIX,brocaproject.com,relay
        - DOMAIN-SUFFIX,brotli.org,relay
        - DOMAIN-SUFFIX,bumpshare.com,relay
        - DOMAIN-SUFFIX,bumptop.ca,relay
        - DOMAIN-SUFFIX,bumptop.com,relay
        - DOMAIN-SUFFIX,bumptop.net,relay
        - DOMAIN-SUFFIX,bumptop.org,relay
        - DOMAIN-SUFFIX,bumptunes.com,relay
        - DOMAIN-SUFFIX,campuslondon.com,relay
        - DOMAIN-SUFFIX,capitalg.com,relay
        - DOMAIN-SUFFIX,certificate-transparency.dev,relay
        - DOMAIN-SUFFIX,certificate-transparency.org,relay
        - DOMAIN-SUFFIX,charlestonroadregistry.com,relay
        - DOMAIN-SUFFIX,chat.gle,relay
        - DOMAIN-SUFFIX,chrome.com,relay
        - DOMAIN-SUFFIX,chromebook.com,relay
        - DOMAIN-SUFFIX,chromecast.com,relay
        - DOMAIN-SUFFIX,chromeexperiments.com,relay
        - DOMAIN-SUFFIX,chromeos.dev,relay
        - DOMAIN-SUFFIX,chromercise.com,relay
        - DOMAIN-SUFFIX,chromestatus.com,relay
        - DOMAIN-SUFFIX,chromium.org,relay
        - DOMAIN-SUFFIX,chronicle.security,relay
        - DOMAIN-SUFFIX,chroniclesec.com,relay
        - DOMAIN-SUFFIX,clickserver.googleads.com,relay
        - DOMAIN-SUFFIX,cloudburstresearch.com,relay
        - DOMAIN-SUFFIX,cloudfunctions.net,relay
        - DOMAIN-SUFFIX,cloudrobotics.com,relay
        - DOMAIN-SUFFIX,cobrasearch.com,relay
        - DOMAIN-SUFFIX,codespot.com,relay
        - DOMAIN-SUFFIX,conscrypt.com,relay
        - DOMAIN-SUFFIX,conscrypt.org,relay
        - DOMAIN-SUFFIX,cookiechoices.org,relay
        - DOMAIN-SUFFIX,coova.com,relay
        - DOMAIN-SUFFIX,coova.net,relay
        - DOMAIN-SUFFIX,coova.org,relay
        - DOMAIN-SUFFIX,crashlytics.com,relay
        - DOMAIN-SUFFIX,crbug.com,relay
        - DOMAIN-SUFFIX,creativelab5.com,relay
        - DOMAIN-SUFFIX,crossmediapanel.com,relay
        - DOMAIN-SUFFIX,crr.com,relay
        - DOMAIN-SUFFIX,crrev.com,relay
        - DOMAIN-SUFFIX,cs4hs.com,relay
        - DOMAIN-SUFFIX,dart.dev,relay
        - DOMAIN-SUFFIX,dartlang.org,relay
        - DOMAIN-SUFFIX,dartpad.dev,relay
        - DOMAIN-SUFFIX,dartsearch.net,relay
        - DOMAIN-SUFFIX,data-vocabulary.org,relay
        - DOMAIN-SUFFIX,dataliberation.org,relay
        - DOMAIN-SUFFIX,debug.com,relay
        - DOMAIN-SUFFIX,debugproject.com,relay
        - DOMAIN-SUFFIX,deepmind.com,relay
        - DOMAIN-SUFFIX,deja.com,relay
        - DOMAIN-SUFFIX,devsitetest.how,relay
        - DOMAIN-SUFFIX,dialogflow.com,relay
        - DOMAIN-SUFFIX,digisfera.com,relay
        - DOMAIN-SUFFIX,digitalassetlinks.org,relay
        - DOMAIN-SUFFIX,digitalattackmap.com,relay
        - DOMAIN-SUFFIX,doubleclick.com,relay
        - DOMAIN-SUFFIX,doubleclick.net,relay
        - DOMAIN-SUFFIX,episodic.com,relay
        - DOMAIN-SUFFIX,fastlane.ci,relay
        - DOMAIN-SUFFIX,fastlane.tools,relay
        - DOMAIN-SUFFIX,feedburner.com,relay
        - DOMAIN-SUFFIX,fflick.com,relay
        - DOMAIN-SUFFIX,financeleadsonline.com,relay
        - DOMAIN-SUFFIX,firebaseapp.com,relay
        - DOMAIN-SUFFIX,firebaseio.com,relay
        - DOMAIN-SUFFIX,flutter.dev,relay
        - DOMAIN-SUFFIX,flutterapp.com,relay
        - DOMAIN-SUFFIX,foofle.com,relay
        - DOMAIN-SUFFIX,froogle.com,relay
        - DOMAIN-SUFFIX,fuchsia.dev,relay
        - DOMAIN-SUFFIX,g-tun.com,relay
        - DOMAIN-SUFFIX,g.cn,relay
        - DOMAIN-SUFFIX,g.co,relay
        - DOMAIN-SUFFIX,g.dev,relay
        - DOMAIN-SUFFIX,g.page,relay
        - DOMAIN-SUFFIX,gateway.dev,relay
        - DOMAIN-SUFFIX,gcr.io,relay
        - DOMAIN-SUFFIX,gerritcodereview.com,relay
        - DOMAIN-SUFFIX,get.app,relay
        - DOMAIN-SUFFIX,get.dev,relay
        - DOMAIN-SUFFIX,get.how,relay
        - DOMAIN-SUFFIX,get.page,relay
        - DOMAIN-SUFFIX,getbumptop.com,relay
        - DOMAIN-SUFFIX,getmdl.io,relay
        - DOMAIN-SUFFIX,getoutline.org,relay
        - DOMAIN-SUFFIX,ggoogle.com,relay
        - DOMAIN-SUFFIX,ggpht.cn,relay
        - DOMAIN-SUFFIX,ggpht.com,relay
        - DOMAIN-SUFFIX,gipscorp.com,relay
        - DOMAIN-SUFFIX,gkecnapps.cn,relay
        - DOMAIN-SUFFIX,globaledu.org,relay
        - DOMAIN-SUFFIX,gmail.com,relay
        - DOMAIN-SUFFIX,gmodules.com,relay
        - DOMAIN-SUFFIX,go-lang.com,relay
        - DOMAIN-SUFFIX,go-lang.net,relay
        - DOMAIN-SUFFIX,go-lang.org,relay
        - DOMAIN-SUFFIX,go.dev,relay
        - DOMAIN-SUFFIX,godoc.org,relay
        - DOMAIN-SUFFIX,gogle.com,relay
        - DOMAIN-SUFFIX,gogole.com,relay
        - DOMAIN-SUFFIX,golang.com,relay
        - DOMAIN-SUFFIX,golang.net,relay
        - DOMAIN-SUFFIX,golang.org,relay
        - DOMAIN-SUFFIX,gonglchuangl.net,relay
        - DOMAIN-SUFFIX,goo.gl,relay
        - DOMAIN-SUFFIX,googil.com,relay
        - DOMAIN-SUFFIX,googl.com,relay
        - DOMAIN-SUFFIX,googlr.com,relay
        - DOMAIN-SUFFIX,goolge.com,relay
        - DOMAIN-SUFFIX,gooogle.com,relay
        - DOMAIN-SUFFIX,gridaware.app,relay
        - DOMAIN-SUFFIX,gsrc.io,relay
        - DOMAIN-SUFFIX,gstatic.cn,relay
        - DOMAIN-SUFFIX,gstatic.com,relay
        - DOMAIN-SUFFIX,gstaticcnapps.cn,relay
        - DOMAIN-SUFFIX,gsuite.com,relay
        - DOMAIN-SUFFIX,gv.com,relay
        - DOMAIN-SUFFIX,gvt0.com,relay
        - DOMAIN-SUFFIX,gvt1.com,relay
        - DOMAIN-SUFFIX,gvt2.com,relay
        - DOMAIN-SUFFIX,gvt3.com,relay
        - DOMAIN-SUFFIX,gvt5.com,relay
        - DOMAIN-SUFFIX,gvt6.com,relay
        - DOMAIN-SUFFIX,gvt7.com,relay
        - DOMAIN-SUFFIX,gvt9.com,relay
        - DOMAIN-SUFFIX,gwtproject.org,relay
        - DOMAIN-SUFFIX,hdrplusdata.org,relay
        - DOMAIN-SUFFIX,hey.gle,relay
        - DOMAIN-SUFFIX,hindiweb.com,relay
        - DOMAIN-SUFFIX,howtogetmo.co.uk,relay
        - DOMAIN-SUFFIX,html5rocks.com,relay
        - DOMAIN-SUFFIX,hwgo.com,relay
        - DOMAIN-SUFFIX,iam.soy,relay
        - DOMAIN-SUFFIX,iamremarkable.org,relay
        - DOMAIN-SUFFIX,igoogle.com,relay
        - DOMAIN-SUFFIX,impermium.com,relay
        - DOMAIN-SUFFIX,itasoftware.com,relay
        - DOMAIN-SUFFIX,j2objc.org,relay
        - DOMAIN-SUFFIX,jibemobile.com,relay
        - DOMAIN-SUFFIX,kaggle.com,relay
        - DOMAIN-SUFFIX,kaggle.io,relay
        - DOMAIN-SUFFIX,keyhole.com,relay
        - DOMAIN-SUFFIX,keytransparency.com,relay
        - DOMAIN-SUFFIX,keytransparency.foo,relay
        - DOMAIN-SUFFIX,keytransparency.org,relay
        - DOMAIN-SUFFIX,lanternal.com,relay
        - DOMAIN-SUFFIX,like.com,relay
        - DOMAIN-SUFFIX,madewithcode.com,relay
        - DOMAIN-SUFFIX,material.io,relay
        - DOMAIN-SUFFIX,mdialog.com,relay
        - DOMAIN-SUFFIX,meet.new,relay
        - DOMAIN-SUFFIX,mfg-inspector.com,relay
        - DOMAIN-SUFFIX,mobileview.page,relay
        - DOMAIN-SUFFIX,moodstocks.com,relay
        - DOMAIN-SUFFIX,near.by,relay
        - DOMAIN-SUFFIX,nest.com,relay
        - DOMAIN-SUFFIX,neverware.com,relay
        - DOMAIN-SUFFIX,nomulus.foo,relay
        - DOMAIN-SUFFIX,oasisfeng.com,relay
        - DOMAIN-SUFFIX,oauthz.com,relay
        - DOMAIN-SUFFIX,ok.gle,relay
        - DOMAIN-SUFFIX,on.here,relay
        - DOMAIN-SUFFIX,on2.com,relay
        - DOMAIN-SUFFIX,onefifteen.net,relay
        - DOMAIN-SUFFIX,onefifteen.org,relay
        - DOMAIN-SUFFIX,oneworldmanystories.com,relay
        - DOMAIN-SUFFIX,openthread.io,relay
        - DOMAIN-SUFFIX,openweave.io,relay
        - DOMAIN-SUFFIX,orbitera.com,relay
        - DOMAIN-SUFFIX,page.link,relay
        - DOMAIN-SUFFIX,pagespeedmobilizer.com,relay
        - DOMAIN-SUFFIX,pageview.mobi,relay
        - DOMAIN-SUFFIX,panoramio.com,relay
        - DOMAIN-SUFFIX,partylikeits1986.org,relay
        - DOMAIN-SUFFIX,paxlicense.org,relay
        - DOMAIN-SUFFIX,picasa.com,relay
        - DOMAIN-SUFFIX,picasaweb.com,relay
        - DOMAIN-SUFFIX,picasaweb.net,relay
        - DOMAIN-SUFFIX,picasaweb.org,relay
        - DOMAIN-SUFFIX,picnik.com,relay
        - DOMAIN-SUFFIX,pittpatt.com,relay
        - DOMAIN-SUFFIX,pixate.com,relay
        - DOMAIN-SUFFIX,pki.goog,relay
        - DOMAIN-SUFFIX,plus.codes,relay
        - DOMAIN-SUFFIX,polymer-project.org,relay
        - DOMAIN-SUFFIX,polymerproject.org,relay
        - DOMAIN-SUFFIX,postini.com,relay
        - DOMAIN-SUFFIX,privacysandbox.com,relay
        - DOMAIN-SUFFIX,projectara.com,relay
        - DOMAIN-SUFFIX,projectbaseline.com,relay
        - DOMAIN-SUFFIX,publishproxy.com,relay
        - DOMAIN-SUFFIX,questvisual.com,relay
        - DOMAIN-SUFFIX,quickoffice.com,relay
        - DOMAIN-SUFFIX,quiksee.com,relay
        - DOMAIN-SUFFIX,recaptcha.net,relay
        - DOMAIN-SUFFIX,redhotlabs.com,relay
        - DOMAIN-SUFFIX,registry.google,relay
        - DOMAIN-SUFFIX,revolv.com,relay
        - DOMAIN-SUFFIX,ridepenguin.com,relay
        - DOMAIN-SUFFIX,run.app,relay
        - DOMAIN-SUFFIX,savethedate.foo,relay
        - DOMAIN-SUFFIX,saynow.com,relay
        - DOMAIN-SUFFIX,schema.org,relay
        - DOMAIN-SUFFIX,schemer.com,relay
        - DOMAIN-SUFFIX,screenwisetrends.com,relay
        - DOMAIN-SUFFIX,screenwisetrendspanel.com,relay
        - DOMAIN-SUFFIX,shattered.io,relay
        - DOMAIN-SUFFIX,snapseed.com,relay
        - DOMAIN-SUFFIX,solveforx.com,relay
        - DOMAIN-SUFFIX,stadia.dev,relay
        - DOMAIN-SUFFIX,stcroixmosquito.com,relay
        - DOMAIN-SUFFIX,stcroixmosquitoproject.com,relay
        - DOMAIN-SUFFIX,studywatchbyverily.com,relay
        - DOMAIN-SUFFIX,studywatchbyverily.org,relay
        - DOMAIN-SUFFIX,stxmosquito.com,relay
        - DOMAIN-SUFFIX,stxmosquitoproject.com,relay
        - DOMAIN-SUFFIX,stxmosquitoproject.net,relay
        - DOMAIN-SUFFIX,stxmosquitoproject.org,relay
        - DOMAIN-SUFFIX,synergyse.com,relay
        - DOMAIN-SUFFIX,teachparentstech.org,relay
        - DOMAIN-SUFFIX,telephony.goog,relay
        - DOMAIN-SUFFIX,tensorflow.org,relay
        - DOMAIN-SUFFIX,tfhub.dev,relay
        - DOMAIN-SUFFIX,thecleversense.com,relay
        - DOMAIN-SUFFIX,thegooglestore.com,relay
        - DOMAIN-SUFFIX,thinkquarterly.co.uk,relay
        - DOMAIN-SUFFIX,thinkquarterly.com,relay
        - DOMAIN-SUFFIX,thinkwithgoogle.com,relay
        - DOMAIN-SUFFIX,tiltbrush.com,relay
        - DOMAIN-SUFFIX,txcloud.net,relay
        - DOMAIN-SUFFIX,txvia.com,relay
        - DOMAIN-SUFFIX,unfiltered.news,relay
        - DOMAIN-SUFFIX,urchin.com,relay
        - DOMAIN-SUFFIX,useplannr.com,relay
        - DOMAIN-SUFFIX,usvimosquito.com,relay
        - DOMAIN-SUFFIX,usvimosquitoproject.com,relay
        - DOMAIN-SUFFIX,v8.dev,relay
        - DOMAIN-SUFFIX,v8project.org,relay
        - DOMAIN-SUFFIX,velostrata.com,relay
        - DOMAIN-SUFFIX,verily.com,relay
        - DOMAIN-SUFFIX,verilylifesciences.com,relay
        - DOMAIN-SUFFIX,verilystudyhub.com,relay
        - DOMAIN-SUFFIX,verilystudywatch.com,relay
        - DOMAIN-SUFFIX,verilystudywatch.org,relay
        - DOMAIN-SUFFIX,wallet.com,relay
        - DOMAIN-SUFFIX,waveprotocol.org,relay
        - DOMAIN-SUFFIX,waymo.com,relay
        - DOMAIN-SUFFIX,waze.com,relay
        - DOMAIN-SUFFIX,web.app,relay
        - DOMAIN-SUFFIX,web.dev,relay
        - DOMAIN-SUFFIX,webappfieldguide.com,relay
        - DOMAIN-SUFFIX,webmproject.org,relay
        - DOMAIN-SUFFIX,webpkgcache.com,relay
        - DOMAIN-SUFFIX,webrtc.org,relay
        - DOMAIN-SUFFIX,weltweitwachsen.de,relay
        - DOMAIN-SUFFIX,whatbrowser.org,relay
        - DOMAIN-SUFFIX,widevine.com,relay
        - DOMAIN-SUFFIX,withgoogle.com,relay
        - DOMAIN-SUFFIX,womenwill.com,relay
        - DOMAIN-SUFFIX,womenwill.com.br,relay
        - DOMAIN-SUFFIX,womenwill.id,relay
        - DOMAIN-SUFFIX,womenwill.in,relay
        - DOMAIN-SUFFIX,womenwill.mx,relay
        - DOMAIN-SUFFIX,x.company,relay
        - DOMAIN-SUFFIX,x.team,relay
        - DOMAIN-SUFFIX,xn--9kr7l.com,relay
        - DOMAIN-SUFFIX,xn--9trs65b.com,relay
        - DOMAIN-SUFFIX,xn--flw351e.com,relay
        - DOMAIN-SUFFIX,xn--ggle-55da.com,relay
        - DOMAIN-SUFFIX,xn--gogl-0nd52e.com,relay
        - DOMAIN-SUFFIX,xn--gogl-1nd42e.com,relay
        - DOMAIN-SUFFIX,xn--ngstr-lra8j.com,relay
        - DOMAIN-SUFFIX,xn--p8j9a0d9c9a.xn--q9jyb4c,relay
        - DOMAIN-SUFFIX,xplr.co,relay
        - DOMAIN-SUFFIX,youtu.be,relay
        - DOMAIN-SUFFIX,yt.be,relay
        - DOMAIN-SUFFIX,ytimg.com,relay
        - DOMAIN-SUFFIX,zukunftswerkstatt.de,relay
        - DOMAIN-SUFFIX,zynamics.com,relay
        - DOMAIN-KEYWORD,appspot,relay
        - DOMAIN-KEYWORD,blogspot,relay
        - DOMAIN-KEYWORD,gmail,relay
        - DOMAIN-KEYWORD,google,relay
        - DOMAIN-KEYWORD,gstatic,relay
        - DOMAIN-KEYWORD,recaptcha,relay
        - IP-CIDR,172.110.32.0/21,relay,no-resolve
        - IP-CIDR,173.194.0.0/16,relay,no-resolve
        - IP-CIDR,216.73.80.0/20,relay,no-resolve
        - IP-CIDR,74.125.0.0/16,relay,no-resolve


    prepend-proxies:
        - name: 纯净节点1
          type: ****
          server: **********
          port: ****
          username: ************
          password: ************
    prepend-proxy-groups:

        - name: 纯净节点前置代理
          type: select
          proxies:
            - SELECT
            - DIRECT

        - name: 纯净节点
          type: select
          proxies:
            - 纯净节点1
            - DIRECT

        - name: relay
          type: relay
          proxies:
            - 纯净节点前置代理
            - 纯净节点
# 魔戒
- url: ******** （此处粘贴刚刚复制的 url）
    yaml:
    prepend-proxy-groups:
        - name: SELECT
          type: select
          proxies:
            - 节点选择
```

> **说明**：规则可以按需增添，以上规则只是笔者个人所需。纯净节点需自备，URL 为刚刚复制的内容。保存后更新该配置，正常能够在代理中看到多出了 `纯净节点前置代理`、`纯净节点`、`relay` 三个分组。

📢 **完成设置后**：启用代理后，OpenAI、Google、Google Scholar、Grok、Claude 等请求就会被转发到你的纯净节点，规避封控。同时下载一些学术论文也不必关闭代理。


## 👤 2. 常用大模型平台注册与使用

### OpenAI

- 网络环境纯净，使用 Google 账号登录即可，无需国外手机验证
- 注意在右上角头像 → Settings → General 中语言切换为英文，进一步规避风险

### Google Scholar

- 纯净网络 + 切换为英文，从此远离一切人机验证

### ......


## 💳 3. 常用大模型平台充值方法

大多数平台需要国外信用卡，推荐使用信用卡代理平台。

- [Wildcard](https://bewildcard.com/i/RLEYJ1IK)
  - 优势：提供一键充值大模型服务（网络环境纯净的情况下十分可行）
  - 缺点：需要支付一次性开卡费和少量手续费
- 如有推荐，欢迎提 issue


## 🔑 4. 大模型API获取与使用

> 待补充
