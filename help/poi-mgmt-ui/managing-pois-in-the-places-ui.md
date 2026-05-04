---
title: 管理现有POI
description: 在Places服务UI中，您可以编辑、删除或过滤现有POI。
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
TQID: https://experienceleague.adobe.com/2VnBQ5-flpx5cyeK3n5b3AOKqnt7RVkdqFBXYa9O5Ys
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
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
source-wordcount: 408
ht-degree: 6%

---

# 管理现有POI {#managing-existing-pois}

通过使用Places UI，可在Places数据库中创建和管理POI和库。

## 编辑POI

1. 使用您的Adobe ID登录Places。
1. 使用您的Adobe ID登录Places服务。
1. 单击右上方的项目符号列表图标。
1. 找到要编辑的POI。
1. 单击&#x200B;**[!UICONTROL ...]**&#x200B;并选择&#x200B;**[!UICONTROL 查看详细信息]**。
1. 更新信息并单击&#x200B;**[!UICONTROL 保存]**。

## 删除目标点(POI)

1. 使用您的Adobe ID登录Places。
1. 使用您的Adobe ID登录Places服务。
1. 单击右上方的项目符号列表图标。
1. 找到要删除的POI。
1. 单击&#x200B;**[!UICONTROL ...]**&#x200B;并选择&#x200B;**[!UICONTROL 删除]**。

## 按城市、州/省、国家/地区或元数据筛选POI

![筛选POI](/help/assets/filter_poi.png)

1. 使用您的Adobe ID登录到Places服务UI 。
1. 单击右上方的筛选图标。
1. 您可以通过以下方式之一过滤POI：

   * 按库：

     答： 选择库。

   * 按属性：

     答： 在“属性”下拉列表中，选择&#x200B;**[!UICONTROL 国家/地区]**、**[!UICONTROL 省/州]**&#x200B;或&#x200B;**[!UICONTROL 城市]**。

     b. 在下一行中，输入一个值。

     例如，您可以选择&#x200B;**[!UICONTROL 州]**&#x200B;并键入&#x200B;**[!UICONTROL 加利福尼亚]**。

   * 包含元数据：

     答： 输入键和值。

## 定义地理围栏POI

地理围栏是一种POI，在数据库中由以下键定义：

| 键 | 描述 | 必需？ |
| :--- | :--- | :--- |
| ID | 分配给每个POI的唯一标识符 | 是 |
| 名称 | 为POI指定的友好名称。 | 是 |
| 库 | 必须为每个POI分配一个用于组织的库。 | 是 |
| 半径 | POI的半径（以米为单位）。 | 是 |
| 图标 | 协助实现POI的可视化。 | 是（已指定默认值） |
| 颜色 | 协助实现POI的可视化。 | 是（已指定默认值） |
| 类别 | 分配在所有库中的所有POI中通用的类别的通用框架。 | 否 |
| 地址 | 街道地址。 | 否 |
| 城市 | POI市。 | 否 |
| 州/省/地区 | POI所在州或地区。 | 否 |
| 国家/地区 | POI的国家/地区。 | 否 |
| 纬度 | POI中心的纬度坐标。 | 是 |
| 经度 | POI中心的经度坐标。 | 是 |
| 元数据 | 可分配给POI的自定义键值对。 此元数据允许您跨库为每个库分组POI，以便在下游工作流中使用规则和过滤器，例如当有人使用“类型=竞争对手”输入POI时发送推送通知，从而简化未来的工作流。 | 否 |
