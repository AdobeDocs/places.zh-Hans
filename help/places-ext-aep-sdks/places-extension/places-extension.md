---
title: Places 扩展
description: Places扩展允许您根据用户的位置进行操作。
translation-type: tm+mt
source-git-commit: a7dddb78e1e00a0bde01ea668334932759a9dae8
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 5%

---


# Places 扩展 {#places-extension}

Places扩展允许您根据用户的位置进行操作。 此扩展是Places查询服务API的接口。 通过侦听包含GPS坐标和地理区域事件的事件，此扩展将派送由规则引擎处理的新事件。 Places扩展还检索并提供从API检索的应用程序数据的最近POI的列表。 API返回的区域存储在缓存和持久性中，这允许有限的脱机处理。

## 在Adobe Experience Platform Launch安装Places扩展

1. In Experience Platform Launch, click the **[!UICONTROL Extensions]** tab.
1. 在选项卡 **[!UICONTROL Catalog]** 上，找到该 **[!UICONTROL Places]** 扩展，然后单击 **[!UICONTROL Install]**。
1. 选择要在此属性中使用的Places库。 这些库将可在您的应用程序中访问。
1. 单击 **[!UICONTROL Save]**。

   单击时， **[!UICONTROL Save]** Experience PlatformSDK会在您选择的库中搜索Places Services中的POI。 在您构建应用程序时，库下载中不包括POI数据，但在运行时将基于位置的POI子集下载到最终用户的设备，并基于用户的GPS坐标。

1. 完成发布过程以更新SDK配置。

   有关在Experience Platform Launch中发布的更多信息，请参 [阅发布](https://docs.adobe.com/content/help/zh-Hans/launch/using/reference/publish/overview.html)。

### Configure the Places extension {#configure-places-extension}

![](//help/assets/places-extension.png)

## 将Places扩展添加到您的应用程序 {#add-places-to-app}

您可以将Places扩展添加到Android和iOS应用程序。 向iOS或Android应用程序添加Places的步骤如下所示。 Places扩展还可用于以下平台。 要在使用其中一个平台进行开发时向应用程序添加地点，请参阅随附的链接：

**[Cordova Places插件](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places插件](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Fullign Places插件](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Places插件](https://github.com/adobe/xamarin-acpcore)**


### Android

要使用Java将Places扩展添加到您的应用程序，请执行以下操作：

1. 使用应用程序的Gradle文件将Places扩展添加到您的项目。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. 在应用程序的主活动中导入Places扩展。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

要使用Objective-C或Swift将Places扩展添加到您的应用程序，请执行以下操作：

1. 将Places和Mobile Core [库添加](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) 到您的项目中。 您需要将以下窗格添加到您的 `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   或者，如果您不使用Cocoapods，则可以在Github上的发布页面手动包含Mobile Core和 [Places库](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) 。

1. 更新您的Cocoapod:

   ```objective-c
   pod update
   ```

1. 打开Xcode，在AppDelegate类中，导入核心和地点标题：

   **Objective-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### 使用移动核心注册Places扩展 {#register-places-mobile-core}

您需要在Android和iOS中用Mobile Core注册Places扩展。

#### Android

在您的应用程序方 `OnCreate` 法中注册Places扩展：

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

在您的应用程序方 `application:didFinishLaunchingWithOptions:` 法中，将Places扩展注册到您的其他SDK注册调用：

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### 修改地点会员资格停留时间 {#places-ttl}

位置数据可能会很快变得陈旧，尤其是当设备未收到后台位置更新时。

通过设置配置设置，控制设备上放置成员资格数据的 `places.membershipttl` 实时时间。 传入的值表示位置状态对设备保持有效的秒数。

#### Android

在更新配置的回 `MobileCore.start()` 调中，在调用配置之前使用必要的更改 `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

在方法回调的第一 `ACPCore`行 `start:` 上，调用 `updateConfiguration:`

**Objective-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## 配置密钥

要在运行时以编程方式更新SDK配置，请使用以下信息更改您的Places扩展配置值。 有关详细信息，请参 [阅配置API参考](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| 键 | 必需 | 描述 |
| :--- | :--- | :--- |
| `places.libraries` | 是 | 用于移动应用程序的Places扩展库。 它指定移动应用程序支持的库ID和库名称。 |
| `places.endpoint` | 是 | 默认的Places查询服务端点，用于获取有关库和POI的信息。 |
| `places.membershipttl` | 否 | 默认值为3600（一小时内的秒）。 指示设备的“放置”会员资格信息将保持有效的时间（以秒为单位）。 |
