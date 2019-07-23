# ZKComponentDocument
ZK组件使用文档说明。

## 组件配置文件地址

[ZK_Version](http://zkteam.cc/android/gradle/versions_1.gradle) : http://zkteam.cc/android/gradle/versions_1.gradle



## 相关组件

- 事件总线：[ZKLiveEventBus](https://github.com/ZhuoKeTeam/ZKLiveEventBus) ---> [![](https://jitpack.io/v/ZhuoKeTeam/ZKLiveEventBus.svg)](https://jitpack.io/#ZhuoKeTeam/ZKLiveEventBus)
- 基础的 SDK 封装：[ZKSDK](https://github.com/ZhuoKeTeam/ZKSDK) ---> [![](https://jitpack.io/v/ZhuoKeTeam/ZKSDK.svg)](https://jitpack.io/#ZhuoKeTeam/ZKSDK)
- 基础的 UI 组件封装：[ZKUIComponents](https://github.com/ZhuoKeTeam/ZKUIComponents) ---> [![](https://jitpack.io/v/ZhuoKeTeam/ZKUIComponents.svg)](https://jitpack.io/#ZhuoKeTeam/ZKUIComponents)
- 广告 AD 封装：[ZKAD](https://github.com/ZhuoKeTeam/ZKAD) ---> [![](https://jitpack.io/v/ZhuoKeTeam/ZKAD.svg)](https://jitpack.io/#ZhuoKeTeam/ZKAD)
- 基础的图片请求 封装：[ZKImageLoader](https://github.com/ZhuoKeTeam/ZKImageLoader) ---> [![](https://jitpack.io/v/ZhuoKeTeam/ZKImageLoader.svg)](https://jitpack.io/#ZhuoKeTeam/ZKImageLoader)
- 基础的网络请求 封装：[ZKConnection](https://github.com/ZhuoKeTeam/ZKConnection) ---> [![](https://jitpack.io/v/ZhuoKeTeam/ZKConnection.svg)](https://jitpack.io/#ZhuoKeTeam/ZKConnection)


## 快速使用说明（一分钟超快搭建一个 APP）

1. 使用 zkteam.jar 快速生成 自建工程

在 zkteam.jar 当前目录执行：

```shell
java -jar zkteam.jar TestW com.test.w /Users/WangQing/Desktop/demo1
```

将会在 /Users/WangQing/Desktop/demo1 目录下生成 以 TestW 命名的文件夹项目，应用的包名是 com.test.w。直接构建项目，下载相关依赖即可运行 app。

项目中默认已经包含 ZKSDK 和 ZKUI。

2. ZKSDK 内置了 ZKBaseApplication，自己的 Application 可以直接继承 ZKBaseApplication，里面包含 MultiDex 和 ZKManager 的 init。



- 默认的 ZKSDK，会将 ZKBaseApplication 在 AndroidManifest.xml 设置为 Application 的结点，支持初始化等操作。

- 如果 app 需要 自定义 Application，继承 ZKBaseApplication ，在 xml 中 application 结点添加 tools:replace="android:name"即可。



  ```xml
      <application
              ...
              android:name=".ZKSDKApplication"
              tools:replace="android:name"
              ... >
      </application>
  ```

- AppTheme 不能加 ActionBar

```
    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
        ...
    </style>
```



3. ZKUI 包含启动页面，背景色每次启动都会换。也包含基础权限申请，可以继承 ZKSplashActivity 写自己的 Splash 启动页面，然后在 AndroidManifest.xml 设置如下，可以屏蔽原始的启动页面：

```xml
<activity android:name="com.zkteam.ui.components.activity.DefaultSplashActivity"
          tools:node="removeAll"/>
```

4. Activity 建议继承自 ZKSplashActivity， 默认包含侧边栏退出当前 Activity。

