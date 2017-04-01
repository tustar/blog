---
layout: post
title: "Android开发总结与设计师交互"
date: 2014-07-16 16:41:01
description: ""
category:
summary: "与20多位设计师合作心得"
tags: [Android, UI, Design]
---

> [Google安卓设计指南英文版](http://developer.android.com/design/index.html)

> [Google安卓设计指南中文版](http://23.244.200.195/design/get-started/creative-vision.html)

#### 布局

+ [margin/padding/border知识](http://www.cnblogs.com/linjiqin/p/3556497.html)

+ [Google推荐布局间隔](http://developer.android.com/design/style/metrics-grids.html)

+ [Android布局](http://www.cnblogs.com/wisekingokok/archive/2011/08/23/2150452.html)

+ 布局完了之后，可以站在用户的角度看自己的设计

+ 页面元素，先加后减，突出想要突出的内容，弱化不想突出的内容或者砍掉

#### 专业术语

+ 参考资料

  [支持不同屏幕英文版](http://developer.android.com/guide/practices/screens_support.html)

  [支持不同屏幕中文版](http://peng4602.iteye.com/blog/1837474)

  [Android手机分辨率基础知识](http://blog.csdn.net/moruite/article/details/6028547)

+ Screen size(屏幕尺寸)
  实际的物理尺寸，也就是屏幕的对角线尺寸。
  为简单起见，Android把所有的实际此存分成四个普遍的组：小，正常，大，巨大

+ Screen density（屏幕密度）屏幕一个物理区域上像素点的总数，通常被称作dpi（每英寸的像素点数）。例如，一个低密度屏幕比正常密度和高密度屏幕在给定的物理屏幕区域上的像素点更少。为简单起见，Android把所有的实际此存分成四个普遍的组：小，正常，大，巨大。

+ Resolution（分辨率）

  一个屏幕的总的物理像素点。当为多屏幕提供支持时，应用程序不直接用像素工作；我们只应该关心应用程序运行设备的屏幕尺寸和密度，然后指定是哪个组的尺寸和哪个组的密度。

+ Density-independent pixel (dp)（逻辑密度单位）

  当你设计UI界面的时候你应该用虚拟的像素单位来表示布局的尺寸和位置。当屏幕密度是160dpi是这个逻辑密度单位等于一个物理像素，同时160dpi作为基线密度被系统认为是中等密度屏幕，当必要时系统在运行时显示的处理基于当前屏幕的实际密度的dp单位的任何缩放，dp单位和屏幕像素转换公式是px=dp*(dpi/160)。例如在一个240dpi的屏幕，1dp等于1.5像素，当你设计你应用程序ui时你应该总是用dp单位来处理不同的屏幕密度



#### 图标

+ 应用图标尺寸

  | 分辨率        | 尺寸 (单位：像素)          |
  | ------------ |:-------------:|
  | ldpi         | 36*36       |
  | mdpi         | 48*48       |
  | hdpi         | 72*72       |
  | xhdpi        | 96*96       |
  | xxhdpi       | 144*144     |
  | web          | 512*512     |

+ 设计技巧

  + [图标设计技巧英文版](http://developer.android.com/design/style/iconography.html)，中文版的可以到Google安卓设计指南中文版中查找

  + **若应用图标是圆角的，切记圆角部分是透明背景**

  + 存储图片时，建议采用RGB565编码，减少图片尺寸

 + 图片命名及格式

  + 未特殊说明，图片一律采用png格式

  + 命名规范

    + 按钮 _n(normal)正常, _p(pressed)按下, _d（disable）不可点击命名

      ```
        fresh_ic_tab_home_n.png
        fresh_ic_tab_home_p.png
        fresh_ic_navi_back_n.png
        fresh_ic_navi_back_p.png
        ```
    + 图标名字前缀

      | Asset Type     |Prefix          | Example           |
      | --------------- |:------------------:|:-----------------:|
      | Icons     |ic_      | ic_star.png   |
      | Launcher    |ic_launcher  | ic_launcher_calendar.png   |
      | Menu      |ic_menu    | ic_menu_archive.png   |
      | Status bar  |ic_stat_notify | ic_stat_notify_msg.png  |
      | Tab icons   |ic_tab     | ic_tab_recent.png   |
      | Dialog icons  |ic_dialog    | ic_dialog_info.png   |

#### 字体

+ [Android手机默认字体](http://developer.android.com/design/style/typography.html)

+ 第三方字体，宋体...

#### 文字

+ 书写格式 [Google推荐书写格式](http://developer.android.com/design/style/writing.html)

+ 大小

  + 12sp 14sp 18sp ...
  + [Google推荐尺寸](http://developer.android.com/design/style/typography.html)

#### 截图

+ 若图片为纯色，只需告诉开发者颜色参数

+ 若图片有重复部分，采用draw9patch加工图片
  [Draw9patch的使用](http://blog.csdn.net/zhufuing/article/details/8058241)


#### 补充

+ 多看看大公司的UI设计

+ 参考一些优秀网站的分享网站的UI设计

+ 设计师相互交流









