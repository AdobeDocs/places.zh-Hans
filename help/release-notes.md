---
title: 发行说明
description: Places Service的发行说明。
translation-type: tm+mt
source-git-commit: f5fa6005396e3c5b5b8eb92c7c920d2d0d974743
workflow-type: tm+mt
source-wordcount: '1419'
ht-degree: 3%

---


# 发行说明 {#release-notes}

## 2020年5月6日

* **PlacesMonitor 2.2.1**

   * **Android**

      * 改进的日志记录

## 2020年5月5日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * 改进的日志记录

## 2020 年 2 月 20 日

* **ACPPlaces 1.3.1(iOS)**

   * 现在，Places Extension将版本信息报告给核心SDK中的事件中心。
   * 设备POI会员资格信息现在的默认有效时间为收集后一小时。 有关详细信息，请 [参阅修改地点会员资格的生效时间](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1(Android)**

   * 现在，Places Extension将版本信息报告给核心SDK中的事件中心。
   * 设备POI会员资格信息现在的默认有效时间为收集后一小时。 有关详细信息，请 [参阅修改地点会员资格的生效时间](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日

* **PlacesMonitor 2.2.0**

   * **Android**

      * 调用新的Places API以在应用程序启动时和在应用程序运行时授权发生更改时收集位置授权状态。
      * 添加了setRequestLocationPermission API和已弃用的setLocationPermission API。

## 2020 年 1 月 9 日

* **Places 1.4.0**

   * **Android**

      * 添加了新的API `setAuthorizationStatus`，用于设置Places Services的设备授权状态。 该值将存储并用于“地点”共享状态。

## 2019 年 12 月 4 日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * 调用Places API在设备发生更改时从设备收集CLAuthorizationStatus。

## 2019 年 12 月 3 日

* **ACPPlaces 1.3.0**

   * **iOS**

      * 添加了新的API `setAuthorizationStatus`，用于设置Places Services的设备授权状态。 该值将存储并用于“地点”共享状态。

## 2019 年 11 月 25 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 修复了使用多个窗格项目选项的Cocoapods项目的导入语句。

## 2019 年 11 月 22 日

* **PlacesMonitor 2.1.1**

   * **Android**

      * 监视器现在可识别Android设备的启动，并根据设备的当前位置在操作系统中重新注册地理围栏（如果需要）。
      * 修复了有时导致入口／出口事件被丢弃的竞态条件。

## 2019 年 10 月 9 日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 添加了新的API `setRequestAuthorizationLevel`，用于设置将提示用户的位置授权请求类型。
   * **Android**

      * 添加了新的API `setLocationPermission`，用于设置将提示用户的位置权限请求类型。
      * 现在，位置监视器支持Android 10。



## 2019 年 8 月 8 日

此版本中进行了以下更新：

### UI更新

以下是对Places UI的更新列表:

#### 新增功能

* 添加了新的列表视图符，显示没有映射的POI。
* 添加了适用于城市、州、国家和元数据的POI过滤选项。
* 将自动创建组织中的第一个库。
* 为列表视图添加了POI排序。

#### UI更新

* 已将列表和详细信息面板移到UI的右侧。
* 在UI顶部添加了新的搜索面板。
* 如果只有一个库，则在创建POI时会自动选择此库。
* 已将库管理移到弹出窗口中。
* 在过滤器旁添加了一个POI计数。

## 2019 年 8 月 6 日

此版本中进行了以下更新：

### 监视器启动扩展2.0.0

* 更新了Places Monitor 2.0的Android和iOS安装说明。

## 2019 年 7 月 31 日

此版本中进行了以下更新：

### Places Monitor 2.0.0

* 现在，监视状态会在启动项之间保留。
* 对回调的处理（由位置权限请求引起）不再要求您扩展PlacesActivity。
* 更改了现有API，使开发人员能从设备清除所有Places数据：

   旧API: `public static void stop();`

   New API: `public static void stop (final boolean clearData);`

* 更新了API的使 `getNearbyPointsOfInterest` 用，以更有效地处理错误情景。

## 2019 年 7 月 25 日

此版本中进行了以下更新：

### ACPPlacesMonitor 2.0.0

* 要从设备清除所有Places数据，

   在ACPPlacesMonitor中，将现有API替换 `+ (void) stop;` 为`+ (void) stop: (BOOL) clearData;`。

* 更新了ACPPlaces API的使用 `getNearbyPointsOfInterest` ，以更有效地处理错误情景。

## 2019 年 7 月 22 日

此版本中进行了以下更新：

### Android Places 1.3.0

* 添加了一个新API，可从共享状态、应用程序内内存和共享首选项中清除所有与Places相关的数据。
* 修复了在应用程序开始期间共享状态未更新的问题。
* 修复了回调在无 `getNearbyPointsOfInterest` Internet上返回错误 `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` 代码的错误。
* `getNearbyPointsOfInterest` 如果检索附近的兴趣点 `successCallback` 时出错，API（不带errorCallback）将调用空poi列表。

## 2019 年 7 月 19 日

此版本中进行了以下更新：

**iOS Places 1.2.0**

添加了一个新API，可从共享状态、应用程序内内存和中清除所有与Places相关的数据 `NSUserDefaults`。

## 2019 年 6 月 25 日

此版本中进行了以下更新：

**iOS Places Monitor 1.0.2**

* 生命质量改进，包括更好的代码内文档和记录。

## 2019 年 6 月 17 日

此版本中进行了以下更新：

**iOS Places 1.1.0**

* 添加了新API，当检索附近位置时返回错误代码。
* 当隐私状态变为退出时，所有与地点相关的数据现在将从设备上擦除。
* 修复了在首次启动后，有时会由于网络状况不佳而导致Places事件丢失的问题。
* 修复了在快速连续处理POI条目事件时，通过规则引擎替换令牌有时会引用错误POI的问题。

## 2019 年 5 月 30 日

**Android Places Monitor 1.0.1**

* 修复了在启动“位置”监视时阻止POI进入事件的问题。

## 2019 年 5 月 28 日

修复了“位置”UI中的以下问题：

* 更新了Places中的解决方案切换程序，使其与Experience Cloud的其余部分保持一致。
* 修复了在未进行排名更改的情况下，会保存排名的问题。
* 将UI中允许的最小半径增加到10米。
* 修复了删除字段中的所有数字时radius字段重置回20米的问题。

## 2019 年 5 月 17 日

此版本中进行了以下更新：

**Android Places 1.2.0**

* 添加了一个新API，用于处理单个地理围栏。
* 用于防止多个连续输入事件的错误修复。

**Android Places Monitor 1.0.0**

Places Monitor for Android的初始版本。

地点监视器管理操作系统级位置API并直接与地点扩展通信。 安装这两个扩展后，客户可以在其应用程序中进行开箱即用的区域监控。
有关位置监视器的详细信息，请单击此处。


## 2019 年 5 月 2 日

**Android Places 1.1.0**

* 为getNearByPlaces引入了一个新的API，它有一个errorCallback，用一个errorCode调用，它指示错误的原因。
* 现在，Places扩展将事件排队，直到获得配置。
* 增加了对环境感知配置的支持。
* 错误修复： 更正了区域进出事件的键
* 上一个已知位置的存储现在正确遵守用户的隐私状态


## 2019 年 4 月 9 日

此版本中进行了以下更新：

**iOS Places Monitor 1.0.1**

* 增加了完整的单元测试覆盖。
* CI集成(CircleCI)
* 代码覆盖集成(codecov)

## 2019 年 3 月 25 日

iOS Places Monitor 1.0.0

iOS地点监视器的初始版本。

地点监视器管理操作系统级位置API并直接与地点扩展通信。 安装这两个扩展后，客户可以在其应用程序中进行开箱即用的区域监控。 有关“地点监视器”的详细信息，请参 [阅“地点监视器”扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

## 2019 年 2 月 28 日

### 测试版

这是Places Service的第一个版本，这是一套工具，允许客户利用真实的位置数据丰富其用户的体验。 对于第一个版本，我们的主要用例是使移动应用程序能够检索自定义位置数据并通过Adobe Experience Platform Launch对该数据执行操作。

### 主要功能

以下是此版本中的主要功能：

#### Places Service UI

我们发布了管理UI，您可以在此视图和管理您的兴趣点(POI)。 您还可以将POI组织到库中。 除了城市、州和类别等标准元数据之外，我们还支持向POI添加自定义元数据的功能。

* 要查看UI，请转 [到https://places.adobe.com](https://places.adobe.com)。
* 要开始使用UI，请参阅 [入门](/help/getting-started.md)。

#### 地点扩展

使用Places Extension，您可以将Places Service库添加到移动应用程序并对其POI执行操作。 使用Experience Platform Launch中的规则构建器，您可以触发用户进入和退出POI时触发的操作。

在“地点”扩展中：

* 您可以选择要包含在应用程序中的POI库。
* 在POI进入或退出时触发的规则事件。
* 创建指向用户当前POI的数据元素。

For more information about the Places extension, see [Places extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places API

您可以使用Places API执行以下操作：

* 允许开发人员填充和更新其POI列表。
* 构建您自己的UI或与现有POI数据库集成。
* 使用Places API批处理端点批量导入POI。

   您可以使用提供的Python实用程序完成批量导入。

有关Places API的详细信息，请参 [阅Web服务API](/help/web-service-api/places-web-services.md)。

### 即将推出

#### Analytics 集成

当用户处于POI（被动调用）中时，将更新Analytics扩展以自动将位置上下文数据从您的Places Service数据库添加到所有传出Analytics调用。 此更新还允许创建规则，以在POI进入或退出（活动呼叫）时直接触发Analytics跟踪呼叫。
