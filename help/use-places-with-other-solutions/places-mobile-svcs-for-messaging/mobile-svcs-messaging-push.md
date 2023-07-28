---
title: 推送通知
description: 此部分将向您展示如何将Places服务与推送通知结合使用。
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 8%

---

# 推送通知

Mobile Services允许您将推送通知发送至Adobe Analytics区段。 在Places Service中，您可以通过使用推送消息与POI的历史交互来细分受众。 例如，您可以向过去30天内访问过您某个商店的用户发送消息。

在开始之前，请确保您已完成以下任务：

* Places服务数据已由Adobe Analytics处理。

  这意味着您的移动设备应用程序已成功将Places服务数据发送到报表包，并且这些数据可用于分段。

* 设置Mobile Services中的推送通知渠道。

  有关更多信息，请参阅[创建推送消息](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html)。

* 了解如何在Mobile Services中向Analytics区段发送推送通知。

  有关更多信息，请参阅[创建推送消息](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html)。

## 发送通知

在 **[!UICONTROL 受众]** 选项卡 *创建推送通知* 工作流，您可以通过以下方式之一为此消息创建受众：

* 在 **[!UICONTROL Analytics区段]** 从下拉列表中，选择之前创建的Adobe Analytics区段。

* 在 **[!UICONTROL 自定义区段]** 部分，使用可用的自定义区段参数构建受众。

![设置推送消息](/help/assets/push-set-up.png)
