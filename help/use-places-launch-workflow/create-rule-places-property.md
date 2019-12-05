---
title: 为您的地点属性创建规则
description: 'Places SDK会跟踪当前位置，监视围绕当前位置配置的POI，并跟踪这些POI的进入和退出事件。 '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# 创建进入和退出规则 {#create-entry-exit-rules}

在移动应用程序中安装地点和地点监视器扩展后，您可以在Adobe Experience Platform Launch中创建规则，这些规则是触发或条件化的位置数据，包括位置进入和退出事件。

## 规则

您可以配置由事件、条件和操作组成的规则。 每个规则由以下内容组成：

* 一个或多个活动
* （可选）条件
* 一个或多个操作

### 地点活动

Places提供了以下事件，您可以在其中运行规则：

* **输入POI**，该POI由客户进入您配置的POI时的Places SDK触发。
* **退出POI**，客户退出您配置的POI时，由Places SDK触发。

### 地点条件

条件定义了与事件关联的数据或该实例中某个扩展的共享状态必须满足的条件，才能执行操作。 例如，您可以设置条件，以触发仅在旧金山市进入咖啡店的操作。

Places SDK保持以下状态：

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
>此示例假设您已经创建了包含美国所有咖啡馆的 POI 库。For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

以下过程是如何创建规则的示例，当您进入旧金山的咖啡店时，该规则会将帖子发送回Slack。

事件、条件和操作通过以下方式进行定义：

* **事件**:放置条目事件。
* **条件**：**当前 POI** 的城市是旧金山
* **操作**:将回发发给Slack，注明客户输入的咖啡店名称。

### 先决条件

在创建规则之前，您必须在Adobe Experience Platform Launch中创建数据元素。 数据元素会自动在回发消息中填充有关您的POI的必要信息。

要在Experience Platform Launch中创建数据元素，请执行以下操作：

1. 单击“数 **据元素** ”选项卡。
1. Click **Add Data Element**.
1. 键入名称，例如“当 **前咖啡店名称”**。
1. 在“扩 **展** ”下拉列表中，选择“ **地点——测试版”**。
1. 在&#x200B;**数据元素**&#x200B;中，选择&#x200B;**城市**。
1. 在右窗格中，选择“当 **前POI”**。
1. 单击&#x200B;**保存**。

### 在Experience Platform Launch for Places中创建规则

![创建规则](/help/assets/placesrule.png)

1. In Experience Platform Launch, click the **[!UICONTROL Rules]** tab.
1. 单击 **[!UICONTROL Add Rule]**。
1. 键入规则的名称，例如 **[!UICONTROL Track entry for coffee shop in SF]**。

### 创建活动

1. 在“活动”部分，单击 **[!UICONTROL + Add]**。 事件决定您希望规则触发的时间。
1. 在下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places – Beta]**。
1. 在下 **[!UICONTROL Event Type]** 拉列表中，选择 **[!UICONTROL Enter POI]**。
1. 在 **[!UICONTROL Name]**&#x200B;中，输入事件的名称，例如 **[!UICONTROL Entering a coffee shop]**。
1. 单击 **[!UICONTROL Keep Changes]**。

### 创建条件

1. 在“条件”部分，单击 **[!UICONTROL +Add]**。 条件决定了必须满足哪些条件才能采取相应的行动。
1. In **[!UICONTROL Logic Type]**, select Regular, which allows actions to execute if the condition is met.
1. 在下 **[!UICONTROL Extension]** 拉列表中，选择 **[!UICONTROL Places – Beta]**。
1. 在中 **[!UICONTROL Condition Type]**，选择 **[!UICONTROL City]**。
1. Type a condition name, for example, **[!UICONTROL Coffee shop in SF]**.
1. In the right pane, click **[!UICONTROL Current POI]**, and in the drop-down list, select **[!UICONTROL San Francisco]** as one of your cities.
1. 单击 **[!UICONTROL Keep Changes]**。

### 创建操作

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL + Add]**.
1. 在下拉 **[!UICONTROL Extension]** 列表中，将默认选项保留为 **[!UICONTROL Mobile Core]** 选中状态。
1. 选择操作类型，例如 **[!UICONTROL Send Postback]**。

   a.在 **[!UICONTROL URL]**&#x200B;中，键入Slack的回发URL，例如 `https://hooks.slack.com/services/`。

   b.要发送帖子正文，请选中 **[!UICONTROL Add Post Body]** 复选框。

   c.在 **[!UICONTROL Post Body]**&#x200B;中，添加帖子正文，例如： `{ "text": "A customer has entered" }`

   c.键入内容类型，例如 **[!UICONTROL application/json]**。

   d.选择超时值，例如 **[!UICONTROL 5]**。

1. 单击 **[!UICONTROL Keep Changes]**。

### 发布规则

1. 要激活规则，您必须发布该规则。 有关在Experience Platform Launch中发布规则的详细信息，请参阅发 [布](https://docs.adobelaunch.com/launch-reference/publishing)。

### 超越进出境的思考

在Experience Platform Launch中使用位置服务地理围栏条目和退出来触发规则的功能极其强大，但您也可以将位置数据用作其他事件触发的条件。 例如，您可能拥有一个Mobile Core Track Action事件触发器，该触发器根据应用程序内的特定trackAction调用事件准备触发。 根据此事件，您可以在执行操作之前为事件添加其他位置条件。 例如，在发生购买事件时打开应用程序内调查，但 `trackAction` 仅在用户的当前位 **置包含特定** “位置服务”元数据时打开。

![创建条件](/help/assets/places-condition.png)