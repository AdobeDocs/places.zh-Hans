---
title: 在“地点”UI中管理库
seo-title: 在“地点”UI中管理库
description: 使用Places UI管理库。
seo-description: 使用Places UI管理库。
translation-type: tm+mt
source-git-commit: a2e30282789d9834e5c65502e28ddb25f3c55dfa

---


# Manage libraries {#manage-libraries-places-ui}

图书馆是POI的集合。 库中最多可有150,000个POI，每个Experience cloud组织最多可有100个库。

根据对您的组织最有用的内容，可以通过各种方式将POI组织到库中。 一些客户可能希望为每个移动应用程序创建单独的库，而其他客户可能使用库对特定类型的POI（如咖啡店、公园、酒店等）进行分组。 例如，一家大型娱乐公司可能有一个图书馆，其室外场所位于一个图书馆中，零售店位于另一个图书馆中。 一个市政府可能会有一个图书馆，它包含城市所有建筑物，另一个图书馆则包含城市所有公园。

库由以下各项定义：

| 键: | 描述: |
| :--- | :--- |
| ID | 创建时分配给库的唯一标识符 |
| 名称 | 给库的友好名称 |
| 排名 | 如果您的组织中没有重叠的地理围栏，则可以忽略这些排名。 如果存在重叠的POI，我们建议您将每个地理序列放在不同的库中，以便它们可以相对彼此进行加权。 用户一次只能处于一个地理围栏中。 <br><br>用户所在地理围栏的最高等级决定其当前地理围栏成员资格。 如果地序具有相同的库等级，则最小的地序是用户的当前地序。 <br><br>SDK还会识别“上次进入 ** ”和“上次退出 ** ”，因此您可以完全控制根据与POI的用户交互触发规则的方式。 |

## 创建库

1. 使用您的Adobe ID登录到地点。
1. 在右上方，单击 **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**。
1. 单击 **[!UICONTROL New]**。
1. 键入名称。
1. 单击 **[!UICONTROL Confirm]**。

## 在“地点”UI中更改库的等级

1. 使用您的Adobe ID登录到地点。
1. 在右上方，单击 **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**。
1. 单击库名称左侧的图标，并将库拖动到新排名。

## 重命名库

1. 使用您的Adobe ID登录到地点。
1. 在右上方，单击 **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**。
1. 找到要删除的库。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL Rename]**。
1. 更新名称并单击 **[!UICONTROL Save]**。

## 删除库

1. 使用您的Adobe ID登录到地点。
1. 在右上方，单击 **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**。
1. 找到要删除的库。
1. 单击 **[!UICONTROL ...]** 并选择 **[!UICONTROL Delete]**。

