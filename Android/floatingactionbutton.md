## FloatingActionButton

一个类似Android版Google+浮动功能按钮的控件
实现以下效果：

![](http://img.blog.csdn.net/20160523215924541)

```
findViewById(R.id.remove_fab).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Snackbar.make(view,"FAB",Snackbar.LENGTH_LONG)
                        .setAction("cancel", new View.OnClickListener() {
                            @Override
                            public void onClick(View v) {
                                //这里的单击事件代表点击消除Action后的响应事件
                            }
                        })
                        .show();
 				}
        });
        
```
或者

```
findViewById(R.id.remove_fab).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
 		Snackbar.make(view,"Hello",Snackbar.LENGTH_SHORT).show();
            }
        });
        
```
###xml

```
 	<android.support.design.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true"
    tools:context="com.example.ztt.floatingactionbutton.MainActivity">
    
    <android.support.design.widget.FloatingActionButton
        android:id="@+id/remove_fab"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="bottom|end"
        android:layout_marginBottom="16dp"
        android:layout_marginEnd="16dp"
        android:layout_marginRight="16dp"
        android:src="@drawable/ic_add_white_24dp" />

</android.support.design.widget.CoordinatorLayout>


```

别忘了在gradle添加

```
compile 'com.android.support:design:22.2.1'

```