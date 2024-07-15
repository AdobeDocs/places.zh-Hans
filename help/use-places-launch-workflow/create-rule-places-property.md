---
title: 为Places Service属性创建规则
description: Places SDK可跟踪当前位置，监控当前位置周围配置的POI，并跟踪这些POI的进入和退出事件。
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 12%

---

# 创建登入和退出规则 {#create-entry-exit-rules}

通过在移动应用程序中安装Places扩展和区域监控解决方案，您可以在Adobe Experience Platform Launch中创建触发或条件性位置数据（包括位置进入和退出事件）的规则。

## 规则

您可以配置规则，该规则由事件、条件和操作组成。 每个规则由以下部分组成：

* 一个或多个事件
* （可选）条件
* 一个或多个操作

### Places服务事件

Places Service提供了以下事件，您可以在其上运行规则：

* **输入POI**，当您的客户进入您配置的POI时，Places SDK会触发该设置。
* **退出POI**，当您的客户退出您配置的POI时，由Places SDK触发。

### Places服务条件

条件定义了与事件关联的数据或该实例上扩展的共享状态必须满足哪些标准才能执行操作。 例如，您可以设置一个条件，以仅对旧金山市的咖啡店的条目触发操作。

Places SDK将维护以下状态：

* 当前POI，是指您的客户当前所在的POI。
* 上次退出的POI，是指您的客户退出的最新POI。
* 上次输入的POI，是指您的客户输入的最新POI。

每个POI都包含以下数据元素：

* ID
* 名称
* 纬度/经度
* 半径
* 元数据，例如城市、国家/地区、州/省、类别

### 操作

操作定义应用程序将执行哪些操作，以响应触发事件的规则符合条件。 例如，当客户进入您的POI时，您可以配置欢迎消息以在其移动设备上显示。

## 创建规则：示例

>[!CAUTION]
>
>此示例假设您已经创建了包含美国所有咖啡馆的 POI 库。有关创建POI和库的更多信息，请参阅[创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md)和&#x200B;*在[管理多个库](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html)中创建库*。

以下过程是创建规则的示例，该规则会在您进入旧金山的咖啡店时将帖子发送回Slack。

事件、条件和操作通过以下方式进行定义：

* **事件**： Places进入事件。
* **条件**：**当前 POI** 的城市是旧金山
* **操作**：发送回发，以Slack客户输入的咖啡馆名称。

### 先决条件

在创建规则之前，必须在Adobe Experience Platform Launch中创建数据元素。 数据元素会自动在回发消息中填充有关目标点(POI)的必要信息。

要在Experience Platform Launch中创建数据元素，请执行以下操作：

1. 单击&#x200B;**数据元素**&#x200B;选项卡。
1. 单击&#x200B;**添加数据元素**。
1. 键入名称，例如&#x200B;**当前咖啡店名称**。
1. 在&#x200B;**扩展**&#x200B;下拉列表中，选择&#x200B;**位置 — Beta**。
1. 在&#x200B;**数据元素**&#x200B;中，选择&#x200B;**城市**。
1. 在右窗格中，选择&#x200B;**当前POI**。
1. 单击&#x200B;**保存**。

### 在Experience Platform Launch中为Places服务创建规则

![创建规则](/help/assets/placesrule.png)

1. 在 Experience Platform Launch 中，单击&#x200B;**[!UICONTROL 规则]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL 添加规则]**。
1. 键入规则的名称，例如&#x200B;**[!UICONTROL SF]**&#x200B;中咖啡店的跟踪条目。

### 创建事件

1. 在“事件”部分中，单击&#x200B;**[!UICONTROL +添加]**。 事件决定您希望规则触发的时间。
1. 在&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 位置 — Beta]**。
1. 在&#x200B;**[!UICONTROL 事件类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 进入 POI]**。
1. 在&#x200B;**[!UICONTROL 名称]**&#x200B;中，输入事件的名称，例如，**[!UICONTROL 进入咖啡馆]**。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

### 创建条件

1. 在“条件”部分中，单击&#x200B;**[!UICONTROL +添加]**。 条件决定了采取操作必须符合哪些标准。
1. 在&#x200B;**[!UICONTROL 逻辑类型]**&#x200B;中，选择“常规”，该选项允许在满足条件时执行操作。
1. 在&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 位置 — Beta]**。
1. 在&#x200B;**[!UICONTROL 条件类型]**&#x200B;中，选择&#x200B;**[!UICONTROL 城市]**。
1. 键入条件名称，例如&#x200B;**[!UICONTROL SF]**&#x200B;中的咖啡馆。
1. 在右侧窗格中，单击&#x200B;**[!UICONTROL 当前 POI]**，然后在下拉列表中，选择&#x200B;**[!UICONTROL 旧金山]**&#x200B;作为您的城市之一。
1. 单击&#x200B;**[!UICONTROL 保留更改]**。

### 创建操作

1. 在&#x200B;**[!UICONTROL 操作]**&#x200B;部分中，单击&#x200B;**[!UICONTROL +添加]**。
1. 在&#x200B;**[!UICONTROL 扩展]**&#x200B;下拉列表中，保留默认的&#x200B;**[!UICONTROL 移动核心]**&#x200B;选项。
1. 选择操作类型，例如&#x200B;**[!UICONTROL 发送回发]**。

   a.在&#x200B;**[!UICONTROL URL]**&#x200B;中，键入Slack的回发URL，例如`https://hooks.slack.com/services/`。

   b.要发送帖子正文，请选中&#x200B;**[!UICONTROL 添加Post正文]**&#x200B;复选框。

   c.在&#x200B;**[!UICONTROL Post正文]**&#x200B;中，添加帖子正文，例如： `{ "text": "A customer has entered" }`

   c.键入内容类型，例如&#x200B;**[!UICONTROL application/json]**。

   d.选择一个超时值，例如&#x200B;**[!UICONTROL 5]**。

1. 单击&#x200B;**[!UICONTROL 保留更改]**。

### Publish规则

1. 要激活规则，您必须发布它。 有关在Experience Platform Launch中发布规则的详细信息，请参阅[发布](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html)。

### 在进入和退出之外思考

使用Places服务地理围栏进入和退出来触发Experience Platform Launch中的规则具有惊人的强大功能，但您也可以使用位置数据作为触发其他事件的条件。 例如，您可以根据应用程序内的特定trackAction调用事件，准备好触发移动设备核心跟踪操作事件触发器。 根据此事件，您可以在执行操作之前为事件设置其他位置条件。 例如，在发生`trackAction`购买事件时打开应用程序内调查，但如果用户的当前位置包含特定的Places服务元数据，则&#x200B;**仅**。

![创建条件](/help/assets/places-condition.png)
