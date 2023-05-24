---
title: 将POI登入和退出数据发送到Analytics
description: 本节提供了有关如何将POI登入和退出数据发送到Analytics的信息。
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---

# 将POI登入和退出数据发送到Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>本节假设您在应用程序中实施了Places服务。 有关实施Places服务的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

在Places服务发送进入和退出事件后，您可以在Experience Platform Launch中创建规则以将Places服务数据发送到Adobe Analytics。 要创建此类型的规则，请在Launch中选择您的资产并完成以下步骤：

## 1.创建规则

1. 在 **[!UICONTROL 规则]** 选项卡，单击 **[!UICONTROL 创建新规则]**.

   请牢记以下信息：

   * 如果您没有此资产的现有规则，则 **[!UICONTROL 创建新规则]** 按钮将位于屏幕中间。
   * 如果您的资产有规则，则 **[!UICONTROL 创建新规则]** 按钮将位于屏幕的右上方。

## 2.选择事件

1. 为您的规则键入一个有意义的名称。

   这样，规则便可以在规则列表中轻松识别。 在此示例中，将规则命名为 **[!UICONTROL 将数据发送到Analytics]**.

1. 在 **[!UICONTROL 事件]** 部分，单击 **[!UICONTROL 添加]**.

1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL Places Service]**.

1. 从 **[!UICONTROL 事件类型]** 下拉列表，选择 **[!UICONTROL 输入POI]**.

1. 单击 **[!UICONTROL Keep Changes]**.

   ![&quot;选择事件&quot;](/help/assets/pt-selectEvent.png)


## 3.添加条件

>[!IMPORTANT]
>
>完成此步骤可将条件添加到规则中。 否则，请跳至 *定义操作* 下面的。

在此示例中，创建了一个条件，该条件导致规则仅在当前POI的名称等于时触发 **[!UICONTROL 我的POI]**.

1. 在 **[!UICONTROL 条件]** 部分，单击 **[!UICONTROL 添加]**.

1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL Places Service]**.

1. 从 **[!UICONTROL 完成情况类型]** 下拉列表，选择 **[!UICONTROL 名称]**.

1. 在右侧窗格的文本字段中，输入 **[!UICONTROL 我的POI]**.

1. 单击 **[!UICONTROL Keep Changes]**.

   ![&quot;set a condition&quot;](/help/assets/pt-setCondition.png)


## 4.定义活动

1. 在 **[!UICONTROL 操作]** 部分，单击 **[!UICONTROL 添加]**.

1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL Adobe Analytics]**.

1. 从 **[!UICONTROL 操作类型]** 下拉列表，选择 **[!UICONTROL Track]**.

1. 在右侧窗格中，添加要发送到Analytics的操作或状态。

   您还可以选择将任何其他上下文数据添加到此请求。 请记住，您可以使用数据元素从SDK动态获取此数据。

1. 单击 **[!UICONTROL Keep Changes]**.

   在以下示例中， `TrackAction` 调用被发送到Analytics，其中包含的其他上下文数据 `poi.name` 等于触发此进入事件的POI的名称：

   ![&quot;set an action&quot;](/help/assets/pt-setAction.png)

## 5.保存规则并重建您的资产

完成配置后，请验证规则是否如下所示：

![&quot;已创建规则&quot;](/help/assets/pt-ruleComplete.png)

1. 单击&#x200B;**[!UICONTROL 保存]**

1. 重新构建Launch资产，并将其部署到正确的环境。
