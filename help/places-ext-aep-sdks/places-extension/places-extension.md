---
title: Places 扩展
description: Places扩展允许您根据用户的位置执行操作。
exl-id: 09c02753-09b3-4e07-82b2-b6c72c4e0e42
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 5%

---

# Places 扩展 {#places-extension}

Places扩展允许您根据用户的位置执行操作。 此扩展是到Places查询服务API的接口。 通过侦听包含GPS坐标和地理围栏区域事件的事件，此扩展可调度由规则引擎处理的新事件。 Places扩展还会检索并提供从API检索的应用程序数据的最接近POI的列表。 API返回的区域存储在缓存和持久性中，允许进行有限的离线处理。

## 在Adobe Experience Platform Launch中安装Places扩展

1. 在Experience Platform Launch中，单击 **[!UICONTROL 扩展]** 选项卡。
1. 在 **[!UICONTROL 目录]** 选项卡，找到 **[!UICONTROL 地标]** 扩展上，然后单击 **[!UICONTROL 安装]**.
1. 选择要在此属性中使用的Places库。 这些是可在应用程序中访问的库。
1. 单击&#x200B;**[!UICONTROL 保存]**。

   当您单击 **[!UICONTROL 保存]**，Experience PlatformSDK将在Places服务中搜索您选择的库中的POI。 在构建应用程序时，POI数据不会包含在库的下载中，但运行时基于位置的POI子集会下载到最终用户的设备，并且会根据用户的GPS坐标进行下载。

1. 完成发布过程以更新SDK配置。

   有关在Experience Platform Launch中发布的更多信息，请参阅 [发布](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html).

### 配置Places扩展 {#configure-places-extension}

![](/help/assets/places-extension.png)

## 将Places扩展添加到您的应用程序 {#add-places-to-app}

您可以将Places扩展添加到Android和iOS应用程序。 下面显示了将地标添加到iOS或Android应用程序的步骤。 Places扩展也可用于以下平台。 有关在使用以下平台之一进行开发时向应用程序添加地标的信息，请参阅随附的链接：

**[Cordova Places插件](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[React Native Places插件](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

**[Flutter Places插件](https://github.com/adobe/flutter-acpplaces_monitor)**

**[Xamarin Places插件](https://github.com/adobe/xamarin-acpcore)**


### Android

要使用Java将Places扩展添加到应用程序，请执行以下操作：

1. 使用应用程序的Gradle文件将Places扩展添加到您的项目中。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. 在应用程序的主活动中导入Places扩展。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

要使用Objective-C或Swift将Places扩展添加到您的应用程序中，请执行以下操作：

1. 添加地标和 [移动核心](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) 库添加到您的项目。 您需要将以下pod添加到您的 `Podfile`：

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   或者，如果您没有使用Cocoapods，则可以手动将移动核心和Places库包含到我们的 [版本页面](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) 在Github上。

1. 更新您的Cocoapods：

   ```objective-c
   pod update
   ```

1. 打开Xcode，然后在AppDelegate类中，导入Core和Places标头：

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

### 在移动核心中注册Places扩展 {#register-places-mobile-core}

您需要在Android和iOS中通过Mobile Core注册Places扩展。

#### Android

在您应用程序的 `OnCreate` 方法注册Places扩展：

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

在您应用程序的 `application:didFinishLaunchingWithOptions:` 方法，在其他SDK注册调用中注册Places扩展：

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

### 修改Places成员资格生存时间 {#places-ttl}

位置数据可能会很快过时，尤其是当设备未收到后台位置更新时。

通过设置，控制Places成员资格数据在设备上的生存时间 `places.membershipttl` 配置设置。 传入的值表示Places状态对设备保持有效的秒数。

#### Android

回调内部 `MobileCore.start()` 在调用之前使用必要的更改更新配置 `lifecycleStart`：

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

在回调的第一行 `ACPCore`的 `start:` 方法，调用 `updateConfiguration:`

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

## 配置键

要在运行时以编程方式更新SDK配置，请使用以下信息更改Places扩展配置值。 有关更多信息，请参阅 [配置API参考](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| 键 | 必需 | 描述 |
| :--- | :--- | :--- |
| `places.libraries` | 是 | 适用于移动设备应用程序的Places扩展库。 它指定库ID以及移动设备应用程序支持的库的名称。 |
| `places.endpoint` | 是 | 默认的Places查询服务端点，用于获取有关库和POI的信息。 |
| `places.membershipttl` | 否 | 默认值为3600（一小时中的秒）。 指示设备的Places成员资格信息将保持有效的时间（秒）。 |
