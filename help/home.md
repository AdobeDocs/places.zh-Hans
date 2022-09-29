---
title: Places Service
description: Places Service是了解移动用户参与度的重要上下文。 通过使用此上下文，移动设备应用程序开发人员可以增强应用程序设计，并使其成为更加个性化和引人入胜的体验。
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: c13da9ea3dc0cd574f2f9a496405867f7d36eae0
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 10%

---

# Places Service {#home}

位置是了解和吸引移动用户的重要上下文。 通过使用此上下文，移动设备应用程序开发人员可以增强应用程序设计，并使其成为更加个性化和引人入胜的体验。

Places Service以前称为Adobe Experience Platform位置服务，是一项地理位置服务，通过此服务，具有位置感知功能的移动设备应用程序可以使用丰富且易于使用的SDK界面(随附了灵活的目标点(POI)数据库)来了解位置上下文。

Places Service允许您实现以下目标：

* 创建并管理一个POI数据库，该数据库可以与其他Adobe Experience Cloud解决方案一起使用。
* 将自定义元数据附加到POI，以通过指定其他属性使其更丰富、更有意义。
* 在地图上可视化POI，以便轻松了解空间上下文并添加/编辑元数据属性。
* 在Adobe Experience Platform Launch中配置SDK以定义位置触发的规则和基于元数据的条件。
* 减少监视设备位置时需要写入的代码，并使用Places扩展自动触发特定于位置的规则。

这样，您就可以实时、何时、何地从位置信号中执行相关操作。 正确的上下文可提供更加丰富的移动参与体验。

以下是使用Places的一些方式：

* 当某人进入POI时发送实时通知， *“嘿……欢迎来到体育场。”*
* 分析您自己的商店与竞争对手商店的足部流量。
* 通过将受众配置文件与位置上下文结合使用，根据离线行为对受众进行分段。
* 根据需要，使用店内体验定位用户。

## Places Service组件

Places Service包含以下组件：

* **Web服务**

   您可以使用Places REST API创建和管理POI。 有关REST API的更多信息，请参阅 [管理库](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) 和 [管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI管理界面**

   在地图上可视化POI以了解空间上下文，并添加/编辑POI及其自定义元数据。

* **Places 扩展**

   用于在移动设备应用程序中集成位置上下文的多平台移动API界面。 有关SDK的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **启动规则**

   地理智能的Launch规则，允许您通过登入和退出事件触发操作。 规则还允许您在条件中使用地理属性来个性化体验。

* **Places Monitor扩展**

   多平台Mobile SDK，可嵌入到您的移动设备应用程序中，以自动监控用户的位置更改并触发Places规则。 有关更多信息，请参阅 [Places Monitor扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## 术语

以下是本文档中使用的一些常用术语：

* A **目标点(POI)** 是贵组织感兴趣的地理位置。

   您可以使用名称、半径、地址、类别和元数据标记等属性来定义POI。

* A **地理** 是一种POI类型。

   此POI类型是由经纬度坐标定义的虚拟地理边界。

* A **信标** 是一种POI类型。

   此POI类型是通过发出低功耗蓝牙信号来表示位置的物理设备。 信标支持即将推出。

* **库**&#x200B;是 POI 集合，POI 经过分组，可以轻松地将规则与一组 POI 关联起来，而不是一个 POI。

* 安 **扩展** 是在移动设备应用程序中集成Places SDK所需的Experience Platform Launch扩展。

   与其他Mobile SDK一起使用的扩展，用于向您的体验添加位置上下文。

* **组织**&#x200B;是一个 Adobe 实体，用于在 Adobe Experience Cloud 中标识您的公司。

   通常，组织是您的公司名称。 但是，公司可以拥有多个组织。 组织管理员可以配置组和用户，并配置单点登录功能。

* **orgID** 是在 Adobe Experience Platform 中代表您组织的 ID。

   有关更多信息，请参阅 [查找您的orgID](https://forums.adobe.com/thread/2339895).

* 的 **Experience CloudID** 服务提供了一个通用的永久性ID，用于在Experience Cloud的所有解决方案中标识您的访客。

   有关更多信息，请参阅[概述](https://docs.adobe.com/content/help/zh-Hans/id-service/using/intro/overview.html)。
