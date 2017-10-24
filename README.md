# cordova-plugin-imlib-android

融云 IMLib 安卓cordova 插件

# 准备

访问[融云官网](https://rongcloud.cn)网站，注册，新建应用，记住你的key

# 安装

1.`cordova plugin add https://github.com/ZhichengChen/cordova-plugin-imlib-android`


2.打开`platforms/android/build.gradle`，添加如下内容

    dependencies {
        compile(name: 'HMS-SDK-2.4.0.300', ext: 'aar')
    }

    repositories { flatDir { dirs 'aars' } }

3.融云 Cordova 服务器例子 https://github.com/ZhichengChen/rongcloud-cordova-server-demo 配合获得token

目前仅测试通过安卓平台

官方文档 http://www.rongcloud.cn/docs/cordova.html
