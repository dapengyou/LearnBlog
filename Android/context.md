##Context

####Context相关类的继承关系
![](http://hi.csdn.net/attachment/201203/1/0_1330607569Vj4c.gif)

应用程序创建Context实例的情况有如下几种情况：

 1. 创建Application 对象时， 而且整个App共一个Application对象
 2. 创建Service对象时
 3. 创建Activity对象时
 
 ```
    因此应用程序App共有的Context数目公式为：
    
  	总Context实例个数 = Service个数 + 
    				   Activity个数 + 1（Application对应的Context实例）
    				   
```

#####创建Application对象的时机
 
每个应用程序在第一次启动时，都会首先创建Application对象。如果对应用程序启动一个Activity(startActivity)流程比较
清楚的话，创建Application的时机在创建handleBindApplication()方法中

#####创建Activity对象的时机
 
 通过startActivity()或startActivityForResult()请求启动一个Activity时，如果系统检测需要新建一个Activity对象时，就会
  回调handleLaunchActivity()方法，该方法继而调用performLaunchActivity()方法，去创建一个Activity实例，并且回调
 onCreate()，onStart()方法等
  
#####创建Service对象的时机
 
  通过startService或者bindService时，如果系统检测到需要新创建一个Service实例，就会回调handleCreateService()方法，完成相关数据操作


>三者函数都位于 ActivityThread.java类中

*通过对ContextImp的分析可知，其方法的大多数操作都是直接调用其属性mPackageInfo(该属性类
型为PackageInfo)的相关方法而来。这说明ContextImp是一种轻量级类，而PackageInfo才是真正重量级的类。而一个App里的
所有ContextIml实例，都对应同一个packageInfo对象。*
            

[参考链接](http://blog.csdn.net/qinjuning/article/details/7310620)