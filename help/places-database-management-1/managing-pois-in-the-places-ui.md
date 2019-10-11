---
title: 在地点UI中管理POI
seo-title: 在地点UI中管理POI
description: 使用Places UI管理POI。
seo-description: 使用Places UI管理POI。
translation-type: tm+mt
source-git-commit: 01617e4e1658f92234803baf1e57282777d04b13

---


# 在地点UI中管理POI

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

## 创建目标点 (POI){#create-a-poi}

目标点(POI)是地图上您感兴趣的位置或点。 酒店可包括咖啡馆、餐馆等场所。

1. 使用您的Adobe ID登录到Adobe Places。
2. 在右上方，单击与项目符号列表类似的图标，然后单击 **[!UICONTROL New]**。
3. 键入POI的名称。
4. 选择或添加库。
5. 输入或选择半径。

   a.为POI选择一个图标。
b.b.为图标选择一种颜色。

6. 展开该 **[!UICONTROL Location]** 部分。

   a.键入地址。

   b.键入城市。

   c.键入状态的名称。

   d.键入国家／地区的名称。

   e.选择或输入纬度或经度。

   f.单击 **[!UICONTROL Drop Pin on Map]**。

7. 展开该 **[!UICONTROL Metadata]** 部分并单击 **[!UICONTROL Add Metadata]**。

   a.键入键名。

   b.键入键值。

8. 单 **[!UICONTROL Confirm]** 击，然后 **[!UICONTROL  Save]**。

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

