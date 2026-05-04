---
title: Adobe Target
description: 此部分提供有关如何将Places服务与Adobe Target结合使用的信息。
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
TQID: https://experienceleague.adobe.com/WsfkEJD0mN5aYKETjcnqiC13dVe5NPYeKfOCTOK82uE
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 2%

---

# 将Places服务与Adobe Target结合使用 {#places-target}

本文档假设您在应用程序中实施了Places扩展。 如果您需要实施Places扩展的帮助，请参阅[Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md)。

在Places扩展发送登入和退出事件后，您可以利用Launch中的规则，将Places服务数据附加到Adobe Target SDK事件。 在Launch中选择所需的属性后，可通过完成以下任务来创建此类规则：

## &#x200B;1. 创建规则

1. 在&#x200B;**[!UICONTROL 规则]**&#x200B;选项卡上，单击&#x200B;**[!UICONTROL 创建新规则]**。

   请牢记以下信息：

   * 如果您没有此属性的现有规则，则按钮将位于屏幕中间。
   * 如果您的资产具有规则，则按钮将位于屏幕的右上角。

## &#x200B;2. 选择事件

1. 为规则提供一个有意义的名称，以便在规则列表中可轻松识别该规则。

   在此示例中，规则名为&#x200B;**[!UICONTROL 将Places服务数据附加到请求的目标内容]**。

1. 在&#x200B;**[!UICONTROL 事件]**&#x200B;部分下，单击&#x200B;**[!UICONTROL 添加]**。
1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL Adobe Target]**。
1. 从&#x200B;**[!UICONTROL 事件类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 请求的内容]**。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

![添加事件](/help/assets/ad-setEvent_target.png)

## &#x200B;3. 添加条件

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

## &#x200B;4. 定义操作

1. 在&#x200B;**[!UICONTROL 操作]**&#x200B;部分下，单击&#x200B;**[!UICONTROL 添加]**。
1. 从&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 移动核心]**。
1. 从&#x200B;**[!UICONTROL 操作类型]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL 附加数据]**。
1. 在右侧窗格的&#x200B;**[!UICONTROL JSON有效负载]**&#x200B;字段中，键入将添加到此事件的数据。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

在右侧窗格中，您可以添加一个自由格式JSON有效负载，该有效负载会在侦听此事件的扩展收到数据之前将数据添加到SDK事件。

在以下示例中，将为Target事件中处理的每个请求的&#x200B;**[!UICONTROL mboxparameters]**&#x200B;添加`poiCity`和`poiName`值。 新键的值在此事件处理时由SDK动态确定。

>[!TIP]
>
>此JSON有效负载对`request`对象使用特殊表示法。 在原始事件中，`request`是匿名对象的数组。 当使用附加数据将数据附加到数组中的所有对象时，已知包含数组的键上的`[*]`表示法会导致有效负载应用于该数组中的所有对象。
>
>对于`request`数组&#x200B;_中的每个对象，`request[*]`的表示法可以大声读为_。

![定义操作](/help/assets/ad-setAction-target.png)

## &#x200B;5. 保存规则并重新构建您的资产

完成配置后，请验证您的规则是否类似于以下图像：

![已完成规则](/help/assets/ad-ruleComplete-target.png)

1. 单击&#x200B;**[!UICONTROL 保存]**
1. 重新构建Launch资产并将其部署到正确的环境。
