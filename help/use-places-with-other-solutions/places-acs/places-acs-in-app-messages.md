---
title: Places Service的应用程序内消息
description: 本节提供有关如何在Campaign Standard中将推送消息与Campaign Standard中的应用程序内消息结合使用的信息。
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---


# Places Service的应用程序内消息传递 {#in-app-messages-loc-service}

此信息有助于您了解如何使用Places Service信息发送应用程序内消息或本地通知。

## 先决条件

开始之前，请完成以下任务:

* 使用Adobe Experience Platform移动SDK配置移动应用程序，包括 [Adobe Campaign Standard扩展](Https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)。

* 将Adobe Experience Platform [移动SDK集](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 成到您的应用程序中。
* 将Adobe Campaign Standard [扩展添加](Https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 到您的移动应用程序配置。

* [在Places Service](/help/poi-mgmt-ui/create-a-poi-ui.md) POI管理界面中创建POI。

* 在您的移动应用 [程序中安](/help/places-ext-aep-sdks/places-extension/places-extension.md) 装 [和配置Places扩](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) 展和Places Monitor扩展。

## 根据地理围栏进入或退出发送应用程序内消息

1. 在您的Adobe Campaign Standard实例中，单击 **[!UICONTROL Create In-App message]**。
1. 对于消息类型，选择 **[!UICONTROL Target all users of a Mobile application]**。
1. 单击 **[!UICONTROL Next]** 并键入常规详细信息。
1. 在左窗格中，验证是否可以使用与Places Services相关的各种触发器。

   * 如果用户已输入POI地理围栏，则可以选择显示应用程序内消息。
   * 您还可以使用在Places Services UI中定义的元数据来筛选受众。

   在以下示例中，您可以触发仅向进入其中一个度假胜地、参加免费饮品项目的用户显示的应用程序内消息，并且您希望在用户到达时向这些用户发送优惠券。

   ![“应用程序内消息放置元数据”](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]** to finish creating the In-app message for delivery.

   ![“创建事件”](/help/assets/prepare-ACS.png)

   要测试应用程序内消息投放，请在Xcode或Android studio中启动应用程序，并使用位置模拟器选择符合消息传递条件的POI。

   ![“饮料优惠券”](/help/assets/drink-coupon-on-app.png)

将Places Services与Adobe Campaign Standard结合使用，为您提供了一个强大的工具，根据地理围栏条目和退出将消息细分并目标给用户。 此集成允许您构建更个性化的情境式使用案例。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform位置服务(带活动消息)](https://www.youtube.com/watch?v=ikiTTQw9c-o)
