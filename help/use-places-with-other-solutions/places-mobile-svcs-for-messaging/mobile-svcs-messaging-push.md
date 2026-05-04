---
title: 推送通知
description: 此部分将向您展示如何将Places服务与推送通知结合使用。
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
TQID: https://experienceleague.adobe.com/aaTMSoOkVUfbPDpPiRm7P3-8d8JSO9N0Ga12Hlmf-go
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 14%

---

# 推送通知

Mobile Services允许您将推送通知发送至Adobe Analytics区段。 在Places Service中，您可以通过使用推送消息与POI的历史交互来细分受众。 例如，您可以向过去30天内访问过您某个商店的用户发送消息。

在开始之前，请确保您已完成以下任务：

* Places服务数据已由Adobe Analytics处理。

  这意味着您的移动设备应用程序已成功将Places服务数据发送到报表包，并且这些数据可用于分段。

* 设置Mobile Services中的推送通知渠道。

  有关更多信息，请参阅[创建推送消息](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=zh-Hans)。

* 了解如何在Mobile Services中向Analytics区段发送推送通知。

  有关更多信息，请参阅[创建推送消息](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.html?lang=zh-Hans)。

## 发送通知

在&#x200B;*创建推送通知*&#x200B;工作流的&#x200B;**[!UICONTROL 受众]**&#x200B;选项卡上，您可以通过以下方式之一为此消息创建受众：

* 在&#x200B;**[!UICONTROL Analytics区段]**&#x200B;下拉列表中选择之前创建的Adobe Analytics区段。

* 在&#x200B;**[!UICONTROL 自定义区段]**&#x200B;部分中，使用可用的自定义区段参数构建受众。

![设置推送消息](/help/assets/push-set-up.png)
