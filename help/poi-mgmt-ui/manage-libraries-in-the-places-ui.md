---
title: 在Places服务UI中管理库
description: 使用Places服务UI管理您的库。
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
TQID: https://experienceleague.adobe.com/PP7P3aOL3EKSEPJWedHtfyHRzbCueMtNS-J7Ao4mawo
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 434
ht-degree: 14%

---

# 管理库 {#manage-libraries-places-ui}

库是POI的集合。 在一个库中，最多可以有150,000个POI，并且每个Experience Cloud组织最多可以有100个库。

根据对组织最有用的内容，可以通过多种方式将POI整理到库中。 某些客户可能倾向于为每个移动设备应用程序创建单独的库，而其他客户可能使用库对特定类型的POI进行分组，例如咖啡馆、公园、酒店等。 例如，一家大型娱乐公司可能有一家图书馆，其中一家图书馆包含其户外场所，另一家图书馆则包含其零售店。 一个市政府可能有一个包含市内所有建筑的图书馆，另一个包含市内所有公园的图书馆。

库由以下内容定义：

| 键： | 描述： |
| :--- | :--- |
| ID | 创建时分配给库的唯一标识符 |
| 名称 | 为库指定的友好名称 |
| 排名 | 如果您的组织中没有重叠的地理围栏，则可以忽略这些排名。 如果存在重叠的 POI，我们建议您将每个地理围栏放在不同的库中，以便它们可以相对彼此进行加权。 用户一次只能处于一个地理围栏中。 <br><br>用户所在地理围栏的最高排名决定了其当前地理围栏成员资格。 如果有地理围栏具有相同的库排名，则最小的地理围栏是用户当前的地理围栏。 <br><br>SDK还能感知&#x200B;*上次进入*&#x200B;和&#x200B;*上次退出*&#x200B;的POI，因此您可以根据用户与POI的交互，完全控制您希望如何触发规则。 |

## 创建库

1. 使用您的Adobe ID登录Places 。
1. 单击右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理库]**。
1. 单击&#x200B;**[!UICONTROL 新建]**。
1. 键入名称。
1. 单击&#x200B;**[!UICONTROL 确认]**。

## 更改Places UI中库的排名

1. 使用您的Adobe ID登录到Places 。
1. 单击右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理库]**。
1. 单击库名称左侧的图标，然后将库拖至新排名。

## 重命名库

1. 使用您的Adobe ID登录到Places 。
1. 单击右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理库]**。
1. 找到要删除的库。
1. 单击&#x200B;**[!UICONTROL ...]**&#x200B;并选择&#x200B;**[!UICONTROL 重命名]**。
1. 更新名称并单击&#x200B;**[!UICONTROL 保存]**。

## 删除库

1. 使用您的Adobe ID登录到Places 。
1. 单击右上角的&#x200B;**[!UICONTROL ...]** > **[!UICONTROL 管理库]**。
1. 找到要删除的库。
1. 单击&#x200B;**[!UICONTROL ...]**&#x200B;并选择&#x200B;**[!UICONTROL 删除]**。
