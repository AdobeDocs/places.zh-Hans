---
title: 推送通知
description: 本节将向您介绍如何将地点与推送通知一起使用。
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# 推送通知

Mobile services允许您向Adobe Analytics区段发送推送通知。 在位置服务中，您可以使用受众与POI的历史交互来为您的推送消息细分受众。 例如，您可以向过去30天内在某家商店中的用户发送消息。

在开始之前，请确保您已完成以下任务：

* 位置服务数据已由Adobe Analytics处理。

   这意味着您的移动应用程序已成功将位置服务数据发送到报表包，并且该数据可用于分段。

* Mobile services中的推送通知渠道已设置。

   有关更多信息，请参阅[创建推送消息](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)。

* 了解如何向Mobile services中的Analytics区段发送推送通知。

   有关更多信息，请参阅[创建推送消息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)。

## 发送通知

在创 **[!UICONTROL Audience]** 建推送通 *知工作流的选项卡上* ，可以通过以下方式之一为此消息创建受众：

* 在下拉 **[!UICONTROL Analytics Segments]** 列表中，选择之前创建的Adobe Analytics区段。

* 在该部 **[!UICONTROL Custom Segment]** 分中，使用可用的自定义区段参数构建受众。

![设置推送消息](/help/assets/push-set-up.png)
