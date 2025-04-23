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

- 推荐 `Clash`
- 汉化版：[Clash 中文版](https://github.com/Z-Siqi/Clash-for-Windows_Chinese/releases) (一般下载 `Clash.for.Windows-0.20.39-Opt.1-win.7z` 即可)

2️⃣ **获取跳板节点**

- 纯净节点通常属于墙外网络，需要一个普通节点作为跳板
- 推荐：[魔戒](https://mojie.app/register?aff=6DpwXzur)（十分便宜，10元100G+流量）

3️⃣ **获取纯净节点**

- 推荐使用`海外静态住宅代理`服务; 可几人共用，但不可太多人滥用。
- 例如：[Proxy302](https://share.proxy302.com/KNlOWp)（每月 7.99 美元）

### 1.2 配置转发规则

4️⃣ **配置 Clash**

1. 点击配置 → 右键单击节点 → 点击设置 → 复制节点的 URL
2. 点击配置 → 右键单击节点 → 点击配置文件预处理 → 点击编辑解析器
3. 清空并粘贴以下内容：

```yaml
parsers:
- reg: http*
    yaml:
    prepend-rules:
        # 放通bing浏览器 
        - DOMAIN-KEYWORD,bing.com,DIRECT
        # 放通学术数据库
        - DOMAIN-KEYWORD,dl.acm.org,DIRECT
        - DOMAIN-KEYWORD,ieeexplore.ieee.org,DIRECT
        - DOMAIN-KEYWORD,springer.com,DIRECT
        # qwen 放通       
        - DOMAIN-KEYWORD,chat.qwenlm.ai,DIRECT
        # 部分内网放通
        - DOMAIN-KEYWORD,mermaid.ink,DIRECT
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

大多数平台需要国外信用卡，推荐使用信用卡代理平台：

- [Wildcard](https://bewildcard.com/i/RLEYJ1IK)
  - 优势：提供一键充值大模型服务（网络环境纯净的情况下十分可行）
  - 缺点：需要支付一次性开卡费和少量手续费


## 🔑 4. 大模型API获取与使用

> 待补充
