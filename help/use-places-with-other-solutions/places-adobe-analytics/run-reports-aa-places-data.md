---
title: 将位置上下文添加到Analytics请求
description: 本节提供有关如何向Analytics请求添加位置上下文的信息。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# 将位置上下文添加到Analytics请求 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>本文档假定您已在应用程序中实施了Adobe Places。 有关实施Adobe Places的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places发送进入和退出事件后，您可以在Experience Platform Launch中创建规则，并将Places数据附加到所有Adobe Analytics事件。 要创建此类型的规则，请在启动项中选择您的属性，然后完成以下步骤：

## 1.创建规则

1. 在选项卡 **[!UICONTROL Rules]**上，单击**[!UICONTROL Create New Rule]**。

   请牢记以下信息：
   * 如果此属性没有现有规则，则 **[!UICONTROL Create New Rule]**按钮将位于屏幕中间。
   * 如果您的属性有规则， **[!UICONTROL Create New Rule]**则按钮将位于屏幕的右上方。

## 2.选择活动

1. 为您的规则指定一个有意义的名称，以便在您的规则列表中轻松识别该规则。

   在此示例中，该规则被命名 **[!UICONTROL Attach Places Data to Analytics Track Action Events]**。

1. 在部分 **[!UICONTROL Events]**下，单击**[!UICONTROL Add]**。

1. 从下 **[!UICONTROL Extension]**拉列表中，选择**[!UICONTROL Mobile Core]**。

1. 从下 **[!UICONTROL Event Type]**拉列表中，选择**[!UICONTROL Track Action]**。

现在，您可以确定要为此规则包含的触发器。 在此示例中，触发器基于所有调 `TrackAction` 用。 配置活动后，单击 **[!UICONTROL Keep Changes]**。

![“创建活动”](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.添加条件

>[!IMPORTANT]
>
>完成此过程，将条件添加到规则。 否则，请跳到下面 *的定义操作* 部分。

在此示例中，创建了一个条件，该条件导致规则仅为AT&amp;T客户触发。

1. 在部分 **[!UICONTROL Conditions]**下，单击**[!UICONTROL Add]**。

1. 从下 **[!UICONTROL Extension]**拉列表中，选择**[!UICONTORL  Mobile Core]**。

1. 从下 **[!UICONTROL Condition Type]**拉列表中，选择**[!UICONTROL Carrier Name]**。

1. 在右侧的窗口中，选中该复选 **[!UICONTROL AT&T]**框。

1. 单击 **[!UICONTROL Keep Changes]**。

![&quot;创建条件&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.定义操作

1. 在部分 **[!UICONTROL Actions]**下，单击**[!UICONTROL Add]**。

1. 从下 **[!UICONTROL Extension]**拉列表中，选择**[!UICONTROL Mobile Core]**。

1. 从下 **[!UICONTROL Action Type]**拉列表中，选择**[!UICONTROL Attach Data]**。

1. 在右侧窗格的字 **[!UICONTROL JSON Payload]**段中，键入要添加到此活动的数据。

1. 单击 **[!UICONTROL Keep Changes]**。

在右侧窗格中，您可以添加自由形式JSON有效负荷，该负荷将数据添加到SDK事件中，然后侦听此事件的扩展才能听到该事件。 在此示例中，某些上下文数据会添加到此事件中，然后Analytics扩展会处理它。 添加的上下文数据现在将位于传出的Analytics点击中。

在以下示例中， `poi.city` 将值 `poi.name` 添加到Analytics事件的上下文数据中。 新键的值由SDK在此事件处理时动态确定。

![“创建操作”](/help/assets/ad-setAction_use-analytics-data.png)

## 5.保存规则并重新构建您的属性

完成配置后，请验证您的规则是否如下图所示：

![“规则已经完成。”](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 单击 **[!UICONTROL Save]**

1. 重新构建您的启动项属性并将其部署到正确的环境。
