# Jetpack Compose
## Design
### 系统栏
> 系统栏包括以下两种类型  
  
- 顶部状态栏
- 底部导航栏

#### 将编写的内容填充到系统栏
`WindowCompat.setDecorFitsSystemWindows(window, false)`  
    
> 如下所示  

  
```Kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        WindowCompat.setDecorFitsSystemWindows(window, false)
    }
}
```

> 此时只是设置了系统栏可以填充我们编写的界面，但是系统栏的背景颜色依然显示，这样就会导致我们编写的内容被系统栏覆盖。

#### 设置状态栏样式
> 修改应用主题，如下所示：
  
```Xml
<style name="Theme.HandyDialogue" parent="Theme.Material3.DayNight">
    <item name="android:statusBarColor">@android:color/transparent</item>
    <item name="android:windowLightStatusBar">?attr/isLightTheme</item>
</style>
```

> 使用上面的主题需要依赖库   

  
`implementation "com.google.android.material:material:1.7.0-rc01"` 
  
> 设置以上主题可能会有错误提示（如果你的应用配置的最小版本低于Api23的话），根据提示修改即可。
> 此时我们顶部的内容会跟状态栏的状态信息重叠显示

#### 设置间距
- 顶部状态栏间距
> 当页面使用Scaffold并且添加了topBar时，不需要设置（视界面实际显示效果再做修改，不行可以通过Modifier.statusBarsPadding()来设置）

- 底部导航栏间距

> Modifier.navigationBarsPadding()  
  




### Text
#### 动态设置文本字体大小，以适配内容的显示
> 参考Stack Overflow的[回答](https://stackoverflow.com/questions/63971569/androidautosizetexttype-in-jetpack-compose)，快速使用可以查看【Brian】的回答，但是【Rahul Sainani】的回答感觉更标准一些。  
### Image
#### 加载网络图片
[stack overflow](https://stackoverflow.com/questions/58594262/how-do-i-load-url-into-image-into-drawimage-in-compose-ui-android-jetpack)
## Material Design
### 获取组件大小
#### TopAppBar默认高度
> 56dp

## Accompanist
> Utils for Jetpack Compose，对Jetpack Compose的扩展支持。  
  
- [教程](https://google.github.io/accompanist/)  
- [Github](https://github.com/google/accompanist)
