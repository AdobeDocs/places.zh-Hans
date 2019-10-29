---
title: 推送消息
seo-title: 推送消息
description: 本节将向您介绍如何将Places与推送消息结合使用。
seo-description: 本节将向您介绍如何将Places与推送消息结合使用。
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# 推送通知(#places-push-messaging)

推送通知：AMS允许您向Adobe Analytics区段发送推送通知。 通过位置服务，您可以按推送消息与POI的历史交互将受众细分。 例如，您可以向过去30天内在某家商店中的用户发送消息。

在开始之前，请确保您已完成以下任务：

* 位置服务数据已由Adobe Analytics处理。

   这意味着您的移动应用程序已成功地将位置服务数据发送到报表包中，且该数据可用于分段。

* Mobile services中的推送通知渠道已设置。

   有关更多信息，请参阅[创建推送消息](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html)。

* 熟悉如何向Mobile services中的Analytics区段发送推送通知。

   * 有关更多信息，请参阅[创建推送消息](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html)。

## 发送通知

在创 **[!UICONTROL Audience]** 建推送通知 *工作流的选项卡中* ，可以通过以下方式之一为此消息创建受众：

* 选择之前创建的Adobe Analytics区段。

* 使用可用的自定义区段参数构建受众。

![设置推送消息](/help/assets/push-set-up.png)

