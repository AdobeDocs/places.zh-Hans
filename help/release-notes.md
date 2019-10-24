---
title: Adobe Experience Platform Places发行说明
seo-title: Adobe Experience Platform Places的发行说明。
description: Adobe Experience Platform Places的发行说明。
seo-description: Adobe Experience Platform Places的发行说明。
translation-type: tm+mt
source-git-commit: 9fc484fd44c74ad77255668e4fbd7bc1642932e2

---


# 发行说明 {#release-notes}

以下是Adobe Experience Platform Places(Places)的发行说明：

## 2019 年 10 月 9 日

* **PlacesMonitor 2.1.0**

   * **iOS**

      * 添加了新的API, `setRequestAuthorizationLevel`用于设置将提示用户的位置授权请求的类型。
   * **Android**

      * 添加了新的API, `setLocationPermission`用于设置将提示用户的位置权限请求类型。
      * Places Monitor现在支持Android 10。



## 2019年8月8日

此版本中进行了以下更新：

### 地点UI更新

以下是对地点UI的更新列表：

#### 新增功能

* 添加了一个新列表视图，该视图显示不带地图的POI。
* 添加了适用于城市、州、国家和元数据的POI过滤选项。
* 将自动创建组织中的第一个库。
* 将POI排序添加到列表视图。

#### UI更新

* 已将列表和详细信息面板移到UI的右侧。
* 在UI顶部添加了新的搜索面板。
* 如果只有一个库，则在创建POI时会自动选择此库。
* 将库管理移到弹出窗口中。
* 在过滤器旁边添加了一个POI计数。

## 2019年8月6日

此版本中进行了以下更新：

### Places Monitor Launch Extension 2.0.0

* 更新了Places Monitor 2.0的Android和iOS安装说明。

## 2019 年 7 月 31 日

此版本中进行了以下更新：

### Places Monitor 2.0.0

* 监视状态现在会在启动项之间保留。
* 对回调的处理（由位置权限请求引起）不再要求您扩展PlacesActivity。
* 更改了现有API，使开发人员能从设备清除所有地点数据：

   旧API: `public static void stop();`

   新API: `public static void stop (final boolean clearData);`

* 更新了Places API的使用 `getNearbyPointsOfInterest` 以更有效地处理错误方案。

## 2019 年 7 月 25 日

此版本中进行了以下更新：

### ACPPlacesMonitor 2.0.0

* 要从设备清除所有地点数据，

   在ACPPlacesMonitor中，将现有API替换 `+ (void) stop;` 为`+ (void) stop: (BOOL) clearData;`。

* 更新了ACPPlaces API的使用 `getNearbyPointsOfInterest` ，以更有效地处理错误场景。

## 2019 年 7 月 22 日

此版本中进行了以下更新：

### Android Places 1.3.0

* 添加了一个新API，用于从共享状态、应用程序内内存和共享首选项中清除所有与地点相关的数据。
* 修复了在应用程序启动期间共享状态未更新的问题。
* 修复了回调在无 `getNearbyPointsOfInterest` Internet上返回错误代 `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` 码的错误。
* `getNearbyPointsOfInterest` 如果检索附近的目标点时出错， `successCallback` API（不带errorCallback）将调用空的poi列表。

## 2019 年 7 月 19 日

此版本中进行了以下更新：

**iOS Places 1.2.0**

添加了一个新的API，可从共享状态、应用程序内内存和中清除所有与Places相关的数据 `NSUserDefaults`。

## 2019 年 6 月 25 日

此版本中进行了以下更新：

**iOS Places Monitor 1.0.2**

* 提高生命质量，包括更好的代码内文档和记录。

## 2019 年 6 月 17 日

此版本中进行了以下更新：

**iOS Places 1.1.0**

* 添加了新的API，用于在检索附近位置失败时返回错误代码。
* 当隐私状态变为退出时，所有与地点相关的数据现在将从设备上清除。
* 修复了在首次启动后，有时由于网络状况不佳而导致“地点”事件丢失的问题。
* 修复了在快速连续处理POI条目事件时，通过规则引擎进行的令牌替换有时会引用错误POI的问题。

