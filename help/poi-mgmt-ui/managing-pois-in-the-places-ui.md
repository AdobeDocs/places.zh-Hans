---
title: 在地点UI中管理POI
seo-title: 在地点UI中管理POI
description: 使用Places UI管理POI。
seo-description: 使用Places UI管理POI。
translation-type: tm+mt
source-git-commit: fdfeb8c17820c4eb0eae249da39be4eebece22d3

---


# 在“地点”UI中管理现有POI

POI和库是使用Places UI在Places数据库中创建和管理的。

## 定义地理围栏POI

Geoffences是一种POI类型，它在数据库中使用以下键定义：

| 键 | 描述 | 必需? |
| :--- | :--- | :--- |
| ID | 分配给每个POI的唯一标识符 | 是 |
| 名称 | 给POI的易记名称 | 是 |
| 库 | 必须为每个POI分配一个用于组织的库 | 是 |
| 图标 | 协助实现POI的可视化 | 是（已指定默认值） |
| Color（颜色） | 协助实现POI的可视化 | 是（已指定默认值） |
| 类别 | 为所有库中的所有POI分配通用的类别框架 | 否 |
| 地址 | 街道地址 | 否 |
| 城市 | POI市 | 否 |
| 省/市/区 | POI的州或地区 | 否 |
| 国家/地区 | POI国家／地区 | 否 |
| 纬度 | POI中心的纬度坐标 | 是 |
| 经度 | POI中心的经度坐标 | 是 |
| 元数据 | 可分配给POI的自定义键值对。 此元数据允许您跨库对POI进行分组，以便每个POI在下游工作流程中使用规则和过滤器，例如，每当有人输入类型为“竞争对手”的POI时，发送推送通知，从而简化了将来的工作流程。 | 否 |


## 编辑POI

1. 使用您的Adobe ID登录到地点。
1. 使用您的Adobe ID登录Adobe Places Service。
1. 在右上方，单击与项目符号列表类似的图标。
1. 找到要编辑的POI。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL View Details]**。
1. 更新信息并单击 **[!UICONTROL Save]**。

## 删除POI

1. 使用您的Adobe ID登录到地点。
1. 使用您的Adobe ID登录Adobe Places Service。
1. 在右上方，单击与项目符号列表类似的图标。
1. 找到要删除的POI。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL Delete]**。

## 按城市、州／省、国家／地区或元数据过滤POI

1. 使用您的Adobe ID登录Adobe Places Service。
1. 在右上方，单击筛选图标。
1. 可以通过以下方式之一过滤POI:

   * 按库：

      a.选择库。

   * 按属性：

      a.在属性下拉列表中，选择 **[!UICONTROL Country]**、 **[!UICONTROL State]**&#x200B;或 **[!UICONTROL City]**。

      b.在下一行中，输入一个值。

      例如，您可以选择并 **[!UICONTROL State]** 键入 **[!UICONTROL California]**。

   * 使用元数据：

      a.输入键和值。
