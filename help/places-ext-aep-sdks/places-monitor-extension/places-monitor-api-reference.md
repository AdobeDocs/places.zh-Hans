---
title: Places Monitor API参考
description: 地点监视器的API列表。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Places Monitor API参考 {#places-api-reference}

## 注册地点监视器扩展

在Core Event Hub中注册Places Monitor扩展。

### RegisterExtension(Android)

以下是此API的语法和示例代码：

#### 语法

下面是Java中的语法：

```java
public static void registerExtension();
```

#### 示例

在初始化Experience Platform SDK `onCreate` 其余部分的方法中调用此方法。

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension(iOS)

以下是此API的语法和示例代码：

#### 语法

下面是Objective-C中的语法：

```objective-c
+ (void) registerExtension;
```

#### 示例

This method should be called in the `didFinishLaunchingWithOptions` delegate method of the `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## 扩展版

返回Places Monitor扩展的当前版本

### ExtensionVersion(Android)

以下是此API的语法和示例代码：

#### 语法

```java
public static String extensionVersion();
```

#### 示例

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion(iOS)

以下是此API的语法和示例代码：

#### 语法

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### 示例

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## 启动设备监控

开始跟踪设备的位置并监控附近的地点。

### 开始(Android)

如果用户尚未授予使用设备位置的授权，则对 `start` API的第一次调用将提示用户授予权限。

以下是此API的语法和示例代码：

#### 语法

```java
public static void start();
```

#### 示例

```java
PlacesMonitor.start();
```

### 开始(iOS)

>[!IMPORTANT]
>
>要开始监控，位置服务必须具有必要的授权：
>
>* 如果尚未向应用程序提供对Places service的授权，则对 `start` API的第一次调用请求授权使用为应用程序配置的Places Service。
>* 根据设备的功能，如果已提供授权，地点监视器会根据当前设置跟踪用户的位置 `ACPPlacesMonitorMode`。 默认情况下，监视器使用 `ACPPlacesMonitorModeSignificantChanges`。


>[!CAUTION]
>
>如果在SDK完成初始化之前发出启动监视的调用，则可能会忽略该调用。

您可以通过从提供给的回调中调用来确保SDK `start` 已完成初始化 `ACPCore::start:`。

以下是此API的语法和示例代码：

#### 语法

```objectivec
+ (void) start;
```

#### 示例

在SDK初始化时启动“地点监视器”:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

稍后在应用程序执行中启动Places Monitor:

```objective-c
[ACPPlacesMonitor start];
```

## 停止设备监视

停止跟踪设备的位置。

### 停止(Android)

以下是此API的语法和示例代码：

#### 语法

```java
public static void stop();
```

#### 示例

```java
PlacesMonitor.stop();
```

### 停止(iOS)

以下是此API的语法和示例代码：

#### 语法

```objectivec
+ (void) stop;
```

#### 示例

```objective-c
[ACPPlacesMonitor stop];
```

## 更新位置

使用此API可立即更新设备的位置。 当您调用此API时，设备将尝试按照您指定的准确度确定位置。 此过程还会刷新扩展监视的附近POI。

### UpdateLocation(Android)

以下是此API的语法和示例代码：

#### 语法

```java
public static void updateLocation();
```

#### 示例

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow(iOS)

#### 语法

```objective-c
+ (void) updateLocationNow;
```

#### 示例

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## 应用程序位置权限

您可以使用此API设置用户被提示并授权用于Places service的位置权限类型。

### SetLocationPermission(Android)

此API设置用户被提示选择的位置权限请求的类型。

>[!TIP]
>
>此API仅对Android 10及更高版本的设备有效。
>
>要设置向用户显示的相应授权提示，请在 `PlacesMonitor.start()`调用此方法时，在主动监视时，会将位置权限级别升级到所请求的权限值。 如果应用程序用户已提供或拒绝所请求的授权级别，或者您尝试将权限从降级到 `ALWAYS_ALLOW` , `WHILE_USING_APP`则此方法无效。

位置权限可以设置为以下值之一：

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   此值仅在使用应用程序时提示用户访问设备位置。 当用户在其设备屏幕上查看应用程序时（例如，活动正在前台运行），应用程序被视为正在使用。

   >[!TIP]
   >
   >确保在应用程序的清单文件中设置了ACCESS_FINE_LOCATION用户权限。

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   此值提示用户访问设备位置，即使应用程序是后台应用程序也是如此。

   >[!TIP]
   >
   >确保在应用程序的清单文件中设置了ACCESS_BACKGROUND_LOCATION和ACCESS_FINE_LOCATION用户权限。

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` 是默认位置权限值。

>[!IMPORTANT]
>
>如果应用程序用户获得了 `WHILE_USING_APP` 该权限，则地理围栏不会向操作系统注册。 因此，“地点监视”扩展不会在后台发生的区域触发进入／退出事件。

以下是此API的语法和示例代码：

#### 语法

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### 示例

要请求权限，请执 `WHILE_USING_APP` 行以下操作：

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

升级到权 `ALWAYS_ALLOW` 限：

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel(iOS)

此API设置将提示用户的位置授权请求的类型。

要设置向用户显示的相应授权提示，请在拨叫前 `SetRequestAuthorizationLevel` 拨叫 `[ACPPlacesMonitor start]`。 要设置向用户显示的相应授权提示，请在 `[ACPPlacesMonitor start]`主动监控时调用此方法会将位置授权级别升级到所请求的授权值。 如果应用程序用户已经提供或拒绝所请求的授权级别，或者当权限从授权降级到授权时， `ACPPlacesRequestAuthorizationLevelAlways``ACPPlacesRequestAuthorizationLevelWhenInUse` 此方法不起作用。

授权级别可以设置为以下值之一：

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   在应用程序使用过程中请求用户使用Places service的权限。 用户提示包含app Info. `NSLocationWhenInUseUsageDescription` plist文件中键的文本，调用此方法时需要该键的存在。 有关详细信息，请参 [阅有关requestWhenInUseAuthorization的Apple文档](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization)。

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   使用此枚举可请求Places Service，即使应用程序处于后台也是如此。 您必须在应 `NSLocationAlwaysUsageDescription` 用程 `NSLocationWhenInUseUsageDescription` 序的Info.plist中包含和键。 这些键定义将在用户提示期间显示的文本。 有关详细信息，请参阅 [Apple的requestAlwaysAuthorization文档](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization)。

`ACPPlacesRequestAuthorizationLevelAlways` 是默认的请求授权值。

>[!IMPORTANT]
>
>授权使用权限的应用程序 `ACPPlacesRequestAuthorizationLevelWhenInUse` 不会在后台发生的区域触发进入／退出事件。

以下是此API的语法和示例代码：

#### 语法

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### 示例

要请求权限，请执 `ACPPlacesRequestAuthorizationLevelWhenInUse` 行以下操作：

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

升级到授 `ACPPlacesRequestAuthorizationLevelAlways` 权：

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## 监视模式（仅限iOS）

可以将监视设置为以下值之一：

* `ACPPlacesMonitorModeContinuous`

   监控扩展更频繁地接收和处理位置。 该监控策略耗电量大，但精度较高。 有关详细信息，请参 [阅Apple持续监控文档](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)。

* `ACPPlacesMonitorModeSignificantChanges`

   监视扩展仅在设备已经从先前处理的位置移动了很远的距离之后接收并处理位置更新。 该监控策略比连续监控策略耗电少。 有关详细信息，请参 [阅Apple重要监控文档](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode(iOS)

以下是此API的语法和示例代码：

#### 语法

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### 示例

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
