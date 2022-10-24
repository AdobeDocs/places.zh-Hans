---
title: 为Places Service资产创建规则
description: Places SDK会跟踪当前位置，监视当前位置周围配置的POI，并跟踪这些POI的登入和退出事件。
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 15%

---

# 创建登入和退出规则 {#create-entry-exit-rules}

在移动应用程序中安装Places扩展和区域监控解决方案后，您可以在Adobe Experience Platform Launch中创建触发的规则，或者设置位置数据（包括位置登入和退出事件）的条件。

## 规则

您可以配置规则，该规则由事件、条件和操作组成。 每个规则都由以下部分组成：

* 一个或多个事件
* （可选）条件
* 一个或多个操作

### Places Service事件

Places Service提供了以下事件，您可以在其上运行规则：

* **进入POI**，由Places SDK在客户进入您配置的POI时触发。
* **退出POI**，由Places SDK在客户退出您配置的POI时触发。

### Places服务条件

条件定义了要执行操作，与事件关联的数据或该实例中扩展的共享状态必须满足的条件。 例如，您可以设置一个条件，以仅在旧金山市对进入咖啡馆的条目触发操作。

Places SDK维护以下状态：

* 当前POI，指客户当前所在的POI。
* 上次退出POI，指客户退出的最近POI。
* 上次输入的POI，指客户输入的最新POI。

每个POI都包含以下数据元素：

* ID
* 名称
* 纬度/经度
* 半径
* 元数据，例如城市、国家/地区、州、类别

### 操作

操作可定义应用程序将执行哪些操作来响应触发事件的满足规则条件。 例如，当客户进入POI时，您可以配置欢迎消息以在其移动设备上显示。

## 创建规则：示例

>[!CAUTION]
>
>此示例假设您已经创建了包含美国所有咖啡馆的 POI 库。有关创建POI和库的更多信息，请参阅 [创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md) 和 *创建库* in [管理多个库](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

以下过程是如何创建规则的示例，当您进入旧金山的咖啡馆时，该规则会将帖子发送回Slack。

事件、条件和操作通过以下方式进行定义：

* **事件**:Places登入事件。
* **条件**：**当前 POI** 的城市是旧金山
* **操作**:发送回发以Slack客户输入的咖啡店的名称。

### 先决条件

在创建规则之前，必须在Adobe Experience Platform Launch中创建数据元素。 数据元素会自动在回发消息中填充有关您的POI的必要信息。

在Experience Platform Launch中创建数据元素：

1. 单击 **数据元素** 选项卡。
1. 单击 **Add Data Element**.
1. 键入一个名称，例如 **当前咖啡店名称**.
1. 在 **扩展** 下拉列表中，选择 **Places — 测试版**.
1. 在&#x200B;**数据元素**&#x200B;中，选择&#x200B;**城市**。
1. 在右侧窗格中，选择 **当前POI**.
1. 单击&#x200B;**保存**。

### 在Experience Platform Launch中为Places Service创建规则

![创建规则](/help/assets/placesrule.png)

1. 在 Experience Platform Launch 中，单击&#x200B;**[!UICONTROL 规则]**&#x200B;选项卡。
1. 单击 **[!UICONTROL Add Rule]**.
1. 键入规则的名称，例如 **[!UICONTROL 在SF中跟踪咖啡店的入口]**.

### 创建事件

1. 在事件部分中，单击 **[!UICONTROL +添加]**. 事件可决定您希望规则何时触发。
1. 在 **[!UICONTROL 扩展]** 下拉列表中，选择 **[!UICONTROL Places — 测试版]**.
1. 在&#x200B;**[!UICONTROL 事件类型]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 进入 POI]**。
1. 在&#x200B;**[!UICONTROL 名称]**&#x200B;中，输入事件的名称，例如，**[!UICONTROL 进入咖啡馆]**。
1. 单击 **[!UICONTROL Keep Changes]**.

### 创建条件

1. 在条件部分中，单击 **[!UICONTROL +添加]**. 这些条件决定了必须满足哪些标准才能执行操作。
1. 在&#x200B;**[!UICONTROL 逻辑类型]**&#x200B;中，选择“常规”，该选项允许在满足条件时执行操作。
1. 在 **[!UICONTROL 扩展]** 下拉列表中，选择 **[!UICONTROL Places — 测试版]**.
1. 在&#x200B;**[!UICONTROL 条件类型]**&#x200B;中，选择&#x200B;**[!UICONTROL 城市]**。
1. 键入条件名称，例如 **[!UICONTROL SF咖啡店]**.
1. 在右侧窗格中，单击&#x200B;**[!UICONTROL 当前 POI]**，然后在下拉列表中，选择&#x200B;**[!UICONTROL 旧金山]**&#x200B;作为您的城市之一。
1. 单击 **[!UICONTROL Keep Changes]**.

### 创建操作

1. 在 **[!UICONTROL 操作]** ，单击 **[!UICONTROL +添加]**.
1. 在 **[!UICONTROL 扩展]** 下拉列表中，保留默认 **[!UICONTROL 移动核心]** 选项。
1. 选择操作类型，例如 **[!UICONTROL 发送回发]**.

   a.在 **[!UICONTROL URL]**，则键入回发URL以进行Slack，例如 `https://hooks.slack.com/services/`.

   b.要发送帖子正文，请选择 **[!UICONTROL 添加帖子正文]** 复选框。

   c.输入 **[!UICONTROL 帖子正文]**，添加帖子正文，例如： `{ "text": "A customer has entered" }`

   c.键入内容类型，例如 **[!UICONTROL application/json]**.

   d.选择一个超时值，例如 **[!UICONTROL 5]**.

1. 单击 **[!UICONTROL Keep Changes]**.

### 发布规则

1. 要激活规则，您必须发布该规则。 有关在Experience Platform Launch中发布规则的更多信息，请参阅 [发布](https://docs.adobe.com/content/help/zh-Hans/launch/using/reference/publish/overview.html).

### 超越进出的思考

在Experience Platform Launch中使用Places Service地理围栏条目和退出来触发规则功能非常强大，但您也可以将位置数据用作触发其他事件的条件。 例如，您的应用程序中可能有一个“移动核心跟踪操作”事件触发器，该触发器可以根据特定的trackAction调用事件进行触发。 根据此事件，您可以在执行操作之前为事件放置其他位置条件。 例如，在购买时打开应用程序内调查 `trackAction` 事件，但 **仅** 用户的当前位置包含特定的Places Service元数据。

![创建条件](/help/assets/places-condition.png)
