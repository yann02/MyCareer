# 自定义Apk名称和生成路径
## Sample
```groove
android {
    //...
    defaultConfig {
        applicationId "com.yann02.sample"
        versionCode 10001
        versionName "V1.0.1"
        //...
    }
    //...
    android.applicationVariants.all { variant ->
        def createTime = new Date().format("YYYY-MM-dd_HH.mm")
        if (variant.buildType.name == "release") {
            //  将release版本放到项目的apks文件夹下，其它编译类型使用默认生成路径即可
            variant.getPackageApplication().outputDirectory = new File(project.rootDir.absolutePath + "/apks/${variant.buildType.name}/${createTime}")
        }
        variant.outputs.all {
            if (variant.buildType.name == "release") {
                outputFileName = "${defaultConfig.applicationId}_${variant.flavorName}_${variant.buildType.name}_${defaultConfig.versionName}_${defaultConfig.versionCode}_${createTime}.apk"
            }
        }
    }
    //...
}
```   

> 上面的样例设置了只对release编译类型的生成包做处理，包括常用的如何获取应用打包时生成Apk名字常用到的关键字段信息  
> 获取应用包名：`defaultConfig.applicationId`  
> 获取应用版本名称：有两种方式  
- `defaultConfig.versionName`
- `variant.versionName`
> 获取应用版本号：有两种方式
- `defaultConfig.versionCode`
- `variant.versionCode`
> 获取应用变体：有两种方式
- `variant.flavorName`
- `variant.productFlavors[0].name`  
> 获取编译类型：`variant.buildType.name`  
> 使用时间：可根据个人需要设置格式，我这里精确到了时分，不含秒  
- `new Date().format("YYYY-MM-dd_HH.mm")`  
  
        Noteworthy：我这里用到了自定义生成apk的路径，每个路径下只能生成一个apk包，打包时系统会替换掉旧的apk包。
        我这里用时间来生成路径，以保留历史安装包。可酌情使用，非必要。
