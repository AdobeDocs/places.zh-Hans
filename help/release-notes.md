---
title: 发行说明
description: Places Service的发行说明。
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 3%

---

# 发行说明 {#release-notes}

## 2020 年 7 月 8 日

* **Places和Places Monitor扩展**

   * 已为 [React本机应用程序](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * 已为 [科尔多瓦应用程序](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * 有关更多信息，请参阅： [使用Places扩展](https://docs.adobe.com/content/help/zh-Hans/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 2020年5月12日

* **Places Service**

   * 使用“导入POI”按钮从CSV文件批量导入POI
   * 选择多个POI并批量编辑或添加元数据值

## 2020年5月6日

* **PlacesMonitor 2.2.1**

   * **Android**

      * 改进了日志记录

## 2020 年 5 月 5 日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * 改进了日志记录

## 2020 年 2 月 20 日

* **ACPPlaces 1.3.1(iOS)**

   * Places扩展现在会向核心SDK中的事件中心报告版本信息。
   * 设备POI成员资格信息现在具有默认的生存时间，即从收集设备POI时起的一小时。 有关更多信息，请参阅 [修改Places成员资格的生存时间](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1(Android)**

   * Places扩展现在会向核心SDK中的事件中心报告版本信息。
   * 设备POI成员资格信息现在具有默认的生存时间，即从收集设备POI时起的一小时。 有关更多信息，请参阅 [修改Places成员资格的生存时间](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日

* **PlacesMonitor 2.2.0**

   * **Android**

      * 调用新的Places API以在应用程序启动时和应用程序运行时授权更改时收集位置授权状态。
      * 添加了setRequestLocationPermission API和已弃用的setLocationPermission API。

## 2020 年 1 月 9 日

* **Places 1.4.0**

   * **Android**

      * 添加了新API， `setAuthorizationStatus`，以设置Places服务的设备授权状态。 该值会在Places共享状态中存储和使用。

## 2019年12月4日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * 调用Places API以在设备发生更改时从设备中收集CLAuthorizationStatus 。

## 2019年12月3日

* **ACPPlaces 1.3.0**

   * **iOS**

      * 添加了新API， `setAuthorizationStatus`，以设置Places服务的设备授权状态。 该值会在Places共享状态中存储和使用。

## 2019 年 11 月 25 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 修复了使用多个面板项目选项的Cocoapods项目的import语句。

## 2019 年 11 月 22 日

* **PlacesMonitor 2.1.1**

   * **Android**

      * 监视器现在可识别Android设备的启动，并在需要时，根据设备的当前位置向操作系统再次注册地理围栏。
      * 修复了有时导致登入/退出事件被丢弃的争用条件。

## 2019 年 10 月 9 日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 添加了新API， `setRequestAuthorizationLevel`，以设置提示用户的位置授权请求类型。
   * **Android**

      * 添加了新API， `setLocationPermission`，以设置提示用户的位置权限请求类型。
      * Places监视器现在支持Android 10。



## 2019 年 8 月 8 日

此版本中进行了以下更新：

### UI更新

以下是Places UI更新的列表：

#### 新增功能

* 添加了新的列表视图，该视图可显示没有映射的POI。
* 为城市、州、国家/地区和元数据添加了POI筛选选项。
* 组织中的第一个库将自动创建。
* 向列表视图添加了POI排序。

#### UI更新

* 将列表和详细信息面板移至UI的右侧。
* 在UI顶部添加了新的搜索面板。
* 如果仅存在一个库，则在创建POI时将自动选择此库。
* 将库管理移入弹出窗口。
* 在过滤器旁边添加了POI计数。

## 2019 年 8 月 6 日

此版本中进行了以下更新：

### 监视Launch扩展2.0.0

* 更新了Places Monitor 2.0的Android和iOS安装说明。

## 2019 年 7 月 31 日

此版本中进行了以下更新：

### Places Monitor 2.0.0

* 现在，启动次数之间会保留监视状态。
* 处理由位置权限请求生成的回调时，不再需要您扩展PlacesActivity。
* 更改了现有的API，允许开发人员从设备中清除所有Places数据：

   旧API: `public static void stop();`

   新API: `public static void stop (final boolean clearData);`

* 更新了 `getNearbyPointsOfInterest` API，以更有效地处理错误情景。

## 2019年7月25日

此版本中进行了以下更新：

### ACPPlacesMonitor 2.0.0

* 要从设备清除所有Places数据，

   在ACPPlacesMonitor中，替换了现有API `+ (void) stop;` with`+ (void) stop: (BOOL) clearData;`.

* 更新了ACPPlace的使用 `getNearbyPointsOfInterest` API，以更有效地处理错误情景。

## 2019 年 7 月 22 日

此版本中进行了以下更新：

### Android Places 1.3.0

* 添加了一个新API，以清除共享状态、应用程序内内存和共享首选项中所有与Places相关的数据。
* 修复了在应用程序启动期间共享状态未更新的问题。
* 修复了 `getNearbyPointsOfInterest` 回调返回错误代码 `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` 在互联网上。
* `getNearbyPointsOfInterest` API（不含errorCallback）将具有 `successCallback` 在检索附近目标点时出错的情况下，使用空poi列表调用。

## 2019年7月19日

此版本中进行了以下更新：

**iOS Places 1.2.0**

添加了一个新API，以清除共享状态、应用程序内内存和 `NSUserDefaults`.

## 2019年6月25日

此版本中进行了以下更新：

**iOS Places Monitor 1.0.2**

* 生活质量改进，包括更好的代码内文档和日志记录。

## 2019年6月17日

此版本中进行了以下更新：

**iOS Places 1.1.0**

* 添加了新API，用于在检索附近位置时返回错误代码。
* 现在，当隐私状态更改为选择禁用时，所有与Places相关的数据都将从设备中擦除。
* 修复了在首次启动后，有时由于网络条件恶劣而导致Places事件丢失的问题。
* 修复了以下问题：在快速连续处理POI条目事件时，通过规则引擎替换令牌有时会引用错误的POI。

## 2019 年 5 月 30 日

**Android Places监视器1.0.1**

* 修复了启动Places监控时POI的登入事件无法发生的问题。

## 2019 年 5 月 28 日

修复了Places UI中的以下问题：

* 更新了“位置”中的解决方案切换器，以与Experience Cloud的其余部分保持一致。
* 修复了在未进行排名更改的情况下保存排名的问题。
* 将UI中允许的最小半径增加到10米。
* 修复了以下问题：如果删除字段中的所有数字，则radius字段会重置为20米。

## 2019年5月17日

此版本中进行了以下更新：

**Android Places 1.2.0**

* 添加了用于处理单个地理围栏的新API。
* 错误修复，以防止多个连续的登入事件。

**Android Places监视器1.0.0**

Android版Places Monitor的初始版本。

Places Monitor可管理操作系统级别的位置API，并直接与Places扩展通信。 安装这两个扩展后，客户可以对其应用程序进行开箱即用的区域监控。
有关Places Monitor的更多信息，请单击此处。


## 2019年5月2日

**Android Places 1.1.0**

* 引入了getNearByPlaces的新API，该API具有errorCallback，通过errorCode进行调用，以指示错误原因。
* Places扩展现在会将事件排入队列，直到获取配置为止。
* 添加了对环境感知配置的支持。
* 错误修复：更正了区域登入/退出事件的键
* 现在，存储最后一个已知位置会正确遵守用户的隐私状态


## 2019 年 4 月 9 日

此版本中进行了以下更新：

**iOS Places Monitor 1.0.1**

* 添加了完整的单元测试覆盖。
* CI集成(CircleCI)
* 代码覆盖集成(codecov)

## 2019年3月25日

iOS Places Monitor 1.0.0

Places Monitor for iOS的初始版本。

Places Monitor可管理操作系统级别的位置API，并直接与Places扩展通信。 安装这两个扩展后，客户可以对其应用程序进行开箱即用的区域监控。

## 2019 年 2 月 28 日

### 测试版

这是Places Service的第一个版本，Places Service是一套工具，允许客户使用真实世界的位置数据丰富其用户体验。 在第一个版本中，我们的主要用例是使移动设备应用程序能够检索自定义位置数据，并通过Adobe Experience Platform Launch对该数据执行操作。

### 主要功能

以下是此版本中的主要功能：

#### Places Service UI

我们发布了一个管理UI，您可以在其中查看和管理目标点(POI)。 您还可以将POI组织到库中。 除了城市、州和类别等标准元数据之外，我们还支持向POI添加自定义元数据的功能。

* 要查看UI，请转到 [https://places.adobe.com](https://places.adobe.com).
* 要开始使用UI，请参阅 [入门指南](/help/getting-started.md).

#### Places扩展

使用Places扩展，您可以将Places Service库添加到移动应用程序并对其POI执行操作。 在Experience Platform Launch中使用规则生成器，您可以触发在用户进入和退出POI时触发的操作。

在Places扩展中：

* 您可以选择要包含在应用程序中的POI库。
* 在POI进入或退出时触发的规则事件。
* 创建指向用户当前POI的数据元素。

有关Places扩展的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places API

您可以使用Places API执行以下操作：

* 允许开发人员填充和更新其POI列表。
* 构建您自己的UI或与现有POI数据库集成。
* 使用Places API批量端点来批量导入POI。

   您可以使用提供的Python实用程序完成批量导入。

有关Places API的更多信息，请参阅 [Web服务API](/help/web-service-api/places-web-services.md).

### 即将推出

#### Analytics 集成

将更新Analytics扩展，以在用户处于POI（被动调用）中时，自动将Places Service数据库中的位置上下文数据添加到所有传出的Analytics调用中。 此更新还允许创建规则，以便在POI登入或退出（活动调用）时直接触发Analytics跟踪调用。
