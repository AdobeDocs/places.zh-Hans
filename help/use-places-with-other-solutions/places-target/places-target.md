---
title: Adobe Target
description: 本节提供了有关如何将Places服务与Adobe Target结合使用的信息。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 3%

---

# 将Places服务与Adobe Target结合使用 {#places-target}

本文档假设您在应用程序中实施了Places扩展。 如果您在实施Places扩展时需要帮助，请参阅 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md).

在Places扩展发送登录和退出事件后，您可以利用Launch中的规则，将Places服务数据附加到Adobe Target SDK事件。 在Launch中选择所需的属性后，您可以通过完成以下任务来创建此类规则：

## 1.创建规则

1. 在 **[!UICONTROL 规则]** 选项卡，单击 **[!UICONTROL 创建新规则]**.

   请牢记以下信息：

   * 如果您没有此属性的现有规则，则按钮将位于屏幕中间。
   * 如果您的资产有规则，则屏幕右上角会显示按钮。

## 2.选择事件

1. 为规则提供一个有意义的名称，以便轻松地在规则列表中识别它。

   在此示例中，将规则命名为 **[!UICONTROL 将Places服务数据附加到请求的目标内容]**.

1. 在 **[!UICONTROL 事件]** 部分，单击 **[!UICONTROL 添加]**.
1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL Adobe Target]**.
1. 从 **[!UICONTROL 事件类型]** 下拉列表，选择 **[!UICONTROL 已请求内容]**.
1. 单击 **[!UICONTROL Keep Changes]**.

![添加事件](/help/assets/ad-setEvent_target.png)

## 3.添加条件

>[!IMPORTANT]
>
>如果要向规则添加条件，请完成此步骤。 否则，请跳至 *定义操作* 下面的。

在以下示例中，创建了一个条件，该条件会导致规则仅对已启动应用程序五次或更多次的用户触发。

1. 在 **[!UICONTROL 条件]** 部分，单击 **[!UICONTROL 添加]**.
1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL 移动核心]**.
1. 从 **[!UICONTROL 完成情况类型]** 下拉列表，选择 **[!UICONTROL 启动次数]**.
1. 在右侧窗格中，修改下拉列表和数字控件，以使条件为 **[!UICONTROL 用户已启动应用程序超过或等于5次]**.
1. 单击 **[!UICONTROL Keep Changes]**.

![添加条件](/help/assets/ad-setCondition_target.png)

## 4.定义活动

1. 在 **[!UICONTROL 操作]** 部分，单击 **[!UICONTROL 添加]**.
1. 从 **[!UICONTROL 扩展]** 下拉列表，选择 **[!UICONTROL 移动核心]**.
1. 从 **[!UICONTROL 操作类型]** 下拉列表，选择 **[!UICONTROL 附加数据]**.
1. 在右窗格的 **[!UICONTROL JSON有效负载]** 字段中，键入要添加到此事件的数据。
1. 单击 **[!UICONTROL Keep Changes]**.

在右侧窗格中，您可以添加一个自由格式JSON有效负载，该有效负载会在侦听此事件的扩展聆听数据之前将数据添加到SDK事件。

在以下示例中， `poiCity` 和 `poiName` 值将添加到 **[!UICONTROL mboxparameters]** Target事件中处理的每个请求。 新键的值在此事件处理时由SDK动态确定。

>[!TIP]
>
>此JSON有效负载使用特殊表示法作为 `request` 对象。 在原来的事件中， `request` 是一个匿名对象的数组。 使用“附加数据”将数据附加到数组中的所有对象时， `[*]` 已知包含数组的键上的表示法会导致有效负载应用于该数组中的所有对象。
>
>表示法 `request[*]` 可以大声宣读为 _中每个对象的 `request` 数组_.

![定义操作](/help/assets/ad-setAction-target.png)

## 5.保存规则并重新构建您的资产

完成配置后，请验证规则是否如下所示：

![已完成规则](/help/assets/ad-ruleComplete-target.png)

1. 单击&#x200B;**[!UICONTROL 保存]**
1. 重新构建Launch资产，并将其部署到正确的环境。
