---
title: Adobe Experience Platform Location Service
seo-title: Adobe Experience Platform Location Service
description: '位置服务是了解移动用户参与度的重要上下文。 通过使用此环境，移动App开发人员可以增强App设计并使其成为更个性化、更具吸引力的体验。 '
seo-description: '位置服务是了解移动用户参与度的重要上下文。 通过使用此环境，移动App开发人员可以增强App设计并使其成为更个性化、更具吸引力的体验。 '
translation-type: tm+mt
source-git-commit: fd98249c01fba93250dc7111798c76f3c96c6e20

---


# 概述 {#home}

Adobe Experience Platform Location Service（位置服务）是了解移动用户参与度的重要环境。 通过使用此环境，移动App开发人员可以增强App设计并使其成为更个性化、更具吸引力的体验。 Places是一种地理位置服务，它使移动应用程序开发人员能通过使用丰富且易于使用的SDK界面以及灵活的兴趣点数据库(POI)来了解位置上下文。

位置服务允许您实现以下目标：

* 创建和管理可与其他Adobe Experience cloud解决方案结合使用的POI数据库。
* 将自定义元数据附加到POI，通过指定其他属性使其更丰富、更有意义。
* 可视化地图上的POI，以便轻松理解空间上下文并添加／编辑元数据属性。
* 在Adobe Experience Platform Launch中配置SDK以定义位置触发的规则和基于元数据的条件。
* 减少需要写入监视设备位置的代码，并使用Adobe位置监视器自动触发特定于位置的规则。

这样，您就可以从位置信号中实时、何时、何地采取相应的操作。 恰当的情境提供了更丰富的移动互动体验。

以下是使用地点的一些方式：

* 当某人进入POI时发送实时通 *知，“嘿……欢迎来到体育场。”*
* 分析您自己的商店与竞争对手商店的步行流量。
* 通过将受众档案与位置上下文结合使用，根据线下行为细分受众。
* 在相关时，以店内体验为目标。

## 位置服务用例

通过

## 位置服务组件

位置服务包括以下组件：

* **Places web服务**

   您可以使用Places REST API创建和管理POI。 有关REST API的详细信息，请参 [阅管理库](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) 和 [管理POI](/help/web-service-api/api-usage/manage-pois/manage-pois.md)。

* **位置服务UI**

   在地图上可视化POI以了解空间上下文并添加／编辑POI及其自定义元数据。

* **Places SDK**

   用于在移动应用程序中集成位置上下文的多平台移动API界面。 有关SDK的详细信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

* **地点规则**

   使用地理智能的启动规则，您可以触发具有进入和退出事件的操作。 这些规则还允许您在条件中使用地理属性来个性化体验。

* **地点监视器**

   多平台移动SDK，可嵌入到移动应用程序中以自动监视用户的位置更改并触发Places规则。 有关详细信息，请参 [阅“地点监视器”扩展](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)。

## 术语

以下是本文档中使用的一些常用术语：

* 目 **标点(POI)** 是您的组织感兴趣的地理位置。

   您可以使用名称、radius、地址、类别和元数据标记等属性定义POI。

* 地 **理科学** 是一种POI。

   此POI类型是由经纬度坐标定义的虚拟地理边界。

* 信 **标是** POI的一种类型。

   该POI类型是通过发射低功率蓝牙信号来表示位置的物理设备。 信标支持即将在未来版本中推出。

* 库 **是** POI的集合，这些POI被分组以将规则轻松附加到集合而不是一个POI。

* SDK扩 **展**，是Experience Platform Launch扩展，它是将Places SDK集成到移动应用程序中所必需的。

   与其他移动SDK一起使用的扩展，用于向体验添加位置上下文。

* 组 **织是** Adobe实体，可在Adobe Experience cloud中识别您的公司。

   通常，组织是您的公司名称。 但是，公司可以拥有多个组织。 组织管理员可以配置组和用户，并配置单点登录功能。

* orgID **是** Adobe Experience platform中代表您的组织的ID。

   有关详细信息，请参 [阅查找您的组织ID](https://forums.adobe.com/thread/2339895)。

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   有关详细信息，请参阅 [概述](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html)。