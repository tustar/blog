---
layout: post
title: "Android内存分析"
date: 2016-04-18 16:41:01
description: ""
category:
summary: "Android应用性能分析摘记"
tags: [Android, Memery]
---


### 说明

+ GC_FOR_MALLOC

  发生在堆被占满不能进行内存分配时，在分配新对象之前必须进行内存回收

+ GC_CONCURRENT

  发生在（可能是部分的）垃圾可够回收时，通常有很多对象可以回收

+ GC_EXTERNAL_ALLOC

  在Android3.0 (Honeycomb)以前，释放通过外部内存（externel memory, 通过JNI代码中malloc分配得到的内存）时产  生。Android3.0和更高版本中不再有这种类型的内存分配了。

+   GC_EXPLICIT

  显示调用System.gc产生的垃圾收集

+ GC_HPROF_DUMP_HEAP

  发生在创建HPROF文件时


### 实例分析

  08-07 17:45:40.373: D/dalvikvm(5783): GC_CONCURRENT freed 2349K, 65% free 3246K/9551K, external 4703K/5261K, paused 2ms+2ms, total 5ms


+ freed 2349K

    说明释放了多少内存.

+ 65% free 3246K/9551K

    65%表示目前可分配内存占比例，3426K表示当前活动对象所占内存，9551K表示堆大小

+ external 4703K/5261K

    indicates external memory allocation, how much external memory the app has allocated and the    soft limit of allocation.说明外部内存的分配，已经分配了多少以及能够分配的上限。

+ paused 2ms+2ms

    第一个时间值表示markrootset的时间，第二个时间值表示第二次mark的时间。如果触发原因不是GC_CONCURRENT，这一    行为单个时间值，表示垃圾收集的耗时时间。

+ total 5ms

    GC总耗时

### 命令行查看数据

+ adb shell
+ ps | grep xxx.xxx 获取pid
+ dumpsys meminfo <pid>

### 参考资料
+ [Android内存泄漏分析及调试](http://blog.csdn.net/gemmem/article/details/13017999)





