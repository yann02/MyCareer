# 权限相关
## 授权系统悬浮窗
> 在Activity中调用以下代码，跳转到授权悬浮窗的页面  

```Kotlin
startActivity(Intent(Settings.ACTION_MANAGE_OVERLAY_PERMISSION, Uri.parse("package:${baseContext.packageName}")))
```
