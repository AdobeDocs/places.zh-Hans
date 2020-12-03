---
title: 将元数据与POI结合使用
description: 本节提供有关如何在POI中使用元数据的信息和策略。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# 在POI中使用元数据的策略 {#using-metadata-pois}

在Places Service中，当您创建新POI时，唯一必需的元素是名称、半径、纬度和经度。 有关创建POI的详细信息，请参 [阅创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。 但是，如果您只输入最低信息，您将错过创造额外价值的机会。

POI元数据可以通过各种方式使用。 从POI管理的角度来看，添加元数据值有助于搜索或筛选可能包含数千个POI的列表。 为与POI相关的关键属性创建元数据可在下游工作流中产生值。 例如，为每家酒店创建POI的酒店连锁可能希望包括元数据，如酒店有没有游泳池、餐厅和酒吧，或者他们有健身房设施。 此元数据可作为上下文数据包含在分析中，也可用于目标优惠或消息传递。

## 在启动项中放置服务元数据

在Experience Platform Launch中，您可以为每个Places Service元数据字段创建数据元素，这对于跟踪或消息传递很重要。

![健身设施的数据元素](/help/assets/gymfacility.png)

然后，您可以使用Analytics扩展创建一个操作，用于创建包含您希望作为上下文数据的任何元数据的新点击。

![健身设施的行动](/help/assets/Analytics-gym.png)

## Adobe Campaign中的应用程序内消息传递

元数据可用作在Adobe Campaign Standard定义的本地通知和应用程序内消息的过滤器。 使用元数据作为过滤器可以创建与实际位置相关的更相关的消息。

![在ACS中过滤本地通知和应用程序内消息](/help/assets/ACS_gym_metadata.png)