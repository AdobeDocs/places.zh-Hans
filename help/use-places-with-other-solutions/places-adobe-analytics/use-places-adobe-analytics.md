---
title: 将POI登入和退出数据发送到Analytics
description: 本节提供了有关如何将POI登入和退出数据发送到Analytics的信息。
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# 将POI登入和退出数据发送到Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>本节假设您在应用程序中实施了Places服务。 有关实施Places服务的详细信息，请参阅[Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places服务发送进入和退出事件后，您可以在Experience Platform Launch中创建规则以将Places服务数据发送到Adobe Analytics。 要创建此类型的规则，请在Launch中选择您的资产，并完成以下步骤：

## 1.创建规则

1. 在&#x200B;**[!UICONTROL 规则]**&#x200B;选项卡上，单击&#x200B;**[!UICONTROL 创建新规则]**。

   请牢记以下信息：

   * 如果没有此属性的现有规则，屏幕中间会显示&#x200B;**[!UICONTROL 创建新规则]**&#x200B;按钮。
   * 如果您的属性具有规则，则&#x200B;**[!UICONTROL 创建新规则]**&#x200B;按钮将位于屏幕的右上方。

## 2.选择事件

1. 为规则键入一个有意义的名称。

   这样，规则便可以在规则列表中轻松识别。 在此示例中，规则名为&#x200B;**[!UICONTROL 将数据发送到Analytics]**。

1. 在&#x200B;**[!UICONTROL 事件]**&#x200B;部分中，单击&#x200B;**[!UICONTROL 添加]**。

1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL Places服务]**。

1. 从&#x200B;**[!UICONTROL 事件类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 进入POI]**。

1. 单击&#x200B;**[!UICONTROL 保留更改]**。

   ![“选择事件”](/help/assets/pt-selectEvent.png)


## 3.添加条件

>[!IMPORTANT]
>
>完成此步骤以将条件添加到规则。 否则，请跳至下面的&#x200B;*定义操作*。

在此示例中，创建了一个条件，该条件导致规则仅在当前POI的名称等于&#x200B;**[!UICONTROL 我的POI]**&#x200B;时触发。

1. 在&#x200B;**[!UICONTROL 条件]**&#x200B;部分下，单击&#x200B;**[!UICONTROL 添加]**。

1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL Places服务]**。

1. 从&#x200B;**[!UICONTROL 条件类型]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL 名称]**。

1. 在右侧窗格的文本字段中，输入&#x200B;**[!UICONTROL 我的POI]**。

1. 单击&#x200B;**[!UICONTROL 保留更改]**。

   ![“设置条件”](/help/assets/pt-setCondition.png)


## 4.定义活动

1. 在&#x200B;**[!UICONTROL 操作]**&#x200B;部分下，单击&#x200B;**[!UICONTROL 添加]**。

1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL Adobe Analytics]**。

1. 从&#x200B;**[!UICONTROL 操作类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 跟踪]**。

1. 在右侧窗格中，添加要发送到Analytics的操作或状态。

   您还可以选择将任何其他上下文数据添加到此请求。 请记住，您可以使用数据元素从SDK动态获取此数据。

1. 单击&#x200B;**[!UICONTROL 保留更改]**。

   在以下示例中，向Analytics发送`TrackAction`调用，其`poi.name`的附加上下文数据等于触发此条目事件的POI的名称：

   ![“设置操作”](/help/assets/pt-setAction.png)

## 5.保存规则并重新构建您的资产

完成配置后，请验证您的规则是否类似于以下图像：

![“规则已创建”](/help/assets/pt-ruleComplete.png)

1. 单击&#x200B;**[!UICONTROL 保存]**

1. 重新构建Launch资产并将其部署到正确的环境。
