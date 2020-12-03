---
title: 向Analytics请求添加位置上下文
description: 本节提供有关如何向Analytics请求添加位置上下文的信息。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---


# 向Analytics请求添加位置上下文 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>此文档假定您已在应用程序中实现了Places Service。 有关实施Places Service的详细信息，请参 [阅Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places Service发送进入和退出事件后，您可以在Experience Platform Launch中创建规则，并将Places Service数据附加到所有Adobe Analytics事件。 要创建此类型的规则，请在启动项中选择您的属性，然后完成以下步骤：

## 1.创建规则

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   请牢记以下信息：
   * 如果此属性没有现有规则， **[!UICONTROL Create New Rule]** 则按钮将位于屏幕中间。
   * 如果您的属性有规 **[!UICONTROL Create New Rule]** 则，则按钮将位于屏幕右上方。

## 2.选择事件

1. 为规则指定一个有意义的名称，以便在规则的列表中容易识别它。

   在此示例中，将命名规则 **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**。

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Mobile Core]**。

1. 从下 **[!UICONTROL Event Type]** 拉列表中，选择 **[!UICONTROL Track Action]**。

现在，您可以确定要为此规则包含的触发器。 在此示例中，触发器基于所有调 `TrackAction` 用。 配置事件后，单击 **[!UICONTROL Keep Changes]**。

![“创建事件”](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.添加条件

>[!IMPORTANT]
>
>完成此过程，将条件添加到规则。 否则，跳到下面 *的定义操作* 部分。

在此示例中，创建了一个条件，该条件使规则仅为AT&amp;T客户触发。

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Mobile Core]**。

1. 从下 **[!UICONTROL Condition Type]** 拉列表中，选择 **[!UICONTROL Carrier Name]**。

1. 在右侧的窗口中，选中复选 **[!UICONTROL AT&T]** 框。

1. 单击 **[!UICONTROL Keep Changes]**。

![&quot;创建条件&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.定义活动

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Mobile Core]**。

1. 从下 **[!UICONTROL Action Type]** 拉列表中，选择 **[!UICONTROL Attach Data]**。

1. 在右侧窗格的字 **[!UICONTROL JSON Payload]** 段中，键入要添加到此事件的数据。

1. 单击 **[!UICONTROL Keep Changes]**。

在右侧窗格中，您可以添加自由形式JSON有效负荷，该负荷会向SDK事件添加数据，然后侦听此事件的扩展才能听到事件。 在此示例中，在Analytics扩展处理前，会先将一些上下文数据添加到此事件。 添加的上下文数据现在将位于传出的Analytics点击中。

在以下示例中， `poi.city` 将 `poi.name` 值添加到Analytics事件的上下文数据。 新密钥的值由SDK在此事件处理时动态确定。

![“创建操作”](/help/assets/ad-setAction_use-analytics-data.png)

## 5.保存规则并重新构建您的属性

完成配置后，请验证您的规则是否与下图类似：

![“规则已经完成。”](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 单击 **[!UICONTROL Save]**

1. 重新构建您的启动属性并将其部署到正确环境。
