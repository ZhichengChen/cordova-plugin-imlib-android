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

# 运行demo

1.`cordova create MyApp`

2.`cd MyApp`

3.`cordova platform add android`

4.`cordova plugin add https://github.com/ZhichengChen/cordova-plugin-imlib-android`

5.打开`platforms/android/build.gradle`添加如下内容

    dependencies {
        compile(name: 'HMS-SDK-2.4.0.300', ext: 'aar')
    }

    repositories { flatDir { dirs 'aars' } }
    
6.`cordova run android`

7.运行 `https://github.com/ZhichengChen/rongcloud-cordova-server-demo`，浏览器访问获得token

8.chrome 访问 `chrome://inspect` 选择设备

9.console 里输入

      var token = '';
      RongCloudLibPlugin.init({
          // appKey: "lmxuhwagx8tyd",
          // appKey: "z3v5yqkbv8v30",
          appKey: 'qd46yzrf4oowf'
          // deviceToken: "87jjfds8393sfjds83"
        },
        function(ret, err) {
          if (ret) {
            console.log('init:' + JSON.stringify(ret));
          }
          if (err) {
            console.log('init error:' + JSON.stringify(err));
          }
        }

      );

      RongCloudLibPlugin.setConnectionStatusListener(
        function(ret, err) {
          if (ret) {
            console.log('setConnectionStatusListener:' + JSON.stringify(ret));
             if(ret.result.connectionStatus == 'KICKED'){
                 alert('您的帐号已在其他端登录!');
             }
          }
          if (err) {
            console.log('setConnectionStatusListener error:' + JSON.stringify(err));
          }
        }
      );

      RongCloudLibPlugin.connect({
          token: token
        },
        function(ret, err) {
          if (ret) {
            console.log('connect:' + JSON.stringify(ret));
          }
          if (err) {
            console.log('init error:' + JSON.stringify(err));
          }
        }
      );

      RongCloudLibPlugin.setOnReceiveMessageListener(
        function(ret, err) {
          if (ret) {
            console.log('setOnReceiveMessageListener:' + JSON.stringify(ret));
            // alert('setOnReceiveMessageListener:' + JSON.stringify(ret));
          }
          if (err) {
            console.log('setOnReceiveMessageListener error:' + JSON.stringify(err));
          }
        }

      );
