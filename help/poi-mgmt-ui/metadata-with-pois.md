---
title: 将元数据与POI一起使用
description: 本节提供了有关如何将元数据与POI一起使用的信息和策略。
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
TQID: https://experienceleague.adobe.com/wTzahAs7MMSv0q-cEhkNObBpALUJXqDXlOcqjitezwY
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 0%

---

# 将元数据与POI一起使用的策略 {#using-metadata-pois}

在Places Service中，当您创建新的POI时，只需提供名称、半径、纬度和经度元素。 有关创建POI的详细信息，请参阅[创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md)。 但是，如果您只输入最小信息，则会错过创建附加值的机会。

可以通过多种方式使用POI元数据。 从POI管理的角度来看，添加元数据值可以帮助搜索或筛选可能包含数千个POI的列表。 为与POI相关的关键属性创建元数据可以在下游工作流中产生值。 例如，为每个资产创建POI的连锁酒店可能希望包含元数据，例如该酒店资产是否具有游泳池、餐厅和酒吧，或者它们是否具有健身设施。 此元数据可作为Analytics中的上下文数据包含在内，也可用于定向优惠或消息传送。

## Launch中的Places服务元数据

在Experience Platform Launch中，您可以为每个Places服务元数据字段创建对跟踪或消息传送目的很重要的数据元素。

健身房设施的![数据元素](/help/assets/gymfacility.png)

然后，您可以使用Analytics扩展创建一个操作，用于创建新点击，该点击包含您想要用作上下文数据的任何元数据。

健身房设施的![操作](/help/assets/Analytics-gym.png)

## Adobe Campaign中的应用程序内消息传送

元数据可用作本地通知和Adobe Campaign Standard中定义的应用程序内消息的过滤器。 将元数据用作过滤器可让您创建与实际位置更相关的消息。

在ACS中![过滤本地通知和应用程序内消息](/help/assets/ACS_gym_metadata.png)
