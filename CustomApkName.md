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
            variant.getPackageApplication().outputDirectory = new File(project.rootDir.absolutePath + "/apks/${variant.buildType.name}/${createTime}")[^1]
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
[^1]: 设置生成Apk的路径
