# 权限相关
## 授权系统悬浮窗
> 在Activity中调用以下代码
> 1.判断应用是否有悬浮窗权限  
  
```Kotlin
Settings.canDrawOverlays(baseContext)
```

  
> 2.如果用户还未授权，则跳转到授权悬浮窗的页面  

```Kotlin
startActivity(Intent(Settings.ACTION_MANAGE_OVERLAY_PERMISSION, Uri.parse("package:${baseContext.packageName}")))
```
