---
layout: post
title: "Android开发总结编码规范与注意事项"
date: 2014-06-24 16:41:01
description: ""
category:
summary: "Android编程风格指南"
tags: [Android, Coding, Style]
---

### 资源文件

1. res/资源文件名

    + 项目名缩写\_(不用于第三方集成，可缺省)组件名称\_模块名称(模块简单，可缺省).xml
    + fresh_activity(item，dialog)_splash.xml

    ```
      // fresh 项目名称简写,若不提供给其他项目使用，项目名称可省略
      anim
        fresh_alpha_in.xml
        fresh_alpha_in.xml
        ...

      // n为normal的简写， p为pressed的简写， d为disable的简写
      drawable
        fresh_shape_btn_n.xml
        fresh_shape_btn_p.xml
        fresh_shape_btn_d.xml
        fresh_selector_btn.xml
        fresh_selector_tab_home.xml
        fresh_selector_navi_back.xml

        // 图片命名
        fresh_ic_tab_home_n.png
        fresh_ic_tab_home_p.png
        fresh_ic_navi_back_n.png
        fresh_ic_navi_back_p.png
        ...

        图片命名参考图片命名链接

      layout

        fresh_activity_spalsh.xml
        fresh_fragment_article_detail.xml
        fresh_item_product_list.xml
        fresh_item_product_grid.xml
        fresh_navi_bar.xml
        fresh_item_tab.xml
        ...

      values

        fresh_strings.xml
        fresh_ids.xml
        fresh_bool.xml
        fresh_public.xml
        ...
    ```

    [图片命名参考](http://developer.android.com/design/style/iconography.html)

2. ID名称

    + 模块名称\_组件名称
    + splash_imageview_logo
    + ID名称尽量不要相同，重构时，会导致改一个名称，导致很多资源文件的ID同时发生改变

    layout:fresh_activity_setting.xml
    ```
    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@color/fresh_color_bg" >

        <include
            android:id="@+id/setting_navi_bar"
            layout="@layout/fresh_navibar" />

        <ImageView
            android:id="@+id/setting_icon"
            android:layout_width="80dp"
            android:layout_height="80dp"
            android:layout_below="@+id/includeTitle"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="15dp"
            android:contentDescription="@string/fresh_app_name"
            android:src="@drawable/fresh_ic_launcher" />
    </RelativeLayout>
    ```

    values:fresh_strings.xml
    ```
   <resources>

    <!-- 应用名称 -->
    <string name="fresh_app_name">Fresh</string>

    <!-- 常用 -->
    <string name="fresh_ok">确定</string>/Users/Tu/Dropbox/GitHub/Study/Android开发总结(二) 与设计师交互.md
    <string name="fresh_cancel">取消</string>
    <string name="fresh_send">发送</string>
   </resources>
  ```

3. 公用布局部分的layout单独写成一个布局文件
```
    fresh_navibar.xml

    // 使用include的方式调用
    <include
        android:id="@+id/setting_navi_bar"
        layout="@layout/fresh_navibar" />
```

4. 一些布局文件若不需要马上显示的，可以采用ViewStub来延迟加载
  一些布局文件可以用merge来减少父布局，提升UI加载刷新速度

5. 应用图标尺寸
  | 分辨率        | 尺寸 (单位：像素)          |
  | ------------ |:-------------:|
  | ldpi         | 36*36       |
  | mdpi         | 48*48       |
  | hdpi         | 72*72       |
  | xhdpi        | 96*96       |
  | xxhdpi       | 144*144     |
  | web          | 512*512     |

6. 屏幕分辨率适配，目前Android Studio的预览效果非常不错
    [友盟指数](http://www.umindex.com/)

7. **修改布局文件layout和values时，需要改全不同分辨率和语言版本，我曾经犯过很多次这样的错误**

### 类文件

[Google Java Style](https://google-styleguide.googlecode.com/svn/trunk/javaguide.html)

[谷歌Java编码规范中文版](http://hawstein.com/posts/google-java-style.html)

+ 命名规范

  + 类名采用驼峰命名法
    + 变量名，不要用匈牙利命名法，采用首字符小写的驼峰命名法
  + 方法名，要能够说明此方法的用途


+ 数组中，若索引是有特殊含义，建议使用常量

    ```
    public static final int INDEX_ID = 0;
    public static final int INDEX_NAME = 1;

    String[] person = new String[]();
    ...
    String name = person[INDEX_NAME];
    // 对比
    String name = person[1];

    ```
+ Model属性适当的加入注释

    ```
    public class Tactic {

        private static final long serialVersionUID = 1L;
        private int id;
        private String action;
        private String value;
        private int notice_type;
        private boolean isReaded = false;
        private Integer[] advertisement_ids;

        ...
    }
    ```
    字段action是什么意思，由英文翻译过来为动作，而真正的用途策略，并且不同的值代表不同策略，建议改成枚举类型（Enum）

    ```
    public class Order extends FreshObject {

        private int pay_type = PayType.HDFK.value;// 付款方式1：货到付款2：已汇款
        private float total;// 订单总金额

        ...
    }
    ```

+ **适当加入空行，增加代码的可阅读性**

+ 一些常用的常量，可以集中定义到一个Interface中

    ```
    public interface CommonDefine {

        public static final int MIN_EXPAND_COUNT = 3;
        public static final int PER_PAGE = 10;
    }
    ```
+ **编完代码后，格式化代码**

    ```
    Eclipse: Shift+Command+F （MAC OS）
    Android Studio: Option+Command+L(MAC OS)
    ```

+ 谨慎使用三元运算符(?:)嵌套 , 太多降低代码阅读性,建议拆分从if..else,建议尽量不要嵌套三元运算符

    ```
    @Override
    public int getCount() {
        return currentViewType == ViewType.LIST ? (products != null ? products
                .size() : 0)
                : (products != null ? (products.size() % 2 == 0 ? products
                        .size() / 2 : (products.size() / 2 + 1)) : 0);
    }
    ```
    这样的代码，可阅读性非常差。

    ```
    @Override
    public int getCount() {

        if (currentViewType == ViewType.LIST) {
            return products != null ? products
                    .size() : 0;
        } else {
            if (products != null) {
                return products.size() % 2 == 0 ? products
                        .size() / 2 : (products.size() / 2 + 1);
            } else {
                return 0;
            }
        }
    }
    ```
    可阅读性强

+ startActivityForResult所需的RequestCode统一管理

    ```
    public interface RequestCode {

        public static final int TopicCreateActivity = 0x00002;
    }
    ```

+ Intent的action,putExtra的key统一管理

  ```
  public interface IntentExtra {

    // 自定义, com.xxx.xxx为项目包名
    public static final String TAG = "com.xxx.xxx.intent.extra.TAG";
    // Android系统的
    public static final String EXTRA_TEXT = "android.intent.extra.TEXT";

    ...
  }
  ```

  ```
    public interface IntentAction {

      // 自定义, com.xxx.xxx为项目包名
        public static final String MAIN = "com.xxx.xxx.intent.action.MAIN";
        // Android系统的
        public static final String ACTION_MAIN = "android.intent.action.MAIN";
    }
    ```
+ SharedPreferences的Key统一管理

  ```
  public interface PrefKey {

    public static final String PRODUCT = "product";
    ...
  }

  ```

+ **Log输出**

  ```
public class WelcomeActivity {

  private static final String TAG = WelcomeActivity.class.getSimpleName(); // 建议

  // private static final String TAG = “WelcomeActivity”; //
  // 不建议，一旦重命名类名，类名不会自动改变，一不注意会影响后期调试

  @Override
  public void onCreate(Bundle savedInstanceState) {

    Log.i(TAG, "onCreate :: savedInstanceState = " + savedInstanceState);
    // 因为是信息级别，所以比较喜欢用Log.i, 输出内容是参照C#中Log输出编写，具体格式为:方法名 + “ :: ”(::左右有空格) +
    // 变量名 + “ = ”(左右有空格) + 变量
    super.onCreate(savedInstanceState);
  }

  @Override
  protected void onResume() {

    Log.i(TAG, "onResume ::");
    super.onResume();
  }

  /**
   * Add shortcut to launcher (多写注释和描述方法，易于代码维护和阅读，具体格式可以参考Java的文档规范)
   */
  private void addShortcut() {

    Log.i(TAG, "addShortcut ::");
    // 信息级别的输出,所以喜欢用Log.i

    Intent intent = new Intent(
        "com.android.launcher.action.INSTALL_SHORTCUT");
    intent.putExtra(Intent.EXTRA_SHORTCUT_NAME,
        getString(R.string.app_name));
    intent.putExtra("duplicate", false);
    ComponentName componentName = new ComponentName(getPackageName(),
        getPackageName() + "." + getLocalClassName());

    Log.d(TAG, "addShortcut :: componentName = " + componentName);
    // 调试级别的输出，所以用Log.d

    intent.putExtra(Intent.EXTRA_SHORTCUT_INTENT, new Intent(
        Intent.ACTION_MAIN).setComponent(componentName));
    ShortcutIconResource iconResource = Intent.ShortcutIconResource
        .fromContext(context, R.drawable.ic_launcher);
    intent.putExtra(Intent.EXTRA_SHORTCUT_ICON_RESOURCE, iconResource);
    sendBroadcast(intent);
  }

  /**
   * Judge have the shortcut on launcher or not
   * (多写注释和描述方法，易于代码维护和阅读，具体格式可以参考Java的文档规范)
   *
   * @return ...
   */
  private boolean hasShortcut() {

    Log.i(TAG, "hasShortcut ::");
    String url;
    if (Build.VERSION.SDK_INT < 8) {
      url = "content://com.android.launcher.settings/favorites?notify=true";
    } else {
      url = "content://com.android.launcher2.settings/favorites?notify=true";
    }

    Cursor cursor = null;
    try {
      ContentResolver resolver = getContentResolver();
      cursor = resolver.query(Uri.parse(url), new String[] { "title" },
          "title=?", new String[] { getString(R.string.app_name) },
          null);
      if (cursor != null && cursor.getCount() > 0) {
        cursor.close();
        return true;
      }
    } catch (Exception e) {
      Log.e(TAG, "hasShortcut :: Exception => Error: " + e.getMessage());
      // 错误级别的输出，所以用Log.e
      e.printStackTrace();
      // 输出错误栈堆里的信息，方便调试
    } finally {
      if (cursor != null && !cursor.isClosed()) {
        cursor.close();
      }
    }

    return false;
  }

  /**
   * Get the section tags like 'Hot tag' or 'search history'
   * (多写注释和描述方法，易于代码维护和阅读，具体格式可以参考Java的文档规范)
   *
   * @param groups
   * @return
   */
  private List<String> getGroups(String[] groups) {

    Log.i(TAG, "getGroups :: groups = " + groups);
    // 信息级别的输出,所以用Log.i

    if (groups == null || groups.isEmpty()) {
      Log.w(TAG, "getGroups :: groups is null or empty");
      // 警告级别的输出,所以用Log.w
    }
    // 参数检查，有助于减少出错和提升性能

    List<String> list = new ArrayList<String>();
    for (String string : groups) {
      list.add(string);
    }
    return list;
  }
  /*
   * 这里的代码是多余的，应该改为用List<String> list = Arrays.asList(groups);若系统帮助类提供某些方法,
   * 我们就没必要花时间去写一些重复的东西，这是自己以前的老代码，贴出了是为了提醒自己。
   */

  // 至于verbose、assert怎么用，用得比较少，欢迎大家共同探讨。后期会从网上收集补全这方面的内容。

  }
  ```
+ **多用系统自带的工具类和第三方工具类，没必要自己去重复造轮子**

  ```
    TextUtils
    URLEncodedUtils
    URIUtils
    Utils
    DateUtils
    DatabaseUtils
    Time
    Arrays
    Collections
    ...

  ```
  [更多原生工具类](http://developer.android.com/reference/android/database/DatabaseUtils.html#q=utils)

  [第三方优秀工具类](http://www.trinea.cn/android/android-common-utils/)


 + **多关注一些第三方开源库，可以从中学习到如何编写框架，使用别人写好的框架，减少开发工作。**

  [Android优秀的开源库](http://www.trinea.cn/android/android-open-source-projects-dev-lib/)







