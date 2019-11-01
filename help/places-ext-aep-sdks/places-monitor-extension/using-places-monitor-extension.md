---
title: 使用地点监视器扩展
seo-title: 使用地点监视器扩展
description: 有关如何安装、配置和使用Places Monitor扩展的信息。
seo-description: '有关如何安装、配置和使用Places Monitor扩展的信息。 '
translation-type: tm+mt
source-git-commit: a2e30282789d9834e5c65502e28ddb25f3c55dfa

---


# 使用地点监视器扩展 {#using-places-monitor-extension}

要使用“地点监视器”扩展，请完成以下任务：

## 在Experience Platform Launch中安装Places Monitor扩展

1. 在Experience Platform Launch中，单击选项 **[!UICONTROL Extensions]** 卡。
1. 在选项 **[!UICONTROL Catalog]** 卡上，找到扩展 **[!UICONTROL Places Monitor]** 名，然后单击“ **安装”**。
1. 单击 **[!UICONTROL Save]**。
1. 按照发布过程更新SDK配置。

### 配置地点监视器扩展 {#configure-places-monitor-extension}

“地点监视器”扩展没有配置任务。

![配置地点监视器](/help/assets/configure_places_monitor.png)‌

## 将Places Monitor扩展添加到您的应用程序 {#add-monitor-extension-to-app}

您需要将“地点监视器”扩展添加到Android或iOS应用程序。

### Android

在Android中，完成以下步骤：

#### Java

1. 使用应用程序的Gradle文件将Places Monitor扩展和Places扩展添加到您的项目。

1. 在Gradle文件中还包括最新的Google Location服务。

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. 在应用程序的主活动中导入“地点监视器”扩展。

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

在iOS中，完成以下步骤：

1. 通过添加，通过Cocoapod将库添 `Podfile` 加到项目 `pod 'ACPPlacesMonitor'`。
1. 导入地点和地点监视器库：

#### Objective-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## 注册并启动地点监视器 {#register-start-places-monitor}

您需要注册并启动Android或iOS中的地点监视器。

## Android

在Android中，完成以下步骤：

### Java

在您的应用程序方法中， `OnCreate` 注册Places Monitor扩展：

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
        } catch (Exception e) {
            //Log the exception
         }
    }
}
```

**** 重要说明：地点监视取决于地点扩展。 手动安装Places Monitor扩展时，请确保还将库添 `places.aar` 加到项目中。

## iOS

在iOS应用程序中`application:didFinishLaunchingWithOptions`，使用Mobile Core注册 `PlacesMonitor` 和放置：

### Objective-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES; 
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })
    
    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>地点监视取决于地点扩展。 手动安装“地点监视器”扩展时，请确保还将库添 `libACPPlaces_iOS.a` 加到项目中。


## 向清单添加权限

### Android

**Java**

对于所有版本的Android，要声明您的应用程序需要位置权限，请在应用程序清单中添加一个元素，作为顶级元素的子 `<uses-permission>``<manifest>` 项。 对于以API级别29及更高版本为目标的Android应用程序，要允许应用程序访问后台位置，请包括ACCESS_BACKGROUND_LOCATION权限。

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" /> 
  <application>        
    ...    
  </application>
</manifest>
```


## 在后台启用位置更新 {#enable-location-updates-background}

iOS支持将位置事件交付到已暂停或不再运行的应用程序。 要在后台接收地点监视器扩展的位置更新，请在中为您的应用程序配置位置更新功能 `Xcode.background-location-updates`。

![使用地点监视器](/help/assets/using-the-places-monitor_1.png)

## 配置plist键

应用程序的文件中必须包含以下键 `Info.plist` :

* `NSLocationWhenInUseUsageDescription` -文本应描述应用程序在前台运行时请求访问用户位置信息的原因。
* `NSLocationAlwaysAndWhenInUseUsageDescription` -文本应描述应用程序始终请求访问用户位置信息的原因。

>[!TIP]
>
>如果您的应用程序支持iOS 10及更早版本， `NSLocationAlwaysUsageDescription` 则该键也是必需的。

![](/help/assets/using-the-places-monitor_2.png)

