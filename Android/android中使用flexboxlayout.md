#FlexboxLayout在Android中的使用


Google最近开源了一个关于布局的项目，FlexboxLayout，一款运用在Android而功能类似于CSS弹性框布局模块的布局

####安装
添加下面的依赖关系到你的build.gradle文件

```
dependencies {
    compile 'com.google.android:flexbox:0.1.3'
}

```
####用法
FlexboxLayout 像 LinearLayout 和 RelativeLayout一样继承ViewGroup，所以可以在xml中这样定义:

```
<?xml version="1.0" encoding="utf-8"?>
   <com.google.android.flexbox.FlexboxLayout 
   	xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/flexbox_layout"
    app:alignContent="center"
    app:alignItems="center"
    app:flexWrap="wrap">

    <TextView
        android:id="@+id/textview1"
        android:layout_width="80dp"
        android:layout_height="80dp"
        android:background="@android:color/holo_red_dark"
        android:text="1"
        android:textAlignment="center"
        />

    <TextView
        android:id="@+id/textview2"
        android:layout_width="80dp"
        android:layout_height="80dp"
        android:background="@android:color/holo_blue_dark"
        android:text="2"
        app:layout_alignSelf="center"
        />

    <TextView
        android:id="@+id/textview3"
        android:layout_width="160dp"
        android:layout_height="80dp"
        android:background="@android:color/holo_purple"
        android:text="3"
        app:layout_alignSelf="center" />
    <TextView
        android:id="@+id/textview4"
        android:layout_width="160dp"
        android:layout_height="80dp"
        android:background="@android:color/holo_purple"
        android:text="3"
        app:layout_alignSelf="center" />
	</com.google.android.flexbox.FlexboxLayout>
	
```
这个控件多出了几个属性，在顶部设置就可以了

```
app:flexWrap="wrap" // 子控件是否自动换行

app:alignItems="flex_start" // 子控件在其所在行/列中的对齐方式

app:alignContent="flex_start" //内容的对齐方式 从头对齐还是从尾对齐

app:flexDirection="column" //子控件排列方式，是列或行（可倒序排列）

app:justifyContent="flex_end" //子控件行列时的对齐方式，中间或两端

```

如此之外，这样写代码也可以：

```
FlexboxLayout flexboxLayout = (FlexboxLayout) findViewById(R.id.flexbox_layout);
flexboxLayout.setFlexDirection(FlexboxLayout.FLEX_DIRECTION_COLUMN);

View view = flexboxLayout.getChildAt(0);
FlexboxLayout.LayoutParams lp = (FlexboxLayout.LayoutParams) view.getLayoutParams();
lp.order = -1;
lp.flexGrow = 2;
view.setLayoutParams(lp);

```
>这里你可以根据自己项目的需求进行设置,下面是可以设置的属性

![](/Users/ztt/Desktop/屏幕快照 2016-05-23 19.08.00.png)


#### 具体支持的属性

1. flexDirection

子项目放置在Flexbox的布局内部，它确定主轴线（和横向轴线，垂直于主轴线）的方向。可能的值有：

   * row (default)
   * row_reverse
* column
* column_reverse

2.flexWrap

此属性控制柔性容器是否是单行或多行，和十字轴的方向。可能的值有

* nowrap (default)
* wrap
* wrap_reverse

3.justifyContent

此属性控制沿主轴线的取向。可能的值有

* flex_start (default)
* flex_end
* center
* space_between
* space_around

4.alignItems

此属性控制沿十字轴的对齐方式。可能的值有

* stretch (default)
* flex_start
* flex_end
* center
* baseline

5.alignContent

此属性控制在柔性容器中的弯曲线的对准。可能的值有

* stretch (default)
* flex_start
* flex_end
* center
* space_between
* space_around

6.layout_order

这个属性中“1”被设置为一个默认值。

7.layout_flexGrow

这个属性中“0”被设置为一个默认值。

8.layout_flexShrink

这个属性中“1”被设置为一个默认值。

9.layout_alignSelf

此属性确定（垂直于主轴线）沿着横轴的对齐。可能的值有：

* auto (default)
* flex_start
* flex_end
* center
* baseline
* stretch

10.layout_flexBasisPercent

 默认值是-1，这意味着未设置。

[GitHub上FlexboxLayout的示例](https://github.com/google/flexbox-layout)
