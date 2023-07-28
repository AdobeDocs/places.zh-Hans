---
title: 发行说明
description: Places服务的发行说明。
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 2%

---

# 发行说明 {#release-notes}

## 2020 年 7 月 8 日

* **Places和Places监视器扩展**

   * 已为添加Places和Places监视器扩展 [React本机应用程序](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * 已为添加Places和Places监视器扩展 [Cordova应用程序](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * 有关更多信息，请参阅： [使用Places扩展](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 2020年5月12日

* **Places Service**

   * 使用“导入POI”按钮从CSV文件批量导入POI
   * 选择多个POI并批量编辑或添加元数据值

## 2020年5月6日

* **PlacesMonitor 2.2.1**

   * **Android**

      * 改进了日志记录

## 2020年5月5日


* **PlacesMonitor 2.1.3**

   * **iOS**

      * 改进了日志记录

## 2020 年 2 月 20 日

* **ACPPlaces 1.3.1 (iOS)**

   * Places扩展现在会向核心SDK中的事件中心报告版本信息。
   * 设备POI成员资格信息的默认生存时间是从收集时间算起的一小时。 有关更多信息，请参阅 [修改Places成员资格生存时间](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Places 1.4.1 (Android)**

   * Places扩展现在会向核心SDK中的事件中心报告版本信息。
   * 设备POI成员资格信息的默认生存时间是从收集时间算起的一小时。 有关更多信息，请参阅 [修改Places成员资格生存时间](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 2020 年 1 月 27 日

* **PlacesMonitor 2.2.0**

   * **Android**

      * 调用新的Places API以在应用程序启动和应用程序运行时授权更改时收集位置授权状态。
      * 添加了setRequestLocationPermission API和已弃用的setLocationPermission API。

## 2020 年 1 月 9 日

* **位置1.4.0**

   * **Android**

      * 添加了一个新的API， `setAuthorizationStatus`，以设置Places服务的设备授权状态。 该值在Places共享状态下存储和使用。

## 2019年12月4日

* **PlacesMonitor 2.1.2**

   * **iOS**

      * 调用Places API以在设备更改时从设备收集CLAuthorizationStatus。

## 2019年12月3日

* **ACPPlaces 1.3.0**

   * **iOS**

      * 添加了一个新的API， `setAuthorizationStatus`，以设置Places服务的设备授权状态。 该值在Places共享状态下存储和使用。

## 2019 年 11 月 25 日

* **PlacesMonitor 2.1.1**

   * **iOS**

      * 修复了使用多个面板项目选项的Cocoapods项目的导入语句。

## 2019年11月22

* **PlacesMonitor 2.1.1**

   * **Android**

      * 监视器现在可以识别Android设备的启动，并根据需要，根据设备的当前位置在操作系统中再次注册地理围栏。
      * 修复了有时会丢弃登入/退出事件的争用情况。

## 2019年10月9日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 添加了一个新的API， `setRequestAuthorizationLevel`，以设置将提示用户的位置授权请求的类型。


   * **Android**

      * 添加了一个新的API， `setLocationPermission`，以设置将提示用户的位置权限请求的类型。
      * Places监视器现在支持Android 10。

## 2019 年 8 月 8 日

此版本中进行了以下更新：

### UI更新

以下是Places UI的更新列表：

#### 新增功能

* 添加了一个新的列表视图，该视图显示没有映射的POI。
* 为城市、州/省、国家/地区和元数据添加了POI过滤选项。
* 会自动创建组织中的第一个库。
* 向列表视图添加了POI排序。

#### UI更新

* 将列表和详细信息面板移到了UI的右侧。
* 在UI顶部添加了一个新的搜索面板。
* 如果只有一个库，则在创建POI时会自动选择此库。
* 将库管理移入弹出窗口。
* 在过滤器旁添加了POI计数。

## 2019 年 8 月 6 日

此版本中进行了以下更新：

### 监控Launch扩展2.0.0

* 更新了Places监视器2.0的Android和iOS安装说明。

## 2019 年 7 月 31 日

此版本中进行了以下更新：

### Places监视器2.0.0

* 现在，监控状态会在启动之间保留。
* 对于因位置权限请求而导致的回调处理，您不再需要扩展PlacesActivity。
* 更改了现有API，允许开发人员清除设备中的所有Places数据：

  旧API： `public static void stop();`

  新API： `public static void stop (final boolean clearData);`

* 更新了 `getNearbyPointsOfInterest` API可以更有效地处理错误场景。

## 2019 年 7 月 25 日

此版本中进行了以下更新：

### ACPPlacesMonitor 2.0.0

* 要清除设备中的所有Places数据，

  在ACPPlacesMonitor中，替换了现有API `+ (void) stop;` 替换为`+ (void) stop: (BOOL) clearData;`.

* 更新了ACPlaces的使用 `getNearbyPointsOfInterest` API可以更有效地处理错误场景。

## 2019 年 7 月 22 日

此版本中进行了以下更新：

### Android Places 1.3.0

* 添加了一个新API，可从共享状态、应用程序内内存和共享首选项中清除所有与Places相关的数据。
* 修复了在应用程序启动期间共享状态未更新的问题。
* 修复了以下错误 `getNearbyPointsOfInterest` callback正在返回错误代码 `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` 无网络连接。
* `getNearbyPointsOfInterest` API（没有errorCallback）将具有 `successCallback` 如果检索附近的目标点时出错，请使用空的poi列表调用。

## 2019年7月19

此版本中进行了以下更新：

**iOS Places 1.2.0**

添加了一个新的API，可从共享状态、应用程序内内存和以下位置清除所有与Places相关的数据 `NSUserDefaults`.

## 2019年6月25日

此版本中进行了以下更新：

**iOS Places监视器1.0.2**

* 生活质量改进，包括更好的代码内文档和日志记录。

## 2019年6月17

此版本中进行了以下更新：

**iOS Places 1.1.0**

* 添加了新API，以便在检索附近位置时返回错误代码。
* 当隐私状态更改为选择禁用时，现在将从设备中擦除所有与Places相关的数据。
* 修复了在首次启动后，有时由于网络条件恶劣而导致Places事件丢失的问题。
* 修复了在快速连续处理POI条目事件时，通过规则引擎进行的令牌替换有时引用不正确的POI的问题。

## 2019 年 5 月 30 日

**Android Places监视器1.0.1**

* 修复了在启动Places监视时阻止POI进入事件的问题。

## 2019 年 5 月 28 日

修复了Places UI中的以下问题：

* 更新了“位置”中的解决方案切换器，以与Experience Cloud的其余部分保持一致。
* 修复了在未进行任何排名更改的情况下保存排名的问题。
* 将UI中允许的最小半径增加到10米。
* 修复了以下问题：如果您删除字段中的所有数字，则半径字段会重置回20米。

## 2019年5月17

此版本中进行了以下更新：

**Android Places 1.2.0**

* 添加了新API以处理单个地理围栏。
* 修复了错误，以防止发生多个连续进入事件。

**Android Places监视器1.0.0**

适用于Android的Places监视器的初始版本。

Places监视器可管理操作系统级别的位置API，并直接与Places扩展进行通信。 安装这两个扩展后，客户可以在应用程序中执行现成的区域监控。
有关Places监视器的详细信息，请单击此处。


## 2019年5月2

**Android Places 1.1.0**

* 为getNearByPlaces引入了新API，该API具有errorCallback，且使用errorCode调用，以指示错误原因。
* Places扩展现在将事件排入队列，直到获取配置为止。
* 添加了对环境感知配置的支持。
* 错误修复：更正了区域进入/退出事件的键
* 存储最后一个已知位置现在会正确尊重用户的隐私状态


## 2019 年 4 月 9 日

此版本中进行了以下更新：

**iOS Places监视器1.0.1**

* 添加了完整的单元测试范围。
* CI集成(CircleCI)
* 代码覆盖率集成(codecov)

## 2019年3月25日

iOS Places监视器1.0.0

适用于iOS的Places监视器的初始版本。

Places监视器可管理操作系统级别的位置API，并直接与Places扩展进行通信。 安装这两个扩展后，客户可以在应用程序中执行现成的区域监控。

## 2019 年 2 月 28 日

### 测试版

这是Places Service的第一个版本，通过这套工具，客户可以使用真实的位置数据丰富其用户体验。 对于第一个版本，我们的主要用例是使移动设备应用程序能够检索自定义位置数据，并通过Adobe Experience Platform Launch处理这些数据。

### 主要功能

以下是此版本中的主要功能：

#### Places Service UI

我们发布了一个管理UI，您可以在其中查看和管理目标点(POI)。 您还可以将POI组织到库中。 除了标准元数据（如城市、州和类别）之外，我们还支持将自定义元数据添加到POI的功能。

* 要查看用户界面，请转到 [https://places.adobe.com](https://places.adobe.com).
* 要开始使用UI，请参阅 [快速入门](/help/getting-started.md).

#### Places扩展

使用Places扩展，您可以将Places服务库添加到移动设备应用程序中，并根据其POI执行操作。 在Experience Platform Launch中使用规则生成器，您可以触发要在用户进入和退出POI时触发的操作。

在Places扩展中：

* 您可以选择要在应用程序中包含的POI库。
* 在POI进入或退出时触发的规则事件。
* 创建指向用户当前POI的数据元素。

有关Places扩展的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Places API

您可以使用Places API执行以下操作：

* 允许开发人员填充和更新其POI列表。
* 构建您自己的UI或与现有POI数据库集成。
* 使用Places API批处理端点批量导入POI。

  您可以使用提供的Python实用程序完成批量导入。

有关Places API的更多信息，请参阅 [Web服务API](/help/web-service-api/places-web-services.md).

### 即将推出

#### Analytics 集成

正在更新Analytics扩展，以便当用户处于POI（被动调用）中时，自动将位置上下文数据从Places服务数据库添加到所有传出的Analytics调用。 此更新还将允许创建规则以直接在POI进入或退出（活动调用）时触发Analytics跟踪调用。
