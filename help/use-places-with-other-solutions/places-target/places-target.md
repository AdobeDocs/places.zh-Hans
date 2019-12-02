---
title: Adobe Target
seo-title: Adobe Target
description: 本节提供有关如何将位置服务与Adobe Target结合使用的信息。
seo-description: 本节提供有关如何将位置服务与Adobe Target结合使用的信息。
translation-type: tm+mt
source-git-commit: 4ee8adb73f6dec15030a160c27edbeca71d3507b

---


# 将位置服务与Adobe Target结合使用 {#places-target}

本文档假定您已在应用程序中实现了“地点”扩展。 如果您需要实施Places扩展的帮助，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在“地点”扩展发送进入和退出的事件后，您可以利用Launch中的“规则”将“地点”数据附加到Adobe Target SDK事件。 在启动项中选择所需的属性后，您可以通过完成以下任务来创建此类型的规则：

## 1.创建规则

1. 在选项卡 **[!UICONTROL Rules]** 上，单击 **[!UICONTROL Create New Rule]**。

   请牢记以下信息：

   * 如果此属性没有现有规则，则按钮将位于屏幕中间。
   * 如果您的属性有规则，则按钮将位于屏幕的右上角。

## 2.选择活动

1. 为您的规则指定一个有意义的名称，以便在您的规则列表中轻松识别该规则。

   在此示例中，该规则被命名 **[!UICONTROL Attach Places Data to Target Content Requested]**。

1. 在部分 **[!UICONTROL Events]** 下，单击 **[!UICONTROL Add]**。

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Adobe Target]**。

1. 从下 **[!UICONTROL Event Type]** 拉列表中，选择 **[!UICONTROL Content Requested]**。

1. 单击 **[!UICONTROL Keep Changes]**。

![添加活动](/help/assets/ad-setEvent_target.png)

## 3.添加条件

>[!IMPORTANT]
>
>如果要向规则中添加条件，请完成此步骤。 否则，请跳到以 *下定义操作* 。

在以下示例中，创建了一个条件，该条件使规则仅为启动应用程序五次或多次的用户触发。

1. 在部分 **[!UICONTROL Conditions]** 下，单击 **[!UICONTROL Add]**。

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Mobile Core]**。

1. 从下 **[!UICONTROL Condition Type]** 拉列表中，选择 **[!UICONTROL Launches]**。

1. 在右侧窗格中，修改下拉列表和数字控件，以便该条件读取 **[!UICONTROL User has launched the app greater than or equal to 5 times]**。

1. 单击 **[!UICONTROL Keep Changes]**。

![添加条件](/help/assets/ad-setCondition_target.png)

## 4.定义操作

1. 在部分 **[!UICONTROL Actions]** 下，单击 **[!UICONTROL Add]**。

1. 从下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Mobile Core]**。

1. 从下 **[!UICONTROL Action Type]** 拉列表中，选择 **[!UICONTROL Attach Data]**。

1. 在右侧窗格的字 **[!UICONTROL JSON Payload]** 段中，键入要添加到此活动的数据。

1. 单击 **[!UICONTROL Keep Changes]**。

在右侧窗格上，您可以添加自由形式JSON有效负荷，在侦听此事件的扩展收到该事件之前，将数据添加到SDK事件。

在以下示例中， `poiCity` 将值 `poiName` 添加到Target事 **[!UICONTROL mboxparameters]** 件中处理的每个请求中。 新键的值由SDK在该事件处理时动态确定。

>[!TIP]
>
>此JSON有效负荷对对象使用特殊记 `request` 号。 在原始事件中， `request` 是一组匿名对象。 使用“附加数据”将数据附加到数组中的所有对象时，已知包含数组的键上的记号会导致有效负荷应用于该数组中的所有对象。 `[*]`
>
>对于数 `request[*]` 组中的每个对象， _可以朗读的记号`request`。_

![定义操作](/help/assets/ad-setAction-target.png)

## 5.保存规则并重新构建您的属性

完成配置后，请验证您的规则是否如下图所示：

![完整规则](/help/assets/ad-ruleComplete-target.png)

1. 单击 **[!UICONTROL Save]**。

1. 重新构建您的启动项属性并将其部署到正确的环境。
