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
3. 清空并粘贴以下内容（请按需调整）：

```yaml
parsers:
  - reg: http*
    yaml:
      prepend-rules:
        # github
        - DOMAIN-KEYWORD,github.com,SELECT

        # 拒绝 Adobe 软件更新
        - DOMAIN-KEYWORD,adobe.com,REJECT
        - DOMAIN-KEYWORD,adobelogin.com,REJECT
        - DOMAIN-KEYWORD,adobesc.com,REJECT
        - DOMAIN-KEYWORD,adobe.io,REJECT

        # 学术数据库
        - DOMAIN-KEYWORD,dl.acm.org,论文数据库--
        - DOMAIN-KEYWORD,ieeexplore.ieee.org,论文数据库--
        - DOMAIN-KEYWORD,springer.com,论文数据库--
        - DOMAIN-KEYWORD,scholar.google,论文数据库--

        # 魔戒
        - DOMAIN-KEYWORD,mojie.app,SELECT

        # openai
        - DOMAIN,openaiapi-site.azureedge.net,AI平台--
        - DOMAIN,openaicom-api-bdcpf8c6d2e9atf6.z01.azurefd.net,AI平台--
        - DOMAIN,openaicomproductionae4b.blob.core.windows.net,AI平台--
        - DOMAIN,production-openaicom-storage.azureedge.net,AI平台--
        - DOMAIN-SUFFIX,chatgpt.com,AI平台--
        - DOMAIN-SUFFIX,chat.com,AI平台--
        - DOMAIN-SUFFIX,oaistatic.com,AI平台--
        - DOMAIN-SUFFIX,oaiusercontent.com,AI平台--
        - DOMAIN-SUFFIX,openai.com,AI平台--
        - DOMAIN-SUFFIX,sora.com,AI平台--
        - DOMAIN-SUFFIX,chatgpt.livekit.cloud,AI平台--
        - DOMAIN-SUFFIX,host.livekit.cloud,AI平台--
        - DOMAIN-SUFFIX,turn.livekit.cloud,AI平台--
        - DOMAIN-SUFFIX,openai.com.cdn.cloudflare.net,AI平台--
        - DOMAIN,o33249.ingest.sentry.io,AI平台--
        - DOMAIN,openaicom.imgix.net,AI平台--
        - DOMAIN,browser-intake-datadoghq.com,AI平台--
        - DOMAIN-SUFFIX,coze.com,AI平台--
        - DOMAIN-SUFFIX,ttwstatic.com,AI平台--
        - DOMAIN-SUFFIX,byteoversea.com,AI平台--
        - DOMAIN-SUFFIX,byteintlapi.com,AI平台--

        # cursor 和 claude
        - DOMAIN-KEYWORD,cursor,AI平台--
        - DOMAIN-KEYWORD,sheerid.com,AI平台--
        - DOMAIN-KEYWORD,claude.ai,AI平台--
        - DOMAIN-KEYWORD,grok.com,AI平台--
        - DOMAIN-KEYWORD,x.ai,AI平台--

        # 谷歌服务--
        - DOMAIN-KEYWORD,google,谷歌服务--
        - DOMAIN-SUFFIX,0emm.com,谷歌服务--
        - DOMAIN-SUFFIX,1ucrs.com,谷歌服务--
        - DOMAIN-SUFFIX,2mdn.net,谷歌服务--
        - DOMAIN-SUFFIX,466453.com,谷歌服务--
        - DOMAIN-SUFFIX,abc.xyz,谷歌服务--
        - DOMAIN-SUFFIX,adgoogle.net,谷歌服务--
        - DOMAIN-SUFFIX,admeld.com,谷歌服务--
        - DOMAIN-SUFFIX,admob.com,谷歌服务--
        - DOMAIN-SUFFIX,adsense.com,谷歌服务--
        - DOMAIN-SUFFIX,adsensecustomsearchads.com,谷歌服务--
        - DOMAIN-SUFFIX,adsenseformobileapps.com,谷歌服务--
        - DOMAIN-SUFFIX,advertisercommunity.com,谷歌服务--
        - DOMAIN-SUFFIX,advertiserscommunity.com,谷歌服务--
        - DOMAIN-SUFFIX,adwords-community.com,谷歌服务--
        - DOMAIN-SUFFIX,adwords.com,谷歌服务--
        - DOMAIN-SUFFIX,adwordsexpress.com,谷歌服务--
        - DOMAIN-SUFFIX,amp.dev,谷歌服务--
        - DOMAIN-SUFFIX,ampproject.com,谷歌服务--
        - DOMAIN-SUFFIX,ampproject.net,谷歌服务--
        - DOMAIN-SUFFIX,ampproject.org,谷歌服务--
        - DOMAIN-SUFFIX,android.com,谷歌服务--
        - DOMAIN-SUFFIX,androidify.com,谷歌服务--
        - DOMAIN-SUFFIX,androidtv.com,谷歌服务--
        - DOMAIN-SUFFIX,angulardart.org,谷歌服务--
        - DOMAIN-SUFFIX,api.ai,谷歌服务--
        - DOMAIN-SUFFIX,apigee.com,谷歌服务--
        - DOMAIN-SUFFIX,app-measurement.com,谷歌服务--
        - DOMAIN-SUFFIX,app-measurement.net,谷歌服务--
        - DOMAIN-SUFFIX,appbridge.ca,谷歌服务--
        - DOMAIN-SUFFIX,appbridge.io,谷歌服务--
        - DOMAIN-SUFFIX,appbridge.it,谷歌服务--
        - DOMAIN-SUFFIX,appspot.com,谷歌服务--
        - DOMAIN-SUFFIX,apture.com,谷歌服务--
        - DOMAIN-SUFFIX,area120.com,谷歌服务--
        - DOMAIN-SUFFIX,asp-cc.com,谷歌服务--
        - DOMAIN-SUFFIX,autodraw.com,谷歌服务--
        - DOMAIN-SUFFIX,bandpage.com,谷歌服务--
        - DOMAIN-SUFFIX,baselinestudy.com,谷歌服务--
        - DOMAIN-SUFFIX,baselinestudy.org,谷歌服务--
        - DOMAIN-SUFFIX,bazel.build,谷歌服务--
        - DOMAIN-SUFFIX,bdn.dev,谷歌服务--
        - DOMAIN-SUFFIX,beatthatquote.com,谷歌服务--
        - DOMAIN-SUFFIX,blink.org,谷歌服务--
        - DOMAIN-SUFFIX,blogblog.com,谷歌服务--
        - DOMAIN-SUFFIX,blogger.com,谷歌服务--
        - DOMAIN-KEYWORD,blogspot,谷歌服务--
        - DOMAIN-SUFFIX,brocaproject.com,谷歌服务--
        - DOMAIN-SUFFIX,brotli.org,谷歌服务--
        - DOMAIN-SUFFIX,bumpshare.com,谷歌服务--
        - DOMAIN-SUFFIX,bumptop.ca,谷歌服务--
        - DOMAIN-SUFFIX,bumptop.com,谷歌服务--
        - DOMAIN-SUFFIX,bumptop.net,谷歌服务--
        - DOMAIN-SUFFIX,bumptop.org,谷歌服务--
        - DOMAIN-SUFFIX,bumptunes.com,谷歌服务--
        - DOMAIN-SUFFIX,campuslondon.com,谷歌服务--
        - DOMAIN-SUFFIX,capitalg.com,谷歌服务--
        - DOMAIN-SUFFIX,certificate-transparency.dev,谷歌服务--
        - DOMAIN-SUFFIX,certificate-transparency.org,谷歌服务--
        - DOMAIN-SUFFIX,charlestonroadregistry.com,谷歌服务--
        - DOMAIN-SUFFIX,chat.gle,谷歌服务--
        - DOMAIN-SUFFIX,chrome.com,谷歌服务--
        - DOMAIN-SUFFIX,chromebook.com,谷歌服务--
        - DOMAIN-SUFFIX,chromecast.com,谷歌服务--
        - DOMAIN-SUFFIX,chromeexperiments.com,谷歌服务--
        - DOMAIN-SUFFIX,chromeos.dev,谷歌服务--
        - DOMAIN-SUFFIX,chromercise.com,谷歌服务--
        - DOMAIN-SUFFIX,chromestatus.com,谷歌服务--
        - DOMAIN-SUFFIX,chromium.org,谷歌服务--
        - DOMAIN-SUFFIX,chronicle.security,谷歌服务--
        - DOMAIN-SUFFIX,chroniclesec.com,谷歌服务--
        - DOMAIN-SUFFIX,clickserver.googleads.com,谷歌服务--
        - DOMAIN-SUFFIX,cloudburstresearch.com,谷歌服务--
        - DOMAIN-SUFFIX,cloudfunctions.net,谷歌服务--
        - DOMAIN-SUFFIX,cloudrobotics.com,谷歌服务--
        - DOMAIN-SUFFIX,cobrasearch.com,谷歌服务--
        - DOMAIN-SUFFIX,codespot.com,谷歌服务--
        - DOMAIN-SUFFIX,conscrypt.com,谷歌服务--
        - DOMAIN-SUFFIX,conscrypt.org,谷歌服务--
        - DOMAIN-SUFFIX,cookiechoices.org,谷歌服务--
        - DOMAIN-SUFFIX,coova.com,谷歌服务--
        - DOMAIN-SUFFIX,coova.net,谷歌服务--
        - DOMAIN-SUFFIX,coova.org,谷歌服务--
        - DOMAIN-SUFFIX,crashlytics.com,谷歌服务--
        - DOMAIN-SUFFIX,crbug.com,谷歌服务--
        - DOMAIN-SUFFIX,creativelab5.com,谷歌服务--
        - DOMAIN-SUFFIX,crossmediapanel.com,谷歌服务--
        - DOMAIN-SUFFIX,crr.com,谷歌服务--
        - DOMAIN-SUFFIX,crrev.com,谷歌服务--
        - DOMAIN-SUFFIX,cs4hs.com,谷歌服务--
        - DOMAIN-SUFFIX,dart.dev,谷歌服务--
        - DOMAIN-SUFFIX,dartlang.org,谷歌服务--
        - DOMAIN-SUFFIX,dartpad.dev,谷歌服务--
        - DOMAIN-SUFFIX,dartsearch.net,谷歌服务--
        - DOMAIN-SUFFIX,data-vocabulary.org,谷歌服务--
        - DOMAIN-SUFFIX,dataliberation.org,谷歌服务--
        - DOMAIN-SUFFIX,debug.com,谷歌服务--
        - DOMAIN-SUFFIX,debugproject.com,谷歌服务--
        - DOMAIN-SUFFIX,deepmind.com,谷歌服务--
        - DOMAIN-SUFFIX,deja.com,谷歌服务--
        - DOMAIN-SUFFIX,devsitetest.how,谷歌服务--
        - DOMAIN-SUFFIX,dialogflow.com,谷歌服务--
        - DOMAIN-SUFFIX,digisfera.com,谷歌服务--
        - DOMAIN-SUFFIX,digitalassetlinks.org,谷歌服务--
        - DOMAIN-SUFFIX,digitalattackmap.com,谷歌服务--
        - DOMAIN-SUFFIX,doubleclick.com,谷歌服务--
        - DOMAIN-SUFFIX,doubleclick.net,谷歌服务--
        - DOMAIN-SUFFIX,episodic.com,谷歌服务--
        - DOMAIN-SUFFIX,fastlane.ci,谷歌服务--
        - DOMAIN-SUFFIX,fastlane.tools,谷歌服务--
        - DOMAIN-SUFFIX,feedburner.com,谷歌服务--
        - DOMAIN-SUFFIX,fflick.com,谷歌服务--
        - DOMAIN-SUFFIX,financeleadsonline.com,谷歌服务--
        - DOMAIN-SUFFIX,firebaseapp.com,谷歌服务--
        - DOMAIN-SUFFIX,firebaseio.com,谷歌服务--
        - DOMAIN-SUFFIX,flutter.dev,谷歌服务--
        - DOMAIN-SUFFIX,flutterapp.com,谷歌服务--
        - DOMAIN-SUFFIX,foofle.com,谷歌服务--
        - DOMAIN-SUFFIX,froogle.com,谷歌服务--
        - DOMAIN-SUFFIX,fuchsia.dev,谷歌服务--
        - DOMAIN-SUFFIX,g-tun.com,谷歌服务--
        - DOMAIN-SUFFIX,g.cn,谷歌服务--
        - DOMAIN-SUFFIX,g.co,谷歌服务--
        - DOMAIN-SUFFIX,g.dev,谷歌服务--
        - DOMAIN-SUFFIX,g.page,谷歌服务--
        - DOMAIN-SUFFIX,gateway.dev,谷歌服务--
        - DOMAIN-SUFFIX,gcr.io,谷歌服务--
        - DOMAIN-SUFFIX,gerritcodereview.com,谷歌服务--
        - DOMAIN-SUFFIX,get.app,谷歌服务--
        - DOMAIN-SUFFIX,get.dev,谷歌服务--
        - DOMAIN-SUFFIX,get.how,谷歌服务--
        - DOMAIN-SUFFIX,get.page,谷歌服务--
        - DOMAIN-SUFFIX,getbumptop.com,谷歌服务--
        - DOMAIN-SUFFIX,getmdl.io,谷歌服务--
        - DOMAIN-SUFFIX,getoutline.org,谷歌服务--
        - DOMAIN-SUFFIX,ggoogle.com,谷歌服务--
        - DOMAIN-SUFFIX,ggpht.cn,谷歌服务--
        - DOMAIN-SUFFIX,ggpht.com,谷歌服务--
        - DOMAIN-SUFFIX,gipscorp.com,谷歌服务--
        - DOMAIN-SUFFIX,gkecnapps.cn,谷歌服务--
        - DOMAIN-SUFFIX,globaledu.org,谷歌服务--
        - DOMAIN-SUFFIX,gmail.com,谷歌服务--
        - DOMAIN-SUFFIX,gmodules.com,谷歌服务--
        - DOMAIN-SUFFIX,go-lang.com,谷歌服务--
        - DOMAIN-SUFFIX,go-lang.net,谷歌服务--
        - DOMAIN-SUFFIX,go-lang.org,谷歌服务--
        - DOMAIN-SUFFIX,go.dev,谷歌服务--
        - DOMAIN-SUFFIX,godoc.org,谷歌服务--
        - DOMAIN-SUFFIX,gogle.com,谷歌服务--
        - DOMAIN-SUFFIX,gogole.com,谷歌服务--
        - DOMAIN-SUFFIX,golang.com,谷歌服务--
        - DOMAIN-SUFFIX,golang.net,谷歌服务--
        - DOMAIN-SUFFIX,golang.org,谷歌服务--
        - DOMAIN-SUFFIX,gonglchuangl.net,谷歌服务--
        - DOMAIN-SUFFIX,goo.gl,谷歌服务--
        - DOMAIN-SUFFIX,googil.com,谷歌服务--
        - DOMAIN-SUFFIX,googl.com,谷歌服务--
        - DOMAIN-SUFFIX,googlr.com,谷歌服务--
        - DOMAIN-SUFFIX,goolge.com,谷歌服务--
        - DOMAIN-SUFFIX,gooogle.com,谷歌服务--
        - DOMAIN-SUFFIX,gridaware.app,谷歌服务--
        - DOMAIN-SUFFIX,gsrc.io,谷歌服务--
        - DOMAIN-SUFFIX,gstatic.cn,谷歌服务--
        - DOMAIN-SUFFIX,gstatic.com,谷歌服务--
        - DOMAIN-SUFFIX,gstaticcnapps.cn,谷歌服务--
        - DOMAIN-SUFFIX,gsuite.com,谷歌服务--
        - DOMAIN-SUFFIX,gv.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt0.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt1.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt2.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt3.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt5.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt6.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt7.com,谷歌服务--
        - DOMAIN-SUFFIX,gvt9.com,谷歌服务--
        - DOMAIN-SUFFIX,gwtproject.org,谷歌服务--
        - DOMAIN-SUFFIX,hdrplusdata.org,谷歌服务--
        - DOMAIN-SUFFIX,hey.gle,谷歌服务--
        - DOMAIN-SUFFIX,hindiweb.com,谷歌服务--
        - DOMAIN-SUFFIX,howtogetmo.co.uk,谷歌服务--
        - DOMAIN-SUFFIX,html5rocks.com,谷歌服务--
        - DOMAIN-SUFFIX,hwgo.com,谷歌服务--
        - DOMAIN-SUFFIX,iam.soy,谷歌服务--
        - DOMAIN-SUFFIX,iamremarkable.org,谷歌服务--
        - DOMAIN-SUFFIX,igoogle.com,谷歌服务--
        - DOMAIN-SUFFIX,impermium.com,谷歌服务--
        - DOMAIN-SUFFIX,itasoftware.com,谷歌服务--
        - DOMAIN-SUFFIX,j2objc.org,谷歌服务--
        - DOMAIN-SUFFIX,jibemobile.com,谷歌服务--
        - DOMAIN-SUFFIX,kaggle.com,谷歌服务--
        - DOMAIN-SUFFIX,kaggle.io,谷歌服务--
        - DOMAIN-SUFFIX,keyhole.com,谷歌服务--
        - DOMAIN-SUFFIX,keytransparency.com,谷歌服务--
        - DOMAIN-SUFFIX,keytransparency.foo,谷歌服务--
        - DOMAIN-SUFFIX,keytransparency.org,谷歌服务--
        - DOMAIN-SUFFIX,lanternal.com,谷歌服务--
        - DOMAIN-SUFFIX,like.com,谷歌服务--
        - DOMAIN-SUFFIX,madewithcode.com,谷歌服务--
        - DOMAIN-SUFFIX,material.io,谷歌服务--
        - DOMAIN-SUFFIX,mdialog.com,谷歌服务--
        - DOMAIN-SUFFIX,meet.new,谷歌服务--
        - DOMAIN-SUFFIX,mfg-inspector.com,谷歌服务--
        - DOMAIN-SUFFIX,mobileview.page,谷歌服务--
        - DOMAIN-SUFFIX,moodstocks.com,谷歌服务--
        - DOMAIN-SUFFIX,near.by,谷歌服务--
        - DOMAIN-SUFFIX,nest.com,谷歌服务--
        - DOMAIN-SUFFIX,neverware.com,谷歌服务--
        - DOMAIN-SUFFIX,nomulus.foo,谷歌服务--
        - DOMAIN-SUFFIX,oasisfeng.com,谷歌服务--
        - DOMAIN-SUFFIX,oauthz.com,谷歌服务--
        - DOMAIN-SUFFIX,ok.gle,谷歌服务--
        - DOMAIN-SUFFIX,on.here,谷歌服务--
        - DOMAIN-SUFFIX,on2.com,谷歌服务--
        - DOMAIN-SUFFIX,onefifteen.net,谷歌服务--
        - DOMAIN-SUFFIX,onefifteen.org,谷歌服务--
        - DOMAIN-SUFFIX,oneworldmanystories.com,谷歌服务--
        - DOMAIN-SUFFIX,openthread.io,谷歌服务--
        - DOMAIN-SUFFIX,openweave.io,谷歌服务--
        - DOMAIN-SUFFIX,orbitera.com,谷歌服务--
        - DOMAIN-SUFFIX,page.link,谷歌服务--
        - DOMAIN-SUFFIX,pagespeedmobilizer.com,谷歌服务--
        - DOMAIN-SUFFIX,pageview.mobi,谷歌服务--
        - DOMAIN-SUFFIX,panoramio.com,谷歌服务--
        - DOMAIN-SUFFIX,partylikeits1986.org,谷歌服务--
        - DOMAIN-SUFFIX,paxlicense.org,谷歌服务--
        - DOMAIN-SUFFIX,picasa.com,谷歌服务--
        - DOMAIN-SUFFIX,picasaweb.com,谷歌服务--
        - DOMAIN-SUFFIX,picasaweb.net,谷歌服务--
        - DOMAIN-SUFFIX,picasaweb.org,谷歌服务--
        - DOMAIN-SUFFIX,picnik.com,谷歌服务--
        - DOMAIN-SUFFIX,pittpatt.com,谷歌服务--
        - DOMAIN-SUFFIX,pixate.com,谷歌服务--
        - DOMAIN-SUFFIX,pki.goog,谷歌服务--
        - DOMAIN-SUFFIX,plus.codes,谷歌服务--
        - DOMAIN-SUFFIX,polymer-project.org,谷歌服务--
        - DOMAIN-SUFFIX,polymerproject.org,谷歌服务--
        - DOMAIN-SUFFIX,postini.com,谷歌服务--
        - DOMAIN-SUFFIX,privacysandbox.com,谷歌服务--
        - DOMAIN-SUFFIX,projectara.com,谷歌服务--
        - DOMAIN-SUFFIX,projectbaseline.com,谷歌服务--
        - DOMAIN-SUFFIX,publishproxy.com,谷歌服务--
        - DOMAIN-SUFFIX,questvisual.com,谷歌服务--
        - DOMAIN-SUFFIX,quickoffice.com,谷歌服务--
        - DOMAIN-SUFFIX,quiksee.com,谷歌服务--
        - DOMAIN-SUFFIX,recaptcha.net,谷歌服务--
        - DOMAIN-SUFFIX,redhotlabs.com,谷歌服务--
        - DOMAIN-SUFFIX,registry.google,谷歌服务--
        - DOMAIN-SUFFIX,revolv.com,谷歌服务--
        - DOMAIN-SUFFIX,ridepenguin.com,谷歌服务--
        - DOMAIN-SUFFIX,run.app,谷歌服务--
        - DOMAIN-SUFFIX,savethedate.foo,谷歌服务--
        - DOMAIN-SUFFIX,saynow.com,谷歌服务--
        - DOMAIN-SUFFIX,schema.org,谷歌服务--
        - DOMAIN-SUFFIX,schemer.com,谷歌服务--
        - DOMAIN-SUFFIX,screenwisetrends.com,谷歌服务--
        - DOMAIN-SUFFIX,screenwisetrendspanel.com,谷歌服务--
        - DOMAIN-SUFFIX,shattered.io,谷歌服务--
        - DOMAIN-SUFFIX,snapseed.com,谷歌服务--
        - DOMAIN-SUFFIX,solveforx.com,谷歌服务--
        - DOMAIN-SUFFIX,stadia.dev,谷歌服务--
        - DOMAIN-SUFFIX,stcroixmosquito.com,谷歌服务--
        - DOMAIN-SUFFIX,stcroixmosquitoproject.com,谷歌服务--
        - DOMAIN-SUFFIX,studywatchbyverily.com,谷歌服务--
        - DOMAIN-SUFFIX,studywatchbyverily.org,谷歌服务--
        - DOMAIN-SUFFIX,stxmosquito.com,谷歌服务--
        - DOMAIN-SUFFIX,stxmosquitoproject.com,谷歌服务--
        - DOMAIN-SUFFIX,stxmosquitoproject.net,谷歌服务--
        - DOMAIN-SUFFIX,stxmosquitoproject.org,谷歌服务--
        - DOMAIN-SUFFIX,synergyse.com,谷歌服务--
        - DOMAIN-SUFFIX,teachparentstech.org,谷歌服务--
        - DOMAIN-SUFFIX,telephony.goog,谷歌服务--
        - DOMAIN-SUFFIX,tensorflow.org,谷歌服务--
        - DOMAIN-SUFFIX,tfhub.dev,谷歌服务--
        - DOMAIN-SUFFIX,thecleversense.com,谷歌服务--
        - DOMAIN-SUFFIX,thegooglestore.com,谷歌服务--
        - DOMAIN-SUFFIX,thinkquarterly.co.uk,谷歌服务--
        - DOMAIN-SUFFIX,thinkquarterly.com,谷歌服务--
        - DOMAIN-SUFFIX,thinkwithgoogle.com,谷歌服务--
        - DOMAIN-SUFFIX,tiltbrush.com,谷歌服务--
        - DOMAIN-SUFFIX,txcloud.net,谷歌服务--
        - DOMAIN-SUFFIX,txvia.com,谷歌服务--
        - DOMAIN-SUFFIX,unfiltered.news,谷歌服务--
        - DOMAIN-SUFFIX,urchin.com,谷歌服务--
        - DOMAIN-SUFFIX,useplannr.com,谷歌服务--
        - DOMAIN-SUFFIX,usvimosquito.com,谷歌服务--
        - DOMAIN-SUFFIX,usvimosquitoproject.com,谷歌服务--
        - DOMAIN-SUFFIX,v8.dev,谷歌服务--
        - DOMAIN-SUFFIX,v8project.org,谷歌服务--
        - DOMAIN-SUFFIX,velostrata.com,谷歌服务--
        - DOMAIN-SUFFIX,verily.com,谷歌服务--
        - DOMAIN-SUFFIX,verilylifesciences.com,谷歌服务--
        - DOMAIN-SUFFIX,verilystudyhub.com,谷歌服务--
        - DOMAIN-SUFFIX,verilystudywatch.com,谷歌服务--
        - DOMAIN-SUFFIX,verilystudywatch.org,谷歌服务--
        - DOMAIN-SUFFIX,wallet.com,谷歌服务--
        - DOMAIN-SUFFIX,waveprotocol.org,谷歌服务--
        - DOMAIN-SUFFIX,waymo.com,谷歌服务--
        - DOMAIN-SUFFIX,waze.com,谷歌服务--
        - DOMAIN-SUFFIX,web.app,谷歌服务--
        - DOMAIN-SUFFIX,web.dev,谷歌服务--
        - DOMAIN-SUFFIX,webappfieldguide.com,谷歌服务--
        - DOMAIN-SUFFIX,webmproject.org,谷歌服务--
        - DOMAIN-SUFFIX,webpkgcache.com,谷歌服务--
        - DOMAIN-SUFFIX,webrtc.org,谷歌服务--
        - DOMAIN-SUFFIX,weltweitwachsen.de,谷歌服务--
        - DOMAIN-SUFFIX,whatbrowser.org,谷歌服务--
        - DOMAIN-SUFFIX,widevine.com,谷歌服务--
        - DOMAIN-SUFFIX,withgoogle.com,谷歌服务--
        - DOMAIN-SUFFIX,womenwill.com,谷歌服务--
        - DOMAIN-SUFFIX,womenwill.com.br,谷歌服务--
        - DOMAIN-SUFFIX,womenwill.id,谷歌服务--
        - DOMAIN-SUFFIX,womenwill.in,谷歌服务--
        - DOMAIN-SUFFIX,womenwill.mx,谷歌服务--
        - DOMAIN-SUFFIX,x.company,谷歌服务--
        - DOMAIN-SUFFIX,x.team,谷歌服务--
        - DOMAIN-SUFFIX,xn--9kr7l.com,谷歌服务--
        - DOMAIN-SUFFIX,xn--9trs65b.com,谷歌服务--
        - DOMAIN-SUFFIX,xn--flw351e.com,谷歌服务--
        - DOMAIN-SUFFIX,xn--ggle-55da.com,谷歌服务--
        - DOMAIN-SUFFIX,xn--gogl-0nd52e.com,谷歌服务--
        - DOMAIN-SUFFIX,xn--gogl-1nd42e.com,谷歌服务--
        - DOMAIN-SUFFIX,xn--ngstr-lra8j.com,谷歌服务--
        - DOMAIN-SUFFIX,xn--p8j9a0d9c9a.xn--q9jyb4c,谷歌服务--
        - DOMAIN-SUFFIX,xplr.co,谷歌服务--
        - DOMAIN-SUFFIX,youtu.be,谷歌服务--
        - DOMAIN-SUFFIX,yt.be,谷歌服务--
        - DOMAIN-SUFFIX,ytimg.com,谷歌服务--
        - DOMAIN-SUFFIX,zukunftswerkstatt.de,谷歌服务--
        - DOMAIN-SUFFIX,zynamics.com,谷歌服务--
        - DOMAIN-KEYWORD,appspot,谷歌服务--
        - DOMAIN-KEYWORD,blogspot,谷歌服务--
        - DOMAIN-KEYWORD,gmail,谷歌服务--
        - DOMAIN-KEYWORD,gstatic,谷歌服务--
        - DOMAIN-KEYWORD,recaptcha,谷歌服务--
        - IP-CIDR,172.110.32.0/21,谷歌服务--,no-resolve
        - IP-CIDR,173.194.0.0/16,谷歌服务--,no-resolve
        - IP-CIDR,216.73.80.0/20,谷歌服务--,no-resolve
        - IP-CIDR,74.125.0.0/16,谷歌服务--,no-resolve

        - MATCH,漏网之鱼 🐟 🐠 🎣 🐡 🦈 🐙

      prepend-proxy-groups:
        - name: 论文数据库--
          type: select
          proxies:
            - DIRECT
            - SELECT
            - relay

        - name: AI平台--
          type: select
          proxies:
            - relay
            - DIRECT
            - SELECT

        - name: 谷歌服务--
          type: select
          proxies:
            - relay
            - DIRECT
            - SELECT
            
        - name: 漏网之鱼 🐟 🐠 🎣 🐡 🦈 🐙
          type: select
          proxies:
            - DIRECT
            - SELECT
            - relay

        - name: 静态住宅前置代理
          type: select
          proxies:
            - SELECT
            - DIRECT

        - name: 静态住宅代理
          type: select
          proxies:
            - 美国-静态住宅
            - DIRECT

        - name: relay
          type: relay
          proxies:
            - 静态住宅前置代理
            - 静态住宅代理

      prepend-proxies:
        - name: 美国-静态住宅
          type: socks5
          server: ***********
          port: ****
          username: ****************
          password: *******************
  # 魔戒
  - url: ******** （此处粘贴刚刚复制的 url）
    yaml:
      prepend-proxy-groups:
        - name: SELECT
          type: select
          proxies:
            - 节点选择
```

> **说明**：规则可以按需增添，以上规则只是笔者个人所需。纯净节点（*号内容）需自备，URL 为刚刚复制的内容。保存后更新该配置，正常能够在代理中看到多出了 `纯净节点前置代理`、`纯净节点`、`relay` 三个分组。

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
