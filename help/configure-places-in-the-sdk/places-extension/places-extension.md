---
title: 地点扩展
seo-title: 地点扩展
description: “地点”扩展允许您根据用户的位置采取行动。
seo-description: “地点”扩展允许您根据用户的位置采取行动。
translation-type: tm+mt
source-git-commit: 1fb87285d2ccd581ee59ab1b1efbec4af04a0fab

---


# 地点扩展 {#places-extension}

“地点”扩展允许您根据用户的位置采取行动。 此扩展是Places Query Service API的接口。 通过侦听包含GPS坐标和地理区域事件的事件，此扩展将调度由规则引擎处理的新事件。 Places扩展还检索并提供从API检索的应用程序数据的最近POI的列表。 由API返回的区域存储在缓存和持久化中，这允许有限的脱机处理。

## 在Adobe Experience Platform Launch中安装Places扩展

1. 在Experience Platform Launch中，单击选项 **[!UICONTROL Extensions]** 卡。
2. 在选项 **[!UICONTROL Catalog]** 卡上，找到扩 **[!UICONTROL Adobe Places]** 展名并单击 **[!UICONTROL Install]**。
3. 选择要在此属性中使用的地点库。 这些库将在您的应用程序中访问。
4. 单击 **[!UICONTROL Save]**。

   单击时， **[!UICONTROL Save]** Experience Platform SDK会在您选择的库中搜索Places Services中的POI。 在您构建应用程序时，库下载中不包括POI数据，但基于位置的POI子集在运行时下载到最终用户的设备，并基于用户的GPS坐标。

5. 完成发布过程以更新SDK配置。

   有关在Experience Platform Launch中发布的更多信息，请参阅 [发布](https://docs.adobelaunch.com/launch-reference/publishing)。

### 配置Places扩展 {#configure-places-extension}

![](//help/assets/places-extension.png)

## 将Places扩展添加到您的应用程序 {#add-places-to-app}

您可以将Places扩展添加到Android和iOS应用程序。

### Android

要使用Java将Places扩展添加到应用程序，请执行以下操作：

1. 使用应用程序的Gradle文件将Places扩展添加到您的项目。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

2. 在应用程序的主活动中导入“地点”扩展。

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

要使用Objective-C或Swift将Places扩展添加到您的应用程序，请执行以下操作：

1. 将Places和 [Mobile Core](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) Libraries添加到项目。 您需要将以下窗格添加到您的 `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   或者，如果您不使用Cocoapod，则可以从Github上的发布页面手动包含Mobile core和 [Places库](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) 。

2. 更新您的Cocopad:

   ```objective-c
   pod update
   ```

3. 打开Xcode，在AppDelegate类中，导入核心和地点标题：

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

### 使用移动核心注册地点 {#register-places-mobile-core}

您需要在Android和iOS中使用Mobile Core注册地点。

#### Android

在您的应用程序方 `OnCreate` 法中注册位置服务扩展：

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

## 配置密钥

要在运行时以编程方式更新SDK配置，请使用以下信息更改您的Places配置值。 有关详细信息，请参 [阅配置API参考](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)。

| 键 | 必需 | 描述 |
| :--- | :--- | :--- |
| `places.libraries` | 是 | 放置移动应用程序的库。 它指定移动应用程序支持的库ID和库名称。 |
| `places.endpoint` | 是 | 默认的Experience Platform Location Query service端点，用于获取有关库和POI的信息。 |
