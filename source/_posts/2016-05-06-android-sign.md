---
layout: post
title: "安卓签名笔记"
date: 2016-05-06 16:41:01
description: ""
category:
summary: "打包应用签名及对齐压缩"
tags: [Android, jarsinger, zipalign]
---

### 安卓jarsigner和zipalign

#### jarsinger
在Terminal中输入

```
  jarsigner -verbose -keystore abc.keystore -signedjar signed.apk unsign.apk abc
```
接着输入密码

```
  abc
```
详情参照[jarsinger](http://docs.oracle.com/javase/6/docs/technotes/tools/windows/jarsigner.html)

输出一堆内容后可以看到已签名好的signed.apk

#### zipalign

在Terminal中输入

```
  zipalign -f -v 4 signed.apk zipsigned.apk
```
输出一堆内容后看到已经对齐好的zipsigned.apk

详情参照[zipalign](http://developer.android.com/tools/help/zipalign.html)

### 备注
必须是先jarsigner后zipalign
