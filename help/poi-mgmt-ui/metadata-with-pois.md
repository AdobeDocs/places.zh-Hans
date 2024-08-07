---
title: 将元数据与POI一起使用
description: 本节提供了有关如何将元数据与POI一起使用的信息和策略。
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# 将元数据与POI一起使用的策略 {#using-metadata-pois}

在Places Service中，当您创建新的POI时，只需提供名称、半径、纬度和经度元素。 有关创建POI的详细信息，请参阅[创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。 但是，如果您只输入最小信息，则会错过创建附加值的机会。

可以通过多种方式使用POI元数据。 从POI管理的角度来看，添加元数据值可以帮助搜索或筛选可能包含数千个POI的列表。 为与POI相关的关键属性创建元数据可以在下游工作流中产生值。 例如，为每个资产创建POI的连锁酒店可能希望包含元数据，例如该酒店资产是否具有游泳池、餐厅和酒吧，或者它们是否具有健身设施。 此元数据可作为Analytics中的上下文数据包含在内，也可用于定向优惠或消息传送。

## Launch中的Places服务元数据

在Experience Platform Launch中，您可以为每个Places服务元数据字段创建数据元素，这些元数据字段对于跟踪或消息传送非常重要。

健身房设施的![数据元素](/help/assets/gymfacility.png)

然后，您可以使用Analytics扩展创建一个操作，用于创建新点击，该点击包含您想要用作上下文数据的任何元数据。

健身房设施的![操作](/help/assets/Analytics-gym.png)

## Adobe Campaign中的应用程序内消息传送

元数据可用作本地通知和Adobe Campaign Standard中定义的应用程序内消息的过滤器。 将元数据用作过滤器可让您创建与实际位置更相关的消息。

在ACS中![过滤本地通知和应用程序内消息](/help/assets/ACS_gym_metadata.png)
