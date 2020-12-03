---
title: 推送通知
description: 本节将向您介绍如何将Places Service与推送通知一起使用。
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 8%

---


# 推送通知

Mobile Services允许您向Adobe Analytics区段发送推送通知。 在Places Service中，您可以使用推送消息与POI的历史交互来细分受众。 例如，您可以向过去30天内在您的某家商店中访问过的用户发送消息。

在开始之前，请确保您已完成以下任务:

* 地点服务数据已由Adobe Analytics处理。

   这意味着您的移动应用程序已成功将Places Service数据发送到报表包，并且该数据可用于分段。

* Mobile Services中的推送通知渠道已设置。

   有关更多信息，请参阅[创建推送消息](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)。

* 了解如何向Mobile Services中的Analytics区段发送推送通知。

   有关更多信息，请参阅[创建推送消息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)。

## 发送通知

在“创 **[!UICONTROL Audience]** 建推送通 *知”工作流的选项卡上* ，您可以通过以下方式之一为此消息创建受众:

* 在下 **[!UICONTROL Analytics Segments]** 拉列表中，选择之前创建的Adobe Analytics区段。

* 在部分 **[!UICONTROL Custom Segment]** 中，使用可用的自定义段参数构建受众。

![设置推送消息](/help/assets/push-set-up.png)
