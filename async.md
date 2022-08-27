# Android中的异步
## 如何在非UI线程中调用Android UI toolkit (components from the android.widget and android.view packages)
### 新的实现
> 通过Kotlin协程处理异步操作，将处理结果赋值给可观察类型的数据（StateFlow、SharedFlow和livedata，[RxJava]）,然后在Activity or fragment组件的生命周期内监听这些数据，避免由于
> 数据模型和组件生命周期长短不一致导致的内存泄漏问题。

### 老的实现
> 可以通过以下的方式实现，要自己处理内存泄漏的问题。比如Handler可以在Activity的onstop生命周期回调函数内调用
> Handler的[removeCallbacksAndMessages](https://developer.android.com/reference/android/os/Handler#removeCallbacksAndMessages(java.lang.Object))方法
> 移除所有的回调和消息实体类。  
- Handler
- AsyncTask
  
> [安卓官方对应用进程和线程的说明](https://developer.android.com/guide/components/processes-and-threads#Processes)

