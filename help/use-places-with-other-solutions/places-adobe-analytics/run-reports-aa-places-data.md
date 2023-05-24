---
title: 将位置上下文添加到Analytics请求
description: 本节提供了有关如何将位置上下文添加到Analytics请求的信息。
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 2%

---

# 将位置上下文添加到Analytics请求 {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>本文档假设您在应用程序中实施了Places服务。 有关实施Places服务的更多信息，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

在Places服务发送进入和退出事件后，您可以在Experience Platform Launch中创建规则，并将Places服务数据附加到所有Adobe Analytics事件。 要创建此类型的规则，请在Launch中选择您的资产并完成以下步骤：

## 1.创建规则

1. 在 **[!UICONTROL 规则]** 选项卡，单击 **[!UICONTROL 创建新规则]**.

   请牢记以下信息：
   * 如果您没有此资产的现有规则，则 **[!UICONTROL 创建新规则]** 按钮将位于屏幕中间。
   * 如果您的资产有规则，则 **[!UICONTROL 创建新规则]** 按钮将位于屏幕的右上方。

## 2.选择事件

1. 为规则提供一个有意义的名称，以便轻松地在规则列表中识别它。

   在此示例中，将规则命名为 **[!UICONTROL 将Places服务数据附加到Analytics跟踪操作事件]**.

1. 在 **[!UICONTROL 事件]** 部分，单击 **[!UICONTROL 添加]**.

1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL 移动核心]**.

1. 从 **[!UICONTROL 事件类型]** 下拉列表，选择 **[!UICONTROL 跟踪操作]**.

现在，您可以确定要为此规则包含的触发器。 在此示例中，触发器基于 `TrackAction` 呼叫。 配置事件后，单击 **[!UICONTROL 保留更改]**.

![&quot;创建事件&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3.添加条件

>[!IMPORTANT]
>
>完成此过程可将条件添加到规则中。 否则，请跳至 *定义操作* 部分。

在此示例中，创建了一个条件，该条件导致规则仅针对AT&amp;T客户触发。

1. 在 **[!UICONTROL 条件]** 部分，单击 **[!UICONTROL 添加]**.

1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL 移动核心]**.

1. 从 **[!UICONTROL 完成情况类型]** 下拉列表，选择 **[!UICONTROL 运营商名称]**.

1. 在右侧窗口中，选择 **[!UICONTROL AT&amp;T]** 复选框。

1. 单击 **[!UICONTROL Keep Changes]**.

![&quot;创建条件&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4.定义活动

1. 在 **[!UICONTROL 操作]** 部分，单击 **[!UICONTROL 添加]**.

1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL 移动核心]**.

1. 从 **[!UICONTROL 操作类型]** 下拉列表，选择 **[!UICONTROL 附加数据]**.

1. 在右窗格的 **[!UICONTROL JSON有效负载]** 字段中，键入要添加到此事件的数据。

1. 单击 **[!UICONTROL Keep Changes]**.

在右侧窗格中，您可以添加一个自由格式的JSON有效负载，该有效负载会先将数据添加到SDK事件，然后侦听此事件的扩展才能听到该事件。 在此示例中，某些上下文数据会在Analytics扩展处理此事件之前添加到此事件。 添加的上下文数据现在将位于传出的Analytics点击中。

在以下示例中， `poi.city` 和 `poi.name` 值将添加到Analytics事件的上下文数据中。 新键的值在此事件处理时由SDK动态确定。

![&quot;创建操作&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5.保存规则并重建您的资产

完成配置后，请验证规则是否如下所示：

![“规则是完整的。”](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. 单击&#x200B;**[!UICONTROL 保存]**

1. 重新构建Launch资产，并将其部署到正确的环境。
