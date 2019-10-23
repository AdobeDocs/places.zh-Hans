---
title: 为您的地点属性创建规则
seo-title: 为您的地点属性创建规则
description: 'Places SDK会跟踪当前位置，监视围绕当前位置配置的POI，并跟踪这些POI的进入和退出事件。 '
seo-description: 'Places SDK会跟踪当前位置，监视围绕当前位置配置的POI，并跟踪这些POI的进入和退出事件。 '
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# 为“地点”属性创建规则 {#creating-rule-places-property}

位置服务SDK会跟踪当前位置，监视当前位置周围配置的POI，并跟踪这些POI的进入和退出事件。

## 规则

您可以配置由事件、条件和操作组成的规则。 每个规则由以下内容组成：

* 一个或多个活动
* （可选）条件
* 一个或多个操作

### Event

Places提供了以下事件，您可以在其中运行规则：

* **[!UICONTROL Enter POI]**，由Places SDK在您的客户进入您配置的POI时触发。
* **[!UICONTROL Exit POI]**，由客户退出您配置的POI时的Places SDK触发。

### 条件

条件定义了与事件关联的数据或该实例中某个扩展的共享状态必须满足的条件，才能执行操作。 例如，您可以设置条件，以触发仅在旧金山市进入咖啡店的操作。

位置服务SDK保持以下状态：

* 当前POI，指客户当前所在的POI。
* 上次退出POI，即客户退出的最近POI。
* 上次输入的POI，指您的客户输入的最新POI。

每个POI都包含以下数据元素：

* ID
* 名称:
* 纬度／经度
* 半径
* 元数据，如城市、国家／地区、州／省、类别

### 操作

操作定义应用程序将执行什么操作以响应已触发事件满足规则的条件。 例如，当客户进入POI时，您可以配置欢迎消息以在其移动设备上显示。

## 创建规则：示例

>[!CAUTION]
>
>此示例假定您已创建了美国所有咖啡店的POI库。 有关创建POI和库的详细信息，请参 [阅创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md) ，并参阅 *在Places UI中的* Manage libraries [中创建库](/help/poi-mgmt-ui/manage-libraries-in-the-places-ui.md)。

以下过程是如何创建规则的示例，当您进入旧金山的咖啡店时，该规则会将帖子发送回Slack。

事件、条件和操作通过以下方式进行定义：

* **事件**:位置服务条目事件。
* **条件**:City for the **Current POI** is San Francisco
* **操作**:向Slack发送回邮件，注明客户输入的咖啡店名称。

### 先决条件

在创建规则之前，您必须在Experience Platform Launch中创建数据元素。 数据元素会自动在回发消息中填充有关您的POI的必要信息。

要在Experience Platform Launch中创建数据元素，请执行以下操作：

1. Click the **[!UICONTROL Data Elements]** tab.
2. 单击 **[!UICONTROL Add Data Element]**。
3. Type a name, for example, **[!UICONTROL Current coffee shop name]**.
4. 在下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places – Beta]**。
5. 在中 **[!UICONTROL Data Element]**，选择 **[!UICONTROL City]**。
6. 在右侧窗格中，选择“ **当前POI”**。
7. 单击 **[!UICONTROL Save]**。

### 在Experience Platform Launch for Location service中创建规则

![](//help/assets/create-a-rule.png)

1. 在Experience Platform Launch中，单击选项 **[!UICONTROL Rules]** 卡。
2. Click **Add Rule**.
3. 键入规则的名称，例如SF **中咖啡店的Track项**。

### 创建活动

1. 在“活动”部分，单击 **[!UICONTROL + Add]**。 事件决定您希望规则触发的时间。
2. 在下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places – Beta]**。
3. 在下 **[!UICONTROL Event Type]** 拉列表中，选择 **[!UICONTROL Enter POI]**。
4. 在 **[!UICONTROL Name]**&#x200B;中，输入事件的名称，例如 **[!UICONTROL Entering a coffee shop]**。
5. 单击 **[!UICONTROL Keep Changes]**。

### 创建条件

1. 在“条件”部分，单击 **[!UICONTROL +Add]**。 条件决定了必须满足哪些条件才能采取相应的行动。
2. 在中， **[!UICONTROL Logic Type]**&#x200B;选择常规，允许在满足条件时执行操作。
3. 在“扩 **展** ”下拉列表中，选择 **[!UICONTROL Places – Beta]**。
4. 在中 **[!UICONTROL Condition Type]**，选择 **[!UICONTROL City]**。
5. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
6. 在右窗格中，单 **[!UICONTROL Current POI]**&#x200B;击，然后在下拉列表中，选择您 **[!UICONTROL San Francisco]** 的某个城市。
7. 单击 **[!UICONTROL Keep Changes]**。

### 创建操作

1. 在部分 **[!UICONTROL Actions]** 中，单击 **[!UICONTRO+添加]**。
2. 在“扩 **[!UICONTRO 展]** ”下拉列表中 **[!UICONTRO ，将默认的“移动核心]** ”选项保留为选中状态。
3. 选择操作类型，例如，“发送回 **[!UICONTRO 发”]**。

   a.在 **[!UICONTROL URL]**&#x200B;中，键入Slack的回发URL，例如 `https://hooks.slack.com/services/`。

   b.要发送帖子正文，请选中“添 **[!UICONTRO 加帖子正文]** ”复选框。

   c.在 **[!UICONTRO 帖子正文中]**，添加帖子正文，例如： `{ "text": "A customer has entered" }`

   c.键入内容类型，例如 **[!UICONTRO application/json]**。

   d.选择超时值，例如， **5**。

4. Click **[!UICONTRO Keep Changes]**.

### 发布规则

1. 要激活规则，您必须发布该规则。 有关在Experience Platform Launch中发布规则的详细信息，请参阅发 [布](https://docs.adobelaunch.com/launch-reference/publishing)。