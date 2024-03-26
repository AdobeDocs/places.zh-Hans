---
title: Places Service
description: Places Service是了解移动用户参与的重要上下文。 通过使用此上下文，移动应用程序开发人员可以增强应用程序设计，并使其成为更加个性化和引人入胜的体验。
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 9%

---

# Places Service {#home}

位置是了解移动用户并与之互动的重要上下文。 通过使用此上下文，移动应用程序开发人员可以增强应用程序设计，并使其成为更加个性化和引人入胜的体验。

Places Service(以前称为Adobe Experience Platform位置服务)是一种地理位置服务，通过此服务，具有位置感知功能的移动设备应用程序可以使用丰富且易于使用的SDK接口(灵活的关注点(POI)数据库随附)，了解位置背景信息。

Places Service允许您实现以下目标：

* 创建和管理可与其他Adobe Experience Cloud解决方案结合使用的POI数据库。
* 将自定义元数据附加到POI，以通过指定其他属性使其更丰富、更有意义。
* 在地图上可视化目标点，以便轻松了解空间上下文并添加/编辑元数据属性。
* 在Adobe Experience Platform Launch中配置SDK，以定义位置触发的规则和基于元数据的条件。
* 减少需要编写以监视设备位置的代码，并使用Places扩展自动触发特定于位置的规则。

这样，您就可以在位置信号很重要的时间和地点实时采取相应措施。 正确的上下文可提供更丰富的移动参与体验。

以下是您可以使用地标的一些方式：

* 当有人进入POI时发送实时通知， *“嘿……欢迎来到体育场。”*
* 分析您自己的商店与竞争对手商店的客流量。
* 通过使用具有位置上下文的受众配置文件根据离线行为对受众进行分段。
* 在相关时定位具有店内体验的用户。

## Places服务组件

Places Service包含以下组件：

* **Web服务**

  您可以使用Places REST API创建和管理POI。 有关REST API的更多信息，请参阅 [管理库](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) 和 [管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI管理界面**

  在地图上可视化POI以了解空间上下文并添加/编辑POI及其自定义元数据。

* **Places扩展**

  多平台移动API接口，用于集成移动应用程序中的位置上下文。 有关SDK的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Launch规则**

  地理智能Launch规则，允许您通过进入和退出事件触发操作。 这些规则还允许您在条件中使用地理属性来个性化体验。

## 术语

以下是本文档中使用的一些常用术语：

* A **目标点(POI)** 是您的组织感兴趣的地理位置。

  您可以使用名称、半径、地址、类别和元数据标记等属性来定义POI。

* A **地理围栏** 是一种POI。

  此POI类型是由纬度和经度坐标定义的虚拟地理边界。

* A **beacon** 是一种POI。

  此POI类型是一种通过发出低功耗蓝牙信号来表示位置的物理设备。 未来版本中将提供Beacons支持。

* **库**&#x200B;是 POI 集合，POI 经过分组，可以轻松地将规则与一组 POI 关联起来，而不是一个 POI。

* An **扩展** 是在移动应用程序中集成Places SDK所需的Experience Platform Launch扩展。

  与其他Mobile SDK一起使用以将位置上下文添加到体验的扩展。

* **组织**&#x200B;是一个 Adobe 实体，用于在 Adobe Experience Cloud 中标识您的公司。

  通常，组织就是您的公司名称。 但是，公司可以有多个组织。 组织管理员可以配置组和用户，以及配置单点登录功能。

* **orgID** 是在 Adobe Experience Platform 中代表您组织的 ID。

  有关更多信息，请参阅 [查找您的组织ID](https://forums.adobe.com/thread/2339895).

* 此 **EXPERIENCE CLOUDID** 服务提供通用的永久性ID，用于在Experience Cloud的所有解决方案中标识您的访客。

  有关更多信息，请参阅[概述](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html?lang=zh-Hans)。

