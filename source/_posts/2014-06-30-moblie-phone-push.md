---
layout: post
title: "手机端推送平台调研"
date: 2014-06-30 16:41:01
description: ""
category:
summary: "手机端推送调研记录"
tags: [Android, iOS, WindowsPhone, Push]
---

### 国内推送平台

#### 百度云推送
+ [百度云官网](http://developer.baidu.com/cloud/push)
+ 免费
+ 平台支持 Android, iOS
+ 评价

  云推送全面支持iOS、Android平台。百度云推送服务支持推送三种类型的消息：通知、透传消息及富媒体，支持单条最大4K的消息推送，其基础的消息推送服务永久免费。而且它支持向所有用户或根据标签分类向特定用户群体推送消息。开发者可自定义内容、后续行为、样式模板等。

  百度推送的送达率有很大的问题，并且后台统计提供的实在是太简陋，综合下来到达率甚至不到50%，而且完全没有技术客服，反馈一个问题通常需要等很久才有回复。

#### 极光推送
+ [极光官网](https://www.jpush.cn/)
+ 量大收费
+ 平台支持 Android, iOS, Windows Phone
+ 评价

  极光推送支持iOS、Android两个平台，其SDK的嵌入比较容易，目前支持Portal上推送，也支持API调用。开发者可以推送自定义的消息内容。JPush SDK把内容完全转给开发者应用程序，由开发者应用程序去处理自定义消息。同时，极光推送能以图表的形式直观呈现推送效果，比如推送到达数、用户点击等。目前，去哪儿网、保卫萝卜、虾米网、中国电信等公司都采用了极光推送的服务。

  刚开始免费，量级较大就会收费，据说他们内部有优先级策略，免费的话消息延时的会非常厉害。

#### 个推推送
+ [个推官网](http://www.igetui.com/)
+ 量大收费
+ 平台支持 Android, iOS
+ 评价

  个推，中国最成功的SaaS服务商之一，为移动开发者提供推送服务，可以帮助开发者在应用推送功能上节省开发成本，并保证用户推送质量、节省用户流量，而且支持富文本。个推目前已经与新浪、百度、淘宝等互联网巨头合作，快捷酒店管家、唱吧、啪啪、应用汇等应用也引进了个推的推送服务。另外，个推还提供增量更新服务。应用接入个推SDK后，当开发者在个推后台提交新版本时，个推自动向用户推送一条信息，通知用户下载更新。而且用户下载新版本时，只下载差量部分，无需下载整个安装包。

  刚开始免费，量级较大就会收费，据说他们内部有优先级策略，免费的话消息延时的会非常厉害。

#### 小米推送
+ [小米官网](http://dev.xiaomi.com/)
+ 免费
+ 平台支持 Android, iOS
+ 评价

  小米的push做得优势很明显，和ios的有类似之处，关闭程序等于停掉进程，其他第三方推送都不能送达到。而小米推送走的系统级长连接，由心跳保证连接一直存在，所以只要用户联网，就送达得到。

  小米推送服务支持所有Android平台，在MIUI上属于系统服务框架，共享系统级长连接.


#### 友盟推送
+ [友盟官网](http://www.umeng.com/push)
+ 免费
+ 平台支持 Android, iOS
+ 评价

  很多朋友用过反馈效果很一般

#### 聚能推
+ [聚能推官网](http://itjuzi.com/)
+ 平台支持 Android, iOS
+ 评价

  今年6月，聚能推上线单机企业版，将推送技术打包独立给开发者。聚能推面向iOS、Android平台，支持群推、在线推、离线推等多种推送方式。同时，开发者在使用聚能推的推送服务时，可以对每一个应用自定义多达128个标签。根据标签开发者可以更加精准地将信息推送到用户的手机中。企业级用户的所有数据均存储在客户自己的服务器，免除了数据存储在第三方服务商而产生的数据泄漏问题。

#### 华为Push
+ [华为Push官网](http://developer.huawei.com/wiki/index.php?title=Push%E4%B8%9A%E5%8A%A1%E4%BB%8B%E7%BB%8D)
+ 免费
+ 平台支持 Android, iOS
+ 评价

  华为Push除了支持通知栏消息、富媒体消息，还支持透传消息，以透传方式将自定义的内容发送给应用。开发者的应用自主解析自定义的内容，并触发相关动作。利用此功能让开发者可实现IP呼叫、好友邀请等功能，完全自由发挥。

  另外，华为Push可根据地理位置触发推送消息。开发者在地图上划定区域，消息会自动推送到进去该区域的用户手机上。


#### 腾讯信鸽
+ [信鸽官网](http://xg.qq.com/)
+ 免费
+ 平台支持 Android, iOS
+ 评价

  有朋友觉得比较小众

#### 其他推送
+ [盛大云推送](http://www.grandcloud.cn/product/push)
+ 应用中自己实现推送功能（内涵段子，今日头条）

---

### 国外推送平台

#### Urban Airship
+ [Urban Airship官网](http://urbanairship.com/)
+ 平台支持 Android, iOS
+ 评价

  Urban Airship底层用的是APNs，restful style api/JSON封装数据，对开发者比较友好。开发者每月有100万条的免费额度，不过在100万条的额度用完后，你会发现，相对于其竞争对手Parse来说，Urban Airship的价格稍贵。Parse为0.07美元/千条，而Urban Airship是0.001美元/条。

#### Appoxee
+ [Appoxee](http://www.appoxee.com/)
+ 平台支持 Android, iOS
+ 评价

  Appoxee的一系列工具可以利用Push信息，唤醒用户、交叉推广其他应用。Appoxee创新的推送通知管理功能可帮助开发者自动调度并根据特殊参数推送通知，如推送富文本信息，或根据用户的时区推送通知等。

  Appoxee采用阶段性定价，用户量在25万以内普通客户可以免费使用，Silver级别客户在可以享受数据分析、标签API等更多功能的同时，需要每月缴纳500美元。如果开发者需要更精细的推送服务、后台管理与数据分析服务，还可议价。

#### 亚马逊推送
+ [亚马逊推送官网](http://aws.amazon.com/cn/sns/)
+ 量大收费
+ 平台支持 Android, iOS
+ 评价

  8月14日，Amazon宣布推出移动设备消息推送服务“Amazon SNS Mobile Push”。Amazon曾在2010年推出消息推送服务，但仅局限于通过SMS或邮件通知收件人。现在该业务已经支持iOS、Android、Kindle Fire等移动平台。

  开发者每个月使用Amazon的推送服务推送的前100万次信息是免费的，之后以“百万次”为单位进行收费，根据通知方式不同，收费为0.06至2.00美元间不等。


#### push.io
+ [push.io官网](http://push.io/)
+ 平台支持 Android, iOS

#### GCM（Google Cloud Messaging）
+ [GCM官网](http://developer.android.com/google/gcm/index.html)
+ 平台支持 Android
+ 评价

  谷歌原生推送。

#### Pubnub
+ [Pubnub官网](http://www.pubnub.com/)

#### Pusher
+ [Pusher官网](http://pusher.com/)

### 参考资料链接
+ [Android 哪个推送平台比较靠谱？](http://www.v2ex.com/t/107861)
+ [你将选哪个：云推送？极光推送？](http://www.tuicool.com/articles/z6vi2q)
+ [留住你的用户：8款第三方移动推送服务](http://www.csdn.net/article/2013-09-10/2816885-8-push-service-for-mobile-developers)
+ [推送服务](http://baike.baidu.com/link?url=YCU5eZ4MZNoGhVVRMWeDJ8ewhVYNtkPozp2gGXaxmtddQQnrBfX5-O5ayxglbyRHhpAbWWYIJeS4r2ODxnkFw_)



