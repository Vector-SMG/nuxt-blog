---
title: Android架构组件Lifecycle-Aware源码解析
description: Lifecycle-Aware，是google开发的用于生命周期感知的架构组件。
---

> 测试环境：
> 
* Android Studio:3.1.3
* Android SDK:27
* Android Lifecycle:1.0.0

## 简介
Lifecycle-Aware，是google开发的用于生命周期感知的架构组件。
<!--more-->
## 使用

### 如何使用Lifecycle-Aware组件？

#### 1. 引入库

```
implementation 'android.arch.lifecycle:extensions:1.0.0’
annotationProcessor 'android.arch.lifecycle:compiler:1.0.0’

```

#### 2. 创建自定义的生命周期观察者

```
public  class CustomLifecycleObserver implements LifecycleObserver {

	punlic CustomLifecycleObserver(......){
		......
	}
	
	 @OnLifecycleEvent(Lifecycle.Event.ON_CREATE)
	 public void excuteMethodOnCreate(){
	 	......
	 }
	
	@OnLifecycleEvent(Lifecycle.Event.ON_RESUME)
	 public void excuteMethodOnResume(){
	 	......
	 }	

}

```

#### 3.给activity添加生命周期观察者

```
public class LifecycleOwnerActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ......
      	 getLifecycle().addObserver(new CustomLifecycleObserver(...));
     }
}

```
通过上述简单的三个步骤，就能实现将和生命周期关联的逻辑隔离到单独的类中。关于这样做的好处，再举个例子，如果一个自定义view需要处理和生命周期相关的逻辑时，可以让view实现LifecycleObserver，并且给相应的方法添加上注解，通过步骤三的方式添加为观察者，就可以让view具有生命周期感知的能力。是不是很easy！！！


### 实际应用的例子

接下来，再举个实际的例子希望能加深你的理解，该例子，主要是通过定位服务获取坐标，onResume的时候，启动获取程序；onPause的时候，关闭获取程序。完整代码如下:（该例子来自[google](https://github.com/googlecodelabs/android-lifecycles)（稍微修改了下））

```
public class LifecycleOwnerActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ......
      	 bindLocationListener();
     }
} 
```
```
private void bindLocationListener() {
        BoundLocationManager.bindLocationListenerIn(this, mGpsListener, getApplicationContext());
}
```
```
public class BoundLocationManager {
    public static void bindLocationListenerIn(LifecycleOwner lifecycleOwner,
     LocationListener listener, Context context) {
        new BoundLocationListener(lifecycleOwner, listener, context);
    }
    static class BoundLocationListener implements LifecycleObserver {
        private final Context mContext;
        private LocationManager mLocationManager;
        private final LocationListener mListener;

        public BoundLocationListener(LifecycleOwner lifecycleOwner,
                                     LocationListener listener, Context context) {
            mContext = context;
            mListener = listener;
            lifecycleOwner.getLifecycle().addObserver(this);
        }

        @OnLifecycleEvent(Lifecycle.Event.ON_RESUME)
        void addLocationListener() {
            mLocationManager =
                    (LocationManager) mContext.getSystemService(Context.LOCATION_SERVICE);
            mLocationManager.requestLocationUpdates(LocationManager.GPS_PROVIDER, 0, 0, mListener);
            Log.d("BoundLocationMgr", "Listener added");

            // Force an update with the last location, if available.
            Location lastLocation = mLocationManager.getLastKnownLocation(
                    LocationManager.GPS_PROVIDER);
            if (lastLocation != null) {
                mListener.onLocationChanged(lastLocation);
            }
        }


        @OnLifecycleEvent(Lifecycle.Event.ON_PAUSE)
        void removeLocationListener() {
            if (mLocationManager == null) {
                return;
            }
            mLocationManager.removeUpdates(mListener);
            mLocationManager = null;
            Log.d("BoundLocationMgr", "Listener removed");
        }
    }
 }

```

## 解析
......




    