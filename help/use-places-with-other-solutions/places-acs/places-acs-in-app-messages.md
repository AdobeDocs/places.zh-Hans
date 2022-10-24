---
title: 使用Places Service的应用程序内消息
description: 本节提供有关如何在Campaign Standard中将推送消息与应用程序内消息结合使用的Campaign Standard信息。
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# 使用Places Service的应用程序内消息传送 {#in-app-messages-loc-service}

此信息可帮助您了解如何使用Places Service信息发送应用程序内消息或本地通知。

## 先决条件

在开始之前，请完成以下任务：

* 已使用Adobe Experience Platform Mobile SDK配置移动应用程序，包括 [Adobe Campaign Standard扩展](Https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* 集成 [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) 到您的应用程序中。
* 添加 [Adobe Campaign Standard扩展](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) 到您的移动设备应用程序配置。

* [创建POI](/help/poi-mgmt-ui/create-a-poi-ui.md) 在Places Service POI管理界面中。

* 安装和配置 [Places扩展](/help/places-ext-aep-sdks/places-extension/places-extension.md) 和区域监控解决方案([CoreLocation文档](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) 对于iOS，或 [Android位置文档](https://developer.android.com/training/location/geofencing))。

## 基于地域围栏登入或退出发送应用程序内消息

1. 在您的Adobe Campaign Standard实例中，单击 **[!UICONTROL 创建应用程序内消息]**.
1. 对于消息类型，选择 **[!UICONTROL 定位移动应用程序的所有用户]**.
1. 单击 **[!UICONTROL 下一个]** 并键入常规详细信息。
1. 在左窗格中，确认可以使用与Places Services相关的各种触发器。

   * 如果用户输入了POI地理围栏，则可以选择显示应用程序内消息。
   * 您还可以使用Places Services UI中定义的元数据来筛选受众。

   在以下示例中，您可以触发一个应用程序内消息，该消息仅向进入其中一个度假胜地（该度假胜地）的用户显示，这些用户将参加免费饮料计划，并且您希望在到达时向这些用户发送优惠券。

   ![“应用程序内消息放置元数据”](/help/assets/last-entered-vacation.png)

1. 单击 **[!UICONTROL 下一个]** 以完成创建要交付的应用程序内消息。

   ![&quot;创建事件&quot;](/help/assets/prepare-ACS.png)

   要测试应用程序内消息投放，请在Xcode或Android Studio中启动应用程序，然后使用位置模拟器选择符合消息传送标准的POI。

   ![&quot;饮用优惠券&quot;](/help/assets/drink-coupon-on-app.png)

将Places Services与Adobe Campaign Standard结合使用，为您提供了一个功能强大的工具，可根据地域划分条目和退出情况将消息发送给用户。 利用此集成，可构建更加个性化和符合情境的用例。

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Adobe Experience Platform Location Service with Campaign Messaging](https://www.youtube.com/watch?v=ikiTTQw9c-o)
