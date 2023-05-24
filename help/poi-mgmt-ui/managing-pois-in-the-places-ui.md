---
title: 管理现有POI
description: 在Places服务UI中，您可以编辑、删除或筛选现有POI。
exl-id: a4cf28ae-1e3c-4724-bca3-ac1d0cd6da09
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 6%

---

# 管理现有POI {#managing-existing-pois}

通过使用Places UI，可在Places数据库中创建和管理POI和库。

## 编辑POI

1. 使用您的Adobe ID登录Places。
1. 使用您的Adobe ID登录Places服务。
1. 单击右上方的项目符号列表图标。
1. 找到要编辑的POI。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL 查看详细信息]**.
1. 更新信息并单击 **[!UICONTROL 保存]**.

## 删除POI

1. 使用您的Adobe ID登录Places。
1. 使用您的Adobe ID登录Places服务。
1. 单击右上方的项目符号列表图标。
1. 找到要删除的POI。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL 删除]**.

## 按城市、州/省、国家/地区或元数据筛选POI

![筛选POI](/help/assets/filter_poi.png)

1. 使用您的Adobe ID登录Places服务UI。
1. 单击右上方的筛选图标。
1. 您可以通过以下方式之一过滤POI：

   * 按库：

      a.选择库。

   * 按属性：

      a.在属性下拉列表中，选择 **[!UICONTROL 国家/地区]**， **[!UICONTROL 状态]**，或 **[!UICONTROL 城市]**.

      b.在下一行，输入一个值。

      例如，您可以选择 **[!UICONTROL 状态]** 和类型 **[!UICONTROL 加利福尼亚]**.

   * 使用元数据：

      a.输入键和值。

## 定义地理围栏POI

地理围栏是一种POI，它是在数据库中根据以下键定义的：

| 键 | 描述 | 必需？ |
| :--- | :--- | :--- |
| ID | 分配给每个POI的唯一标识符 | 是 |
| 名称 | 为POI指定的友好名称。 | 是 |
| 库 | 必须为每个POI分配一个组织库。 | 是 |
| 半径 | POI的半径（以米为单位）。 | 是 |
| 图标 | 协助实现POI的可视化。 | 是（分配的默认值） |
| 颜色 | 协助实现POI的可视化。 | 是（分配的默认值） |
| 类别 | 分配在所有库中的所有POI中通用的类别的通用框架。 | 否 |
| 地址 | 街道地址. | 否 |
| 城市 | POI市。 | 否 |
| 州/省/地区 | POI所在州或地区。 | 否 |
| 国家/地区 | 目标点所在的国家/地区。 | 否 |
| 纬度 | POI中心的纬度坐标。 | 是 |
| 经度 | POI中心的经度坐标。 | 是 |
| 元数据 | 可分配给POI的自定义键值对。 此元数据允许您跨库为每个库分组POI，以便在下游工作流中使用规则和过滤器，例如当有人使用“类型=竞争对手”输入POI时发送推送通知，从而简化未来的工作流。 | 否 |
