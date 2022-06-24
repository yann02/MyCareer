# MyCareer
My learning record of Android development.

## 目录
* [Kotlin](#Kotlin)
* [UI](#UI)
* [How to write README](#How to write README)
---
  
## Kotlin
### Flow(StateFlow and SharedFlow)
#### Collect Flow
##### 关于在视图组件（wether activity or fragment）中收集Flow的注意事项
* 要在onCreate生命周期的回调方法中定义收集流  
> 如果在其他回调方法中定义的话可能会因为用户离开当前页面再返回时，导致重复定义流的收集。比如我们在Afragment的onViewCreated方法中定义了流的收集方法，当我们从AFragment跳转到BFragment,再从BFragment返回AFragment，这时，AFragment的onViewCreated方法会被再次被系统调用，导致重复执行了流的收集，这样，当流emit一条数据时，collect方法会收到两次数据（我这里是使用Navigation component在fragment直接导航，使用它从AFragment导航到BFragment时，AFragment的视图会被销毁,触发onDestroyView方法(**Navigation会缓存带有id标识的组件的状态**)，再从BFragment返回AFragment时，onCreateView方法会被调用（**恢复带有id标识组件的状态**））
* 使用repeatOnLifecycle API收集流，确保视图的生命周期安全，不会导致视图引用泄漏  
我这里引用一个[_安卓开发官网的用例_](https://developer.android.com/kotlin/flow/stateflow-and-sharedflow)：
```Kotlin
class LatestNewsActivity : AppCompatActivity() {
    private val latestNewsViewModel = // getViewModel()

    override fun onCreate(savedInstanceState: Bundle?) {
        ...
        // Start a coroutine in the lifecycle scope
        lifecycleScope.launch {
            // repeatOnLifecycle launches the block in a new coroutine every time the
            // lifecycle is in the STARTED state (or above) and cancels it when it's STOPPED.
            repeatOnLifecycle(Lifecycle.State.STARTED) {
                // Trigger the flow and start listening for values.
                // Note that this happens when lifecycle is STARTED and stops
                // collecting when the lifecycle is STOPPED
                latestNewsViewModel.uiState.collect { uiState ->
                    // New value received
                    when (uiState) {
                        is LatestNewsUiState.Success -> showFavoriteNews(uiState.news)
                        is LatestNewsUiState.Error -> showError(uiState.exception)
                    }
                }
            }
        }
    }
}
```
---  
## UI 
### 动画
#### Property Animation
* ValueAnimator
> 在监听动画的方法里修改对象属性，来达到动画的效果。  
* ObjectAnimator
> 继承自ValueAnimator，对对象的可set/get属性动画，用法更简单，不需要在监听器中更新对象属性。但是可以设置动画的监听器，监听动画完成等事件。监听动画完成，可以在动画完成后执行一些我们想要的操作。  

#### View Animation
> 有两大约束
* 只是修改视图的绘制，并不会修改视图的位置。尤其是只有点击初始位置才能接收到点击事件  
* 只能对View使用
---
### 图片选择器
#### 推荐使用的库
1. [__PictureSelector__](https://github.com/LuckSiege/PictureSelector)
---
### 字符串资源引用
* 省略号
> …
  
## How to write README
[官方文档]([How to write README.md](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#styling-text)  
> 有中文版