## 2019年5月30日（地点）

**Android Places Monitor 1.0.1**

* 修复了在“地点”监视启动时，POI的进入事件无法发生的问题。

## 2019 年 5 月 28 日

修复了“地点”UI中的以下问题：

* 更新了Places中的解决方案切换程序，使其与Experience cloud的其余部分保持一致。
* 修复了在未进行排名更改的情况下会保存排名的问题。
* 将UI中允许的最小半径增加到10米。
* 修复了如果删除字段中的所有数字，radius字段将重置回20米的问题。

## 2019年5月17日（地点）

此版本中进行了以下更新：

**Android Places 1.1.0**

* 添加了用于处理单个地理围栏的新API。
* 用于防止多个连续进入事件的错误修复。

**Android Places Monitor 1.0.0**

Places Monitor for android的初始版本。

地点监视器管理操作系统级位置API并直接与地点扩展通信。 安装这两个扩展后，客户可以在其应用程序中进行开箱即用的区域监控。
有关地点监视器的详细信息，请单击此处。


## 2019 年 5 月 2 日

**Android Places 1.1.0**

* 为getNearByPlaces引入了一个新的API，它有一个errorCallback，用指示错误原因的errorCode进行调用。
* 现在，“地点”扩展将事件排队，直到获得配置。
* 增加了对环境感知型配置的支持。
* 错误修复：更正了区域进入／退出事件的键
* 现在，对上一个已知位置的存储正确遵守用户的隐私状态


## 2019 年 4 月 9 日

此版本中进行了以下更新：

**iOS Places Monitor 1.0.1**

* 增加了完整的单元测试覆盖。
* CI集成(CircleCI)
* 代码覆盖集成(codecov)

## 2019 年 3 月 25 日

iOS Places Monitor 1.0.0

iOS的地点监视器的初始版本。

地点监视器管理操作系统级位置API并直接与地点扩展通信。 安装这两个扩展后，客户可以在其应用程序中进行开箱即用的区域监控。 有关“地点监视器”的详细信息，请参阅“地 [点监视器”扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

## 2019 年 2 月 28 日

### 测试版

这是Places的第一个版本，这是一套工具，允许客户使用真实的位置数据丰富其用户的体验。 在第一个版本中，我们的主要用例是使移动应用程序能够检索自定义位置数据并通过Adobe Experience Platform Launch对该数据执行操作。

### 主要功能

以下是此版本的主要功能：

#### 地点UI

我们发布了管理UI，您可以在其中查看和管理您的兴趣点(POI)。 您还可以将POI组织到库中。 除了标准元数据（如城市、州／省和类别）之外，我们还支持向POI添加自定义元数据的功能。

* 要查看地点UI，请转到 [https://places.adobe.com](https://places.adobe.com)。
* 要开始使用Places UI，请参阅快 [速入门](/help/getting-started.md)。

#### 地点扩展

使用Places Extension，您可以将Places库添加到移动应用程序并对其POI执行操作。 使用Experience Platform Launch中的规则构建器，您可以触发用户进入和退出POI时触发的操作。

在“地点”扩展中：

* 您可以选择要包含在应用程序中的POI库。
* 在POI进入或退出时触发的规则事件。
* 创建指向用户当前POI的数据元素。

有关“地点”扩展的详细信息，请参阅“地 [点”扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

#### Places API

您可以使用Places API执行以下操作：

* 允许开发人员填充和更新其POI列表。
* 构建您自己的UI或与现有POI数据库集成。
* 使用Places API批处理端点可批量导入POI。

   Python实用程序随API提供。

有关Places API的详细信息，请参阅 [Places web服务](/help/places-web-service-api/places-web-services.md)。

### 即将推出

#### Analytics 集成

将更新Analytics扩展，以在用户在POI（被动调用）中时自动将位置上下文数据从Places数据库添加到所有传出Analytics调用。 此更新还允许创建规则，以在POI进入或退出（活动呼叫）时直接触发Analytics跟踪调用。

