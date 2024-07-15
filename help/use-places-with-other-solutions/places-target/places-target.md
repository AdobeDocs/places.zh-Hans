---
title: Adobe Target
description: 此部分提供有关如何将Places服务与Adobe Target结合使用的信息。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 1%

---

# 将Places服务与Adobe Target结合使用 {#places-target}

本文档假设您在应用程序中实施了Places扩展。 如果您需要实施Places扩展的帮助，请参阅[Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places扩展发送登入和退出事件后，您可以利用Launch中的规则，将Places服务数据附加到Adobe Target SDK事件。 在Launch中选择所需的属性后，可通过完成以下任务来创建此类规则：

## 1.创建规则

1. 在&#x200B;**[!UICONTROL 规则]**&#x200B;选项卡上，单击&#x200B;**[!UICONTROL 创建新规则]**。

   请牢记以下信息：

   * 如果您没有此属性的现有规则，则按钮将位于屏幕中间。
   * 如果您的资产具有规则，则按钮将位于屏幕的右上角。

## 2.选择事件

1. 为规则提供一个有意义的名称，以便在规则列表中可轻松识别该规则。

   在此示例中，规则名为&#x200B;**[!UICONTROL 将Places服务数据附加到请求的目标内容]**。

1. 在&#x200B;**[!UICONTROL 事件]**&#x200B;部分下，单击&#x200B;**[!UICONTROL 添加]**。
1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL Adobe Target]**。
1. 从&#x200B;**[!UICONTROL 事件类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 请求的内容]**。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

![添加事件](/help/assets/ad-setEvent_target.png)

## 3.添加条件

>[!IMPORTANT]
>
>如果要向规则添加条件，请完成此步骤。 否则，请跳至下面的&#x200B;*定义操作*。

在以下示例中，创建了一个条件，该条件会导致规则仅对已启动应用程序五次或更多次的用户触发。

1. 在&#x200B;**[!UICONTROL 条件]**&#x200B;部分下，单击&#x200B;**[!UICONTROL 添加]**。
1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 移动核心]**。
1. 从&#x200B;**[!UICONTROL 条件类型]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL 启动项]**。
1. 在右侧窗格中，修改下拉列表和数字控件，以使条件为&#x200B;**[!UICONTROL 用户已启动大于或等于5次]**。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

![添加条件](/help/assets/ad-setCondition_target.png)

## 4.定义活动

1. 在&#x200B;**[!UICONTROL 操作]**&#x200B;部分下，单击&#x200B;**[!UICONTROL 添加]**。
1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 移动核心]**。
1. 从&#x200B;**[!UICONTROL 操作类型]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL 附加数据]**。
1. 在右侧窗格的&#x200B;**[!UICONTROL JSON有效负载]**&#x200B;字段中，键入将添加到此事件的数据。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

在右侧窗格中，您可以添加一个自由格式JSON有效负载，该有效负载会在侦听此事件的扩展聆听数据之前将数据添加到SDK事件。

在以下示例中，将为Target事件中处理的每个请求的&#x200B;**[!UICONTROL mboxparameters]**&#x200B;添加`poiCity`和`poiName`值。 新键的值在此事件处理时由SDK动态确定。

>[!TIP]
>
>此JSON有效负载对`request`对象使用特殊表示法。 在原始事件中，`request`是匿名对象的数组。 当使用附加数据将数据附加到数组中的所有对象时，已知包含数组的键上的`[*]`表示法会导致有效负载应用于该数组中的所有对象。
>
>对于`request`数组&#x200B;_中的每个对象，`request[*]`的表示法可以大声读为_。

![定义操作](/help/assets/ad-setAction-target.png)

## 5.保存规则并重新构建您的资产

完成配置后，请验证您的规则是否类似于以下图像：

![已完成规则](/help/assets/ad-ruleComplete-target.png)

1. 单击&#x200B;**[!UICONTROL 保存]**
1. 重新构建Launch资产并将其部署到正确的环境。
