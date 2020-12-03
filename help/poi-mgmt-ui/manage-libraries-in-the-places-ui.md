---
title: 在Places Service UI中管理库
description: 使用Places Service UI管理库。
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 14%

---


# 管理库 {#manage-libraries-places-ui}

图书馆是POI的集合。 图书馆中最多可有150,000个POI，每个Experience Cloud组织最多可有100个库。

根据对您的组织最有用的信息，有多种方法将POI组织到库中。 一些客户可能希望为每个移动应用程序创建单独的库，而其他客户可能使用库对特定类型的POI（如咖啡店、公园、酒店等）进行分组。 例如，一家主要娱乐公司可能拥有一个图书馆，它包括一个图书馆的室外场所和另一个图书馆的零售店。 市政府可能会有一个图书馆，它包含市内所有建筑物，而另一个图书馆则包含市内所有公园。

库由以下各项定义：

| 密钥： | 描述: |
| :--- | :--- |
| ID | 创建时分配给库的唯一标识符 |
| 名称 | 给图书馆的友好名称 |
| 排名 | 如果您的组织中没有重叠的地理围栏，则可以忽略这些排名。 如果存在重叠的 POI，我们建议您将每个地理围栏放在不同的库中，以便它们可以相对彼此进行加权。用户一次只能处于一个地理围栏中。<br><br>用户所在地理围栏的最高排名决定了其当前地理围栏成员资格。如果有具有相同库排名的地理围栏，则最小的地理围栏就是用户当前的地理围栏。 <br><br>SDK还会识别“上 *次输入* ”和“ *上次退出* ”POI，因此您可以完全控制根据与POI的用户交互触发规则的方式。 |

## 创建库

1. 用您的Adobe ID登录Places。
1. 在右上方，单击 **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**。
1. 单击 **[!UICONTROL New]**。
1. 键入名称。
1. 单击 **[!UICONTROL Confirm]**。

## 在Places UI中更改库的等级

1. 使用您的Adobe ID登录到地点。
1. 在右上方，单击 **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**。
1. 单击库名称左侧的图标，并将库拖动到新等级。

## 重命名库

1. 使用您的Adobe ID登录到地点。
1. 在右上方，单击 **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**。
1. 找到要删除的库。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL Rename]**。
1. 更新名称并单击 **[!UICONTROL Save]**。

## 删除库

1. 使用您的Adobe ID登录到地点。
1. 在右上方，单击 **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**。
1. 找到要删除的库。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL Delete]**。

