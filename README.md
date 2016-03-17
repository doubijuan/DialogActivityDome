# Android中使用Dialog风格弹出框的Activity
在Android中经常会遇到需要使用Dialog风格弹出框的activity，首先我们可能会首先想到的是在XML布局文件中设置android:layout_height="wrap_content"属性，让activity的高度自适应，显然这还不行，我们还需要为其DialogActivity设置自定义一个样式

```Java
<style name="dialogstyle">  
        <!--设置dialog的背景-->  
        <item name="android:windowBackground">@android:color/transparent</item>  
        <!--设置Dialog的windowFrame框为无-->  
        <item name="android:windowFrame">@null</item>  
        <!--设置无标题-->  
        <item name="android:windowNoTitle">true</item>  
        <!--是否浮现在activity之上-->  
        <item name="android:windowIsFloating">true</item>  
        <!--是否半透明-->  
        <item name="android:windowIsTranslucent">true</item>  
        <!--设置窗口内容不覆盖-->  
        <item name="android:windowContentOverlay">@null</item>  
        <!--设置动画，在这里使用让它继承系统的Animation.Dialog-->  
        <item name="android:windowAnimationStyle">@android:style/Animation.Dialog</item>  
        <!--背景是否模糊显示-->  
        <item name="android:backgroundDimEnabled">true</item>  
    </style>  
```

然后在AndroidManifest.xml中设置DialogActivity的样式为我们自定义的dialogstyle
![](http://img.blog.csdn.net/20151206163010559?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

如下是布局的代码
```Java
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="@color/white"
    android:orientation="vertical">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="65dp"
        android:orientation="horizontal"
        android:paddingLeft="@dimen/acitvity_margin"
        android:paddingRight="@dimen/acitvity_margin">

        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:orientation="horizontal">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="match_parent"
                android:gravity="center"
                android:text="上班时间:"
                android:textColor="@color/grey"
                android:textSize="@dimen/size_text_medium" />

            <Button
                android:id="@+id/tv_signin_time"
                android:layout_width="wrap_content"
                android:layout_height="match_parent"
                android:background="@color/white"
                android:gravity="center"
                android:text="9:00"
                android:textColor="@color/grey"
                android:textSize="@dimen/size_text_medium" />
        </LinearLayout>

        <LinearLayout
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:orientation="horizontal">

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="match_parent"
                android:gravity="center"
                android:text="下班时间:"
                android:textColor="@color/grey"
                android:textSize="@dimen/size_text_medium" />

            <Button
                android:id="@+id/tv_signout_time"
                android:layout_width="wrap_content"
                android:layout_height="match_parent"
                android:background="@color/white"
                android:gravity="center"
                android:text="18:00"
                android:textColor="@color/grey"
                android:textSize="@dimen/size_text_medium" />
        </LinearLayout>
    </LinearLayout>

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="65dp"
        android:paddingLeft="@dimen/acitvity_margin"
        android:paddingRight="@dimen/acitvity_margin">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:layout_alignParentLeft="true"
            android:gravity="center"
            android:text="公司位置:"
            android:textColor="@color/grey"
            android:textSize="@dimen/size_text_medium" />

        <EditText
            android:id="@+id/et_address"
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:layout_marginLeft="2dp"
            android:layout_toRightOf="@+id/tv_address"
            android:background="@color/white"
            android:hint="请输入公司位置"
            android:singleLine="true"
            android:textSize="@dimen/size_text_small" />

        <TextView
            android:id="@+id/tv_location"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentRight="true"
            android:layout_centerInParent="true"
            android:gravity="center"
            android:padding="5dp"
            android:text="重新定位"
            android:textColor="@color/blue"
            android:textSize="@dimen/size_text_medium" />
    </RelativeLayout>

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="65dp"
        android:paddingLeft="@dimen/acitvity_margin"
        android:paddingRight="@dimen/acitvity_margin">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:layout_alignParentLeft="true"
            android:gravity="center"
            android:text="设置管理员:"
            android:textColor="@color/grey"
            android:textSize="@dimen/size_text_medium" />

        <ImageView
            android:layout_width="wrap_content"
            android:layout_height="match_parent"
            android:layout_alignParentRight="true"
            android:gravity="center"
            android:src="@mipmap/icon_toright" />
    </RelativeLayout>
</LinearLayout>
```
接下来我们再看一下效果图是不是我们想要的呢

![](http://img.blog.csdn.net/20151206163140794?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)
