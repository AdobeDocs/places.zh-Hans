---
title: 将POI进入和退出数据发送到Analytics
description: 本节提供有关如何将POI进入和退出数据发送到Analytics的信息。
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 2%

---


# 将POI进入和退出数据发送到Analytics {#places-data-analytics}


>[!IMPORTANT]
>
>本节假定您已在应用程序中实施Places Service。 有关实施Places Service的详细信息，请参 [阅Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places Service发送进入和退出事件后，您可以在Experience Platform Launch中创建规则以将Places Service数据发送到Adobe Analytics。 要创建此类型的规则，请在启动项中选择您的属性，然后完成以下步骤：

## 1.创建规则

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   请牢记以下信息：

   * 如果此属性没有现有规则， **[!UICONTROL Create New Rule]** 则按钮将位于屏幕中间。
   * 如果您的属性有规 **[!UICONTROL Create New Rule]** 则，则按钮将位于屏幕右上方。

## 2.选择事件

1. 为规则键入有意义的名称。

   这样，规则在您的规则列表中就很容易识别。 在此示例中，将命名规则 **[!UICONTROL Send Data to Analytics]**。

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places Service]**。

1. 从下 **[!UICONTROL Event Type]** 拉列表中，选择 **[!UICONTROL Enter POI]**。

1. 单击 **[!UICONTROL Keep Changes]**。

   ![&quot;选择事件&quot;](/help/assets/pt-selectEvent.png)


## 3.添加条件

>[!IMPORTANT]
>
>完成此步骤，将条件添加到规则。 否则，跳到以 *下定义操作* 。

在此示例中，创建了一个条件，该条件仅在当前POI的名称等于时使规则触发 **[!UICONTROL My POI]**。

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places Service]**。

1. 从下 **[!UICONTROL Condition Type]** 拉列表中，选择 **[!UICONTROL Name]**。

1. 在右侧窗格的文本字段中，输入 **[!UICONTROL My POI]**。

1. 单击 **[!UICONTROL Keep Changes]**。

   ![&quot;设置条件&quot;](/help/assets/pt-setCondition.png)


## 4.定义活动

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Adobe Analytics]**。

1. 从下 **[!UICONTROL Action Type]** 拉列表中，选择 **[!UICONTROL Track]**。

1. 在右侧窗格中，添加要发送到Analytics的操作或状态。

   您还可以选择向此请求添加任何其他上下文数据。 请记住，您可以使用数据元素从SDK动态获取此数据。

1. 单击 **[!UICONTROL Keep Changes]**。

   在以下示例中，将向 `TrackAction` Analytics发送一个调用，其附加上下文数据 `poi.name` 与触发此条目事件的POI的名称相等：

   ![&quot;设置操作&quot;](/help/assets/pt-setAction.png)

## 5.保存规则并重新构建您的属性

完成配置后，请验证您的规则是否与下图类似：

![&quot;已创建规则&quot;](/help/assets/pt-ruleComplete.png)

1. 单击 **[!UICONTROL Save]**

1. 重新构建您的启动属性并将其部署到正确环境。
